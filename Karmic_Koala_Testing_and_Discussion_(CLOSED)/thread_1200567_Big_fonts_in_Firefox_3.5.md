---
title: "Big fonts in Firefox 3.5"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-06-30
Hi,

I'm getting a problem in Firefox 3.5, where most of the fonts are big and fuzzy, including those on the menubar and other parts of the interface. Are you guys familiar with this, or know how to solve it?

Thanks!

---

### Post by psyke83 on 2009-06-30
> **Bou said:**
> Hi,

I'm getting a problem in Firefox 3.5, where most of the fonts are big and fuzzy, including those on the menubar and other parts of the interface. Are you guys familiar with this, or know how to solve it?

Thanks!

Can you show a screenshot? Fonts are displaying fine for me here (using 3.5~rc2+nobinonly-0ubuntu1), except in some cases where the subpixel hinting seems to be the "legacy" kind instead of the "ClearType" kind that's now default. 

An example of the legacy font rendering is present in the textbox as I write this reply right this moment; all other parts of the site (and Firefox's interface) uses the newer system-wide hinting.

---

### Post by Roman0 on 2009-06-30
Hi, I think I have the same problem. Bou, does it look like in these screenshots?

[http://img40.imageshack.us/img40/7571/zrzutekranufqx.png]("http://img40.imageshack.us/img40/7571/zrzutekranufqx.png") - Firefox 3.1 installed in Ubuntu 9.04 by default (that's the way it should look like)
[http://img530.imageshack.us/img530/6126/zrzutekranu1n.png]("http://img530.imageshack.us/img530/6126/zrzutekranu1n.png") - Firefox 3.5 from mozilla's ftp server (that's the way it looks like, blurred, almost bold fonts)

Additionally, the same way they look in Opera Browser installed from an archive. Seems you're right, they both are not using some system-wide font settings.

---

### Post by Bou on 2009-06-30
> **Roman0 said:**
> Hi, I think I have the same problem. Bou, does it look like in these screenshots?

Right, that's the problem. Anyway, turns out the solution had already been posted. Please take a look at [http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387)

Hope it helps you (it worked for me).

---

