---
title: "Bad Compiz! Bad!"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-01-28
[http://img94.imageshack.us/img94/7263/ohgodo.png](http://img94.imageshack.us/img94/7263/ohgodo.png)

Did Compiz get updated within the last day or so?

---

### Post by MadMan2k on 2010-01-28
I would guess its the graphic driver. Besides it is funny - enjoy :D

---

### Post by phillw on 2010-01-28
:lolflag:

Wonderful - that's made my day, thanks for sharing that gem.

(- Hope you got it sorted)

Regards,

Phill.

---

### Post by praveenmarkandu on 2010-01-28
> **Starks said:**
> [http://img94.imageshack.us/img94/7263/ohgodo.png](http://img94.imageshack.us/img94/7263/ohgodo.png)

Did Compiz get updated within the last day or so?

looks like the rotational setting in your graphics driver has been changed. look into that. also seems as if you are missing a windwoss manager

---

### Post by Vanishing on 2010-01-28
> **Starks said:**
> [http://img94.imageshack.us/img94/7263/ohgodo.png](http://img94.imageshack.us/img94/7263/ohgodo.png)

Did Compiz get updated within the last day or so?

this made me lol..
how did you manage to post this thread with that display..:lolflag:
in ccsm, check Text in Image loading..if that's the problem.

---

### Post by phenest on 2010-01-28
> **praveenmarkandu said:**
> looks like the rotational setting in your graphics driver has been changed. look into that. also seems as if you are missing a windwoss manager

Look at it carefully. It's not rotated, it's flipped. Rotate that picture and all the writing is back to front.

---

### Post by Darkshade on 2010-01-28
This is amazing! :D
I've seen something similar before though, I believe it was graphic drivers related.
Extra points if you posted from the PC on the screenshot.

---

### Post by Merk42 on 2010-01-28
Just put your monitor on a really shiny table and look at the reflection.

---

### Post by Vanishing on 2010-01-28
> **Merk42 said:**
> Just put your monitor on a really shiny table and look at the reflection.

that is one great idea..lol..

---

### Post by darco on 2010-01-28
(: ¡&#670;&#596;&#305;&#633;&#647; &#647;&#592;&#477;u &#592; s&#647;&#592;&#613;&#647; '&#653;o&#653;

---

### Post by shafin on 2010-01-29
```
<head>
<title>Flip!</title>
<script language="JavaScript">

function flip() {
	var result = flipString(document.f.original.value);
	document.f.flipped.value = result;
}

function flipString(aString) {
	aString = aString.toLowerCase();
	var last = aString.length - 1;
	var result = "";
	for (var i = last; i >= 0; --i) {
		result += flipChar(aString.charAt(i))
	}
	return result;
}

function flipChar(c) {
	if (c == 'a') {
		return '\u0250'
	}
	else if (c == 'b') {
		return 'q'
	}
	else if (c == 'c') {
		return '\u0254'
	}
	else if (c == 'd') {
		return 'p'
	}
	else if (c == 'e') {
		return '\u01DD'
	}
	else if (c == 'f') {
		return '\u025F'
	}
	else if (c == 'g') {
		return 'b'
	}
	else if (c == 'h') {
		return '\u0265'
	}
	else if (c == 'i') {
		return '\u0131'//'\u0131\u0323'
	}
	else if (c == 'j') {
		return '\u0638'
	}
	else if (c == 'k') {
		return '\u029E'
	}
	else if (c == 'l') {
		return '1'
	}
	else if (c == 'm') {
		return '\u026F'
	}
	else if (c == 'n') {
		return 'u'
	}
	else if (c == 'o') {
		return 'o'
	}
	else if (c == 'p') {
		return 'd'
	}
	else if (c == 'q') {
		return 'b'
	}
	else if (c == 'r') {
		return '\u0279'
	}
	else if (c == 's') {
		return 's'
	}
	else if (c == 't') {
		return '\u0287'
	}
	else if (c == 'u') {
		return 'n'
	}
	else if (c == 'v') {
		return '\u028C'
	}
	else if (c == 'w') {
		return '\u028D'
	}
	else if (c == 'x') {
		return 'x'
	}
	else if (c == 'y') {
		return '\u028E'
	}
	else if (c == 'z') {
		return 'z'
	}
	else if (c == '[') {
		return ']'
	}
	else if (c == ']') {
		return '['
	}
	else if (c == '(') {
		return ')'
	}
	else if (c == ')') {
		return '('
	}
	else if (c == '{') {
		return '}'
	}
	else if (c == '}') {
		return '{'
	}
	else if (c == '?') {
		return '\u00BF'
	}
	else if (c == '\u00BF') {
		return '?'
	}
	else if (c == '!') {
		return '\u00A1'
	}
	else if (c == "\'") {
		return ','
	}
	else if (c == ',') {
		return "\'"
	}
	return c;
}
</script>

</head> 		<body> 		<font face="Porky's">Original:</font> <textarea rows="5" cols="50" name="original"></textarea> 		<input type="button" value="Flip" onclick="flip()"> 		<br><font face="Porky's">Flipped:</font> 		<textarea rows="5" cols="50" name="flipped"></textarea></form> 		</body>
```
[URL="http://theburningbiscuit.com/Flip.html"]
Source[/URL]

---

### Post by olnir on 2010-01-29
Lol.

Confirm that.

I have an Ati HD4850 card and using Xorg-edgers ppa for drivers etc.

Works fine without compiz, flipped screen with latest drivers.

So... havent figured out if this is due to xorg-edgers or compiz updates yet.. Any ideas ;)

---

### Post by Starks on 2010-01-29
I'm running edgers, probably the root cause of the bug.

---

