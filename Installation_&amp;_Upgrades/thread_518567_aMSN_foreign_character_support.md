---
title: "aMSN foreign character support?"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by ownaginatious on 2007-08-06
I recently installed aMSN to replace msn messenger in my quest to transition to ubuntu from windows, and I'm having problems getting it to display the foreign characters people have in their MSN names. The problem is that a lot of my friends are from outside Canada, and like to write stuff in their MSN nicknames in Tamil or other Indian scripts. aMSN doesn't show the characters, and instead leaves a bunch of spaces equivalent to the length of the text that is supposed to be there. This kind of causes a problem because I can't tell who is who, and it doesn't visually look very nice. I tried playing around with the encoding and tried a few different fonts, but nothing seems to really work :(.

Does anyone know how to fix this problem? Any help would be greatly appreciated :)

---

### Post by ownaginatious on 2007-08-06
bump

---

### Post by ownaginatious on 2007-08-06
anyone? :(

---

### Post by ZipoTe on 2007-08-06
What you need is antialiasing!! :P with that amsn looking will improve. But having this feature means you will have to compile amsn by yourself :D

Easy job :P, first remove amsn via apt-get or synaptic, then follow this:

[http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn+antialiasing]("http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn+antialiasing")
look for the #7 post (patrickfromspain's one) and follow his instructions, it works like a charm.

If you don't understand something post here your questions.

---

### Post by ownaginatious on 2007-08-06
> **ZipoTe said:**
> What you need is antialiasing!! :P with that amsn looking will improve. But having this feature means you will have to compile amsn by yourself :D

Easy job :P, first remove amsn via apt-get or synaptic, then follow this:

[http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn+antialiasing]("http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn+antialiasing")
look for the #7 post (patrickfromspain's one) and follow his instructions, it works like a charm.

If you don't understand something post here your questions.

Umm... that's not at all what I wanted. I don't want semi-transparency of the program, I want foreign ttext support :p

---

### Post by vambo on 2007-08-06
First, I don't know anything about aMSN. However, just to cover the obvious. Have you enabled the appropriate language support for the ones you're trying to read?

System -> Admin -> Language Support

Might be worth a go if you haven't

Cheers

---

### Post by ZipoTe on 2007-08-07
With antialiasing you don't get transparencies, it improves the looking and, in my case, antialiasing let me see some characters that before i couldn't. So give it a try!:)

---

### Post by ownaginatious on 2007-08-07
I would try it, but I'm kinda a noob to linux, and the installation just looks way to difficult, and I had problems when I did it. I hate this thing about linux where you have to compile everything yourself...

---

### Post by ownaginatious on 2007-08-07
Ok, I have everything the way I want it now :) I installed the extra languages as someone mentioned (thanks by the way :)) and upgraded aMSN... apparently the version I had way really old 0.o

Well, it looks really good now :) Thanks for everyone's help!

---

