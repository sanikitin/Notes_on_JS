Javascript - это язык программирования с помощью которого можно писать скрипты (прогарммы), которые можно встраивать в HTML код. Для них не нужна компиляция для запуска.

Запуск Javascripta на других устрйоствах реализуется с помощью предустановленного движка или по другому виртуальной машины Javascript. 
Например:
В Chrome и Opera используется движок V8, а в Firefox движок SpiderMonkey.

В разных движках возможны разные функциональности, поэтому нужно понимать, где какой движок используется, чтобы знать запустится или нет определенный функционал.
Посмотреть можно тут:
- http://caniuse.com – таблицы с информацией о поддержке по каждой возможности языка.
- https://kangax.github.io/compat-table – таблица с возможностями языка и движками, которые их поддерживают и не поддерживают.

Принцип работы движка:
1. Движок, например в браузере, читает текст скрипта;
2. Преобразует текст в машинный код;
3. Запускает полученный машинный код.

На каждом этапе происходит оптимизация машинного кода. Благодаря чему можно добиться значительного быстродействия.

Javascript не строго типизированный язык. Для строгой типизации нужен другой язык, который преобразуется автоматически в Javascript. TypeScript концентрируется на добавлении «строгой типизации» для упрощения разработки и поддержки больших и сложных систем. Разработан Microsoft.

Если, что то непонятное, то самая полная информация по Javascript находится в спецификации: https://www.ecma-international.org/publications/standards/Ecma-262.htm

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Основная работа в бораузере - это исправление багов. Поэтому, важно понимать, как работать с консолью разработчика в браузере.
Обычно она открывается клавишей F12.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Основы

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Подключение скрипта

Программы на JavaScript могут быть вставлены в любое место HTML-документа с помощью тега ```<script>```. Например:
```javascript
<!DOCTYPE HTML>
<html>
<body>
  <p>Перед скриптом...</p>
  <script>
    alert( 'Привет, мир!' );
  </script>
  <p>...После скрипта.</p>
</body>
</html>
```
Тег ```<script>``` имеет несколько атрибутов, которые редко используются, но всё ещё могут встретиться в старом коде:
- Атрибут type: ```<script type=…>```
Старый стандарт HTML, HTML4, требовал наличия этого атрибута в теге ```<script>```. Обычно он имел значение ```type="text/javascript"```. На текущий момент этого больше не требуется. 
- Атрибут language: ```<script language=…>```
Этот атрибут должен был задавать язык, на котором написан скрипт. Но так как JavaScript является языком по умолчанию, в этом атрибуте уже нет необходимости.

В основном сейчас файл скрипта подключают к HTML с помощью атрибута src. Синтаксис: ```<script src="/path/to/script.js"></script>```
В пути можно указать:
- абсолютный путь до скрипта от корня сайта (```src="/path/to/script.js"```);
- относительный путь от текущей страницы (```src="script.js"```);
- URL-адрес (```https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js```).
Если скриптов несколько, то просто используется несколько тегов.

ВАЖНО!: Если атрибут ```src``` установлен, содержимое тега ```<script>``` будет игнорироваться.

Польза от отдельных файлов ещё и в том, что браузер загрузит скрипт отдельно и сможет хранить его в кеше. Другие страницы, которые подключают тот же скрипт, смогут брать его из кеша вместо повторной загрузки из сети. И таким образом файл будет загружаться с сервера только один раз. Это сокращает расход трафика и ускоряет загрузку страниц.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Структура кода

Инструкции – это синтаксические конструкции и команды, которые выполняют действия.
Пример: ```alert('Привет, мир!');```
Желательно писать команду с новой строки, чтобы было проще читать.

Точку с запятой в конце можно ставить, а можно не ставить. Пример:
```javascript
alert('Привет')
alert('Мир')
```
Это выполнится, как две команды.
НО! во избежании ошибок, которые потом не найдешь лучше всегда использовать точку с запятой.

Есть возможность комментировать код. Комментариев два вида: 
- Однострочный;
```javascript
alert('Мир'); // Этот комментарий следует за инструкцией
```
- Многострочный;
```javascript
/* 
Это - многострочный комментарий.
*/
alert('Привет');
```
Вложение комментариев друг в друга не поддерживается.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Чтобы отключить поддержку обратной совместимости в коде и работать с скриптом в современном режиме используется команда ```"use strict"``` или ```'use strict'```.

ВАЖНО!: ```"use strict"``` должен находится в первой исполняемой строке скрипта, иначе строгий режим может не включиться. И отменить этот режим невозможно. Его можно только включить, но не выключить.

