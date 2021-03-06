# tokenizer #
A simple tokenizer written in javascript for Node.JS

### Example ###
```javascript
var fs = require('fs');
var tokenizer = require('./tokenizer');

tokenizer.debug = true;
tokenizer.rule('newline', /^\n/);
tokenizer.rule('whitespace', /^\s+/);
tokenizer.rule('function', /^fn [^\s]+/);
tokenizer.rule('string', /^\'.+\'/);
tokenizer.rule('word', /^[^\s]+/);
var tokens = tokenizer.tokenize(fs.readFileSync('./nick.n', 'utf8'));

console.log('Parsed ' + tokens.length + ' tokens');
```

where the source file is:
```
fn hello_world
  puts 'hello world'
```


will output:

```
-- Starting tokenizer --
fn hello_world
  puts 'hello world'

--                    --
function token: fn hello_world
newline token: 

whitespace token:   
word token: puts
whitespace token:  
string token: 'hello world'
newline token: 

-- Tokenizing complete --
[ 'fn hello_world',
  '\n',
  '  ',
  'puts',
  ' ',
  '\'hello world\'',
  '\n' ]
--                     --
Parsed 7 tokens
```
