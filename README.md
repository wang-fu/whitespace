# whitespace
whitespace
```
var source = 'hello,this is w whitespace'
function whitespaceEncode(str) {
    var j, result = '';

    for (var i = 0; i < str.length; i++) {
        var charCode = str.charCodeAt(i);
        var binStr = charCode.toString(2);

        var padLen = 7 - (binStr.length % 7);
        for (j = 0; j < padLen && padLen <7; j++) {
            binStr = '0' + binStr;
        }

        for (j = 0; j < binStr.length; j++) {
            result += (binStr[j] === '0') ?
                ' ' :  // space
                '	'; // tab
        }
    }

    return result;
}

function whitespaceDecode(str) {
    var result = '';
    str.replace(/.{7}/g, function (strByte) {
        var binStr = strByte.replace(/ /g, '0').replace(/	/g, '1');
        var charCode = parseInt(binStr, 2);
        result += String.fromCharCode(charCode);
    });

    return result;
}

var encodedSource = whitespaceEncode(source);
var decodedSource = whitespaceDecode(encodedSource);

alert('SOURCE:', source);
alert('ENCODED:', encodedSource);
alert('DECODED:', decodedSource);
```