```'use strict'``` по умолчанию в консоли браузера выключен. Иногда, когда ```'use strict'``` имеет значение можно получить неправильные результаты.

Современный JavaScript поддерживает «классы» и «модули», которые автоматически включают строгий режим. Поэтому в них нет нужды добавлять директиву "use strict".

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

В Javascript есть переменные, как и в остальных языках программирования.
Объявляется с помощью команды let. 
Примеры:
```javascript
let message;

message = 'Hello'; // сохранить строку
alert(message); // показывает содержимое переменной
```
Или
```javascript
let message = 'Hello!'; // определяем переменную и присваиваем ей значение
```
Можно объявлять несколько переменных в одной строке. Но это уменьшает читаемость кода.
```javascript
let user = 'John', age = 25, message = 'Hello';
```
Ранее, использовалось также ```var```, но сейчас оно устарело. Оно имеет отличия в поведении и сейчас не используется.

ВАЖНО!: Повторное объявление вызывает ошибку "SyntaxError: 'message' has already been declared". Переменная может быть объявлена только один раз. Поэтому следует объявлять переменную только один раз и затем использовать её уже без ```let```.

В JavaScript есть два ограничения, касающиеся имён переменных:
- Имя переменной должно содержать только буквы, цифры или символы $ и _.
- Первый символ не должен быть цифрой.

Если имя содержит несколько слов, обычно используется верблюжья нотация, это хорошая практика: myVeryLongName.

ВАЖНО!: Регистр имеет значение. Переменные с именами apple и AppLE – это две разные переменные.

Также, как и в остальных языках нельзя использовать зарезервированные имена: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Lexical_grammar#%D0%9A%D0%BB%D1%8E%D1%87%D0%B5%D0%B2%D1%8B%D0%B5_%D1%81%D0%BB%D0%BE%D0%B2%D0%B0

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Чтобы объявить константу (неизменяемую переменную) используется ```const```.
```javascript
const myBirthday = '21.11.1991';
```

Особенность: Широко распространена практика использования констант в качестве псевдонимов, которые известны до начала исполнения скрипта. Названия таких констант пишутся с использованием заглавных букв и подчёркивания.
```javascript
const COLOR_RED = "#F00";
```
Другими словами, константы с именами, записанными заглавными буквами, используются только как псевдонимы для «жёстко закодированных» значений.


Название переменной должно иметь ясный и понятный смысл, говорить о том, какие данные в ней хранятся. Именование переменных – это один из самых важных и сложных навыков в программировании.
Несколько хороших правил:
- Используйте легко читаемые имена, такие как ```userName``` или ```shoppingCart```.
- Избегайте использования аббревиатур или коротких имён, таких как a, b, c, за исключением тех случаев, когда вы точно знаете, что так нужно.
- Делайте имена максимально описательными и лаконичными. Примеры плохих имён: ```data``` и ```value```. Такие имена ничего не говорят. Их можно использовать только в том случае, если из контекста кода очевидно, какие данные хранит переменная.
- Договоритесь с вашей командой об используемых терминах. Если посетитель сайта называется ```«user»```, тогда мы должны называть связанные с ним переменные ```currentUser``` или ```newUser```, а не, к примеру, ```currentVisitor``` или ```newManInTown```.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Типы данных

Есть восемь основных типов данных в JavaScript. Переменная в JavaScript может содержать любые данные. В один момент там может быть строка, а в другой – число:
```javascript
let message = "hello";
message = 123456;
```
Языки программирования, в которых такое возможно, называются «динамически типизированными». Это значит, что типы данных есть, но переменные не привязаны ни к одному из них.

1. Числовой тип данных (number) представляет как целочисленные значения, так и числа с плавающей точкой. С ними можно выполнять все стандартные арифметически операции.
Кроме обычных чисел, существуют так называемые «специальные числовые значения», которые относятся к этому типу данных: ```Infinity```, ```-Infinity``` и ```NaN```.
а) ```Infinity``` представляет собой математическую бесконечность ∞. Это особое значение, которое больше любого числа. Мы можем получить его в результате деления на ноль:
```javascript
alert( 1 / 0 ); // Infinity
```
Или задать его явно:
```javascript
alert( Infinity ); // Infinity
```
б) ```NaN``` означает вычислительную ошибку. Это результат неправильной или неопределённой математической операции, например:
```javascript
alert( "не число" / 2 ); // NaN
```
Такое деление является ошибкой.
Значение ```NaN``` «прилипчиво». Любая операция с ```NaN``` возвращает ```NaN```:
```javascript
alert( "не число" / 2 + 5 ); // NaN
```

