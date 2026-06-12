---
title: "LaTeX broken in lucid lynx?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2010-05-06
Does anyone know what has happened with LaTeX in Lucid Lynx?  I use LaTeX all the time, and just having upgraded my /usr/bin/latex is now a symbolic link to pdftex, and I get the error
[INDENT]This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
---! /home/mylogin/.texmf-var/web2c/pdftex/latex.fmt doesn't match pdftex.pool
(Fatal format file error; I'm stymied)
[/INDENT]

Anyone have any ideas?

Thanks!

---

### Post by lechien73 on 2010-05-06
The problem is that your the latex.fmt file in ~/.texmf-var/web2c/pdftex/ is from your previous version, and so is overriding the global format that would have been created by the new installation.

From your home directory try:

```
mv .texmf-var/ .texmf-backup
```

---

### Post by Demogorge on 2010-05-06
You can also run

```
sudo fmtutil --all
```

To rebuild the ~/.texmf-var directory. This fixed it for me.


In addition you may need to run:

```

sudo updmap-sys
update-updmap
updmap

```

if you have trouble with finding fonts.

---

### Post by eckubu on 2010-05-08
Excellent hint given by *demogorge*/ Within less than one minute LaTeX worked again!
Thanks.

---

### Post by bodhidharma on 2010-05-08
Yes ... thanks for the help!  I was already completely removing and reinstalling everything, *and* I did what you suggested... so I'm not sure which one it was which helped.  Anyway, thanks!

---

### Post by Demogorge on 2010-05-17
Glad I could help!

---

### Post by quackeroni_pizza on 2010-06-11
I'm seeing a slightly different error with Latex after the upgrade...

The style file ifpdf.sty conflicts with \ifpdf variable definitions in texinfo..  This breaks \includegraphics auto-extensions.

Extrememely annoying!!

---

