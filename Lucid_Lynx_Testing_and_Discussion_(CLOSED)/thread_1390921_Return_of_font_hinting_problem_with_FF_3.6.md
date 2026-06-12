---
title: "Return of font hinting problem with FF 3.6"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-01-26
Anyone seeing red tinging to some letters.

---

### Post by phenest on 2010-01-26
Anywhere in particular? A web page?

---

### Post by tad1073 on 2010-01-26
red and green tint here.

---

### Post by philinux on 2010-01-26
> **tad1073 said:**
> red and green tint here.

Medium hinting seems to give a better result than slight.

---

### Post by ranch hand on 2010-01-26
> **tad1073 said:**
> red and green tint here.
I bet you need an update.  sounds like you are using the Christmas Edition.

Sorry, but not very, just couldn't resist.

---

### Post by tad1073 on 2010-01-26
> **ranch hand said:**
> I bet you need an update.  sounds like you are using the Christmas Edition.

Sorry, but not very, just couldn't resist.

:lolflag:
all i know is, the font look horrid

---

### Post by phillw on 2010-01-26
> **ranch hand said:**
> I bet you need an update.  sounds like you are using the Christmas Edition.

:lolflag:

Am on 3.6.1pre - no tints here.

Phill.

---

### Post by philinux on 2010-01-27
Sky news has this effect but not ubuntu forums.

See first paragraph, first sentence. Red and green effect.

---

### Post by phenest on 2010-01-27
Can't see it.

---

### Post by uBeer on 2010-01-27
Please post a png file as jpg's compression method screws up the red/green stuff. Png displays pixel per pixel how it is supposed to be.

I do see it though if I zoom in far enough.

---

### Post by portis on 2010-01-27
ff3.6 is compiled with --disable-system-cairo option.
That's the reason.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615)
[https://bugzilla.mozilla.org/show_bug.cgi?id=541319](https://bugzilla.mozilla.org/show_bug.cgi?id=541319)

---

### Post by philinux on 2010-01-28
> **uBeer said:**
> Please post a png file as jpg's compression method screws up the red/green stuff. Png displays pixel per pixel how it is supposed to be.

I do see it though if I zoom in far enough.

It was a png on my desktop. The forum upload changes it.

---

### Post by philinux on 2010-01-28
> **portis said:**
> ff3.6 is compiled with --disable-system-cairo option.
That's the reason.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615)
[https://bugzilla.mozilla.org/show_bug.cgi?id=541319](https://bugzilla.mozilla.org/show_bug.cgi?id=541319)

Thanks for that I'll wait for the fix.

Why did they do that though?

---

### Post by portis on 2010-01-28
A Ubuntu developer told me that mozilla asked them for years to not use system-cairo, although I don't understand the purpose.

> **philinux said:**
> Thanks for that I'll wait for the fix.

Why did they do that though?

---