Особенности: 
1. Математические операции в JavaScript «безопасны». Можно делать что угодно. Скрипт никогда не остановится с фатальной ошибкой. В худшем случае мы получим ```NaN``` как результат выполнения.
2. В JavaScript тип «number» не может содержать числа больше, чем (2 в 53 степени -1) (т. е. 9007199254740991), или меньше, чем -(2 в 53 степени -1) для отрицательных чисел. Это техническое ограничение вызвано их внутренним представлением.


2. Тип ```BigInt``` был добавлен в JavaScript, чтобы дать возможность работать с целыми числами произвольной длины. Чтобы создать значение типа ```BigInt```, необходимо добавить n в конец числового литерала:
```javascript
// символ "n" в конце означает, что это BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```
Особенность: ```BigInt``` имеет проблемы с поддержкой, поэтому нужно проверять поддерживает ли его браузер.

3. Строка (```string```) в JavaScript должна быть заключена в кавычки. В JavaScript существует три типа кавычек.
а) Двойные кавычки: ```"Привет"```.
б) Одинарные кавычки: ```'Привет'```.
в) Обратные кавычки: `Привет`.

Двойные или одинарные кавычки являются «простыми», между ними нет разницы в JavaScript. Обратные же кавычки имеют расширенную функциональность. Они позволяют нам встраивать выражения в строку, заключая их в ${…}. Например:
```javascript
let name = "Иван";
// Вставим переменную
alert( `Привет, ${name}!` ); // Привет, Иван!
// Вставим выражение
alert( `результат: ${1 + 2}` ); // результат: 3
```
Особенность: Нет отдельного типа данных для одного символа. В C и Java, для хранения одного символа существует отдельный тип char. В JavaScript есть только тип string. Строка может содержать ноль символов (быть пустой), один символ или множество.

4. Булевый тип (```boolean```) может принимать только два значения: ```true``` (истина) и ```false``` (ложь). Пример: 
```javascript
let nameFieldChecked = true; // да, поле отмечено
let ageFieldChecked = false; // нет, поле не отмечено
```
Булевые значения также могут быть результатом сравнений:
```javascript
let isGreater = 4 > 1;
alert( isGreater ); // true (результатом сравнения будет "да")
```

5. Специальное значение ```null```. В JavaScript ```null``` не является «ссылкой на несуществующий объект» или «нулевым указателем». Это просто специальное значение, которое представляет собой «ничего», «пусто» или «значение неизвестно». Пример:
```javascript
let age = null;
```

6. Специальное значение ```undefined```. Оно означает, что «значение не было присвоено». Если переменная объявлена, но ей не присвоено никакого значения, то её значением будет undefined:
```javascript
let age;
alert(age); // выведет "undefined"
```
Технически мы можем присвоить значение ```undefined```. Но так делать не рекомендуется. Обычно ```null``` используется для присвоения переменной «пустого» или «неизвестного» значения, а ```undefined``` – для проверок, была ли переменная назначена.

7. Тип ```object``` (объект). В объектах же хранят коллекции данных или более сложные структуры.

8. Тип ```symbol``` (символ) используется для создания уникальных идентификаторов в объектах.

Оператор ```typeof``` возвращает тип аргумента. Это полезно, когда мы хотим обрабатывать значения различных типов по-разному или просто хотим сделать проверку. У него есть две синтаксические формы:
- Синтаксис оператора: ```typeof x```.
- Синтаксис функции: ```typeof (x)```.
Результат одинаковый. Вызов ```typeof x``` возвращает строку с именем типа:
```javascript
typeof undefined // "undefined"
typeof 0 // "number"
typeof 10n // "bigint"
typeof true // "boolean"
typeof "foo" // "string"
typeof Symbol("id") // "symbol"
typeof Math // "object"  (1)
typeof null // "object"  (2)
typeof alert // "function"  (3)
```
ВАЖНО!:
- Результатом вызова ```typeof null``` является "object". Это официально признанная ошибка в typeof, ведущая начало с времён создания JavaScript и сохранённая для совместимости.
- Вызов ```typeof alert``` возвращает ```"function"```, потому что ```alert``` является функцией. Функции относятся к объектному типу. Но ```typeof``` обрабатывает их особым образом, возвращая ```"function"```. Так тоже повелось от создания JavaScript. Формально это неверно, но может быть удобным на практике.



