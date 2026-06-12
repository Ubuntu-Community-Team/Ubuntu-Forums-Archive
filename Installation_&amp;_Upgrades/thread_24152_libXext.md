---
title: "libXext"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by bibaleebu on 2005-04-05
Hello, yesterday i installed v 5.04 on my pc.  I found this program called Quanta, and have been trying to install it for countless hours......

At first, i didnt have a c compiler, so i looked around on this site and found how to install it, but now im getting the error, after using the configure command.....

checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.
  what should i do?, i am a noob so use short words and speak slowlY ](*,)

---

### Post by alastair on 2005-04-05
I have :

/usr/X11R6/lib/libXext.so.6.4
/usr/X11R6/lib/libXext.so.6
/usr/X11R6/lib/libXext.a
/usr/X11R6/lib/libXext.so

I have packages :

libxext-dev
libxext6

Hope that helps.

---

### Post by bibaleebu on 2005-04-05
i have that stuff too, but it still says the same thing :?

---

### Post by alastair on 2005-04-05
OK - well, that should be enough (header and libs) so ....

Why not just install the quanta package?

sudo apt-get install quanta quanta-data

---

### Post by bibaleebu on 2005-04-05
[QUOTE=alastair]OK - well, that should be enough (header and libs) so ....

Why not just install the quanta package?

sudo apt-get install quanta quanta-data[/QUOTE]
 see, i need to learn how to do that.....type one little sentance and have my pc do it for me......thanks

---

### Post by jeremy on 2005-04-06
Quanta is now called kdewebdev, look for that in synaptic.

---

