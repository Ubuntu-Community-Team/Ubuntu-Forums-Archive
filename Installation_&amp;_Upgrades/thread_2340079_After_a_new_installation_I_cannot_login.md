---
title: "After a new installation I cannot login"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by yves67 on 2016-10-15
Hello,
The migration from 16.04 to 16.10 failed.
I reinstalled the version 16.04.1, but my /home in another partition (sda5)
and as soon as I typed my password, the system go back to the logon screen (without any error message)

If I use the Guest logon, no problem

If I install with a normal home, no problem...

How can I debug this problem ? 
Why my /home in sda5 failed the system ? 

Thanks a lot for any help
Yves67

---

### Post by ubfan1 on 2016-10-15
You have many "dot" files (files whose first character is a period), which contain configurations for many things, which are now the wrong versions after your upgrade.  Start with .Xauthority and the .cache  directory -- just delete them or move them to another directory you make like "olddot".  Then try to login.  There are many others, which you might have to move too, but start with the two mentioned.

---

### Post by yves67 on 2016-10-15
Thanks for your answer
I delete .Xauthority and .cache and /tmp
same problem

---

### Post by yves67 on 2016-10-15
I have moved ALL the . files to the olddot directory

same problem...

---

### Post by yves67 on 2016-10-15
now, I have ALL files to a data directory .... 

same problem

---

### Post by yves67 on 2016-10-15
OK I have reinstalled 16.04.1 LTS using the normal /home and it is working this way
I will mount my old home to get access

thanks for your help

---

