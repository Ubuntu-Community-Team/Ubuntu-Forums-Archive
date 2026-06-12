---
title: "launching .exe files"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by flexalecto on 2010-04-27
I recently installed ubuntu 9.10. I have been trying to launch utilities and other programs that have .exe extensions by double clicking the .exe file. Each time I attempt this I get the following error message in archive manager:

Archive:  /home/tony/Downloads/advisor.exe
[/home/tony/Downloads/advisor.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/tony/Downloads/advisor.exe or
          /home/tony/Downloads/advisor.exe.zip, and cannot find /home/tony/Downloads/advisor.exe.ZIP, period.

 I tried downloading file helper from blitware but I can't launch...
somebody please tell me how to launch .exe files in ubuntu

thanks
flexalecto

---

### Post by crlang13 on 2010-04-27
it depends on the .exe

.exe doesn't work in Ubuntu (it's a windows format).  You can have a go opening them in Wine though -> downloaded through the software center.

---

### Post by tekkidd on 2010-04-27
.exe's are windows executables in order to run them you need wine 

```
sudo apt-get install wine
```

---

### Post by kmsalex on 2010-04-27
when approaching ubuntu for the first time i also tryed to runing a few windows programs but i quickly found alternitves. don't think about how you can get a program to work think about how you can use a program to get a job done.

---

### Post by themusicalduck on 2010-04-27
I would try the newer wine rather than the old one.

Use ```
sudo apt-get install wine1.2
``` or just search for wine in the software centre and install the second listed package.

You could also search for alternative linux native programs by searching for something similar in the software centre or by googling for it.

---

### Post by OU_Guy on 2010-04-27
Also, wine can be hard to use. It can do the job most of the time though. It won't do every game or program, but a lot will. For a full list:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

