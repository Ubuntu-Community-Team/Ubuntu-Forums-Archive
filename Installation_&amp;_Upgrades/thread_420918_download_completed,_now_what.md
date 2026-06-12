---
title: "download completed, now what?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by jfh432 on 2007-04-24
How do I use md5 sums to confirm integrity of file ?

---

### Post by BoneKracker on 2007-04-24
if you are on a Windows system, then you need to download an md5 checker program.  There are lots of them.  I don't have a recommendation because I haven't used one on Windows in a long time.  Most of them have "md5" in their name.  Any shareware site will have them (like tucows, for example).

If you're on linux, you do one of the following:

a) if the file came with another file that's a properly-formatted digest (it should end with .md5 or .digest), then you just type
```
md5sum -c filename

```(where filename is name of the _digest file_, not the main download)
The program will do the comparison for you and tell you whether it's ok or not.

b) if you don't have a digest, per se, but you do have something that shows what the md5 string should be, then you type
```
md5sum filename
```
(where filename is the name of _the main file you downloaded_, not the file containing the md5sum string).  This will produce a newly-computed md5sum string for the file.  Then you just visually compare that to the string that you already had.  If they match, then you're good.

Unless things have changed, the file provided by Ubuntu that contains the md5sums is not a digest, it is just a list.  So you have to use the latter method.

---

### Post by sradhakrishna on 2007-04-24
Actually, a pretty neat explanation is available at [Ubuntu's help site]("https://help.ubuntu.com/community/HowToMD5SUM")

As a newbie to the linux/ ubuntu world, that's one thing that I liked a lot. Help's available so freely - the help site, the [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), this forum...

Go Ubuntu!! 

Radha. :)

---

