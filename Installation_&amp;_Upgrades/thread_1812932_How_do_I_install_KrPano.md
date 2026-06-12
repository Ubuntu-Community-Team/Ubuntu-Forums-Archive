---
title: "How do I install KrPano?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2011-07-27
I downloaded KrPano from their site [here]("http://krpano.com/download/") and I'm trying to install it. There's no documentation, all I get is a file called krpanotools-1.0.8.12-linux64-2010-11-24.tar.gz. So I extracted it and here is a list of files included in it:

kcube2sphere
kencrypt
kmakemultires
kmakepreview
kmaketiles
kprotectcl
ktransform

That's it. Any idea what I do with this thing? Thanks.

---

### Post by steve11911 on 2011-07-27
Krpano has a support forum (below) and they will accept email questions.

[email]mail@krpano.com[/email]

[http://krpano.com/forum/wbb/index.php?page=Index](http://krpano.com/forum/wbb/index.php?page=Index)

==

This site is probably worth a visit:

[http://www.kolor.com/forum/](http://www.kolor.com/forum/)

---

### Post by Maheriano on 2011-08-04
Turns out you have to download the Windows version, copy all those files into the folder where you downloaded the Linux version and then call it from the command line using their tutorial.

---

### Post by tonderai on 2012-05-18
This KRPano forum thread gives a lot more details on using KRPano in Linux from the command line. The configuration template files are the same as in the Windows build, and you can call them with:

```
/--path-to-the-krpanotools/kmakemultires -config=templates/normal.config ./panoimage.jpg
```

---

