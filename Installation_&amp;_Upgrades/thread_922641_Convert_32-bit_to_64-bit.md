---
title: "Convert 32-bit to 64-bit"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by JayeD on 2008-09-17
I'm currently using ubuntu 32-bit and was thinking about changing over to 64-bit but have so much installed and setup that doing so could be a pain. Is there a simple way to do this without breaking everything I currently have set up already?

Also, are there any problems with 64-bit ubuntu, Such as certain things not working, or driver problems, etc? I seem to remember a flash problem at some point.

---

### Post by god0fgod on 2008-09-17
Apparently the 64 bit versions aren't very good I've heard.

I think you need to change your /etc/apt/sources.list file

"deb http://giss.tv/~vale/ubuntu32"

to

"deb http://giss.tv/~vale/ubuntu64"

Then update. Probably a good idea to backup anting important in case that fails.

---

### Post by oldos2er on 2008-09-17
I suggest you read [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) .

 You will need to install 64-bit as a new install; there is no upgrade.

---

### Post by tuxxy on 2008-09-17
> **god0fgod said:**
> Apparently the 64 bit versions aren't very good I've heard.

I think you need to change your /etc/apt/sources.list file

"deb http://giss.tv/~vale/ubuntu32"

to

"deb http://giss.tv/~vale/ubuntu64"

Then update. Probably a good idea to backup anting important in case that fails.


You heard wrong, also why try and advise on a matter that you have no experience with, you dont just change a repository either.

Heres a link to the [64-Bit users group]("http://ubuntuforums.org/group.php?groupid=258") for when you take the plunge :)

---

