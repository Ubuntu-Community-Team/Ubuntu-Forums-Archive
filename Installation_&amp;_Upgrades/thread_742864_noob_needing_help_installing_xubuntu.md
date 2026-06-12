---
title: "noob needing help installing xubuntu"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by joshuayu101 on 2008-04-02
When installing xubuntu alternative cd the install hangs around 82% to 84% i dont know why it does this
any clues?


the cd has no defects and check the md5 sum for the iso and came back okay

system specs
PIII
128mb ram
laptop
13gb hard drive

---

### Post by housam on 2008-04-02
Are you making a dual boot or just only ubuntu will be on your laptop? 
Did you made a preinstallation partitioning or just gave ubuntu the full HDD?

---

### Post by joshuayu101 on 2008-04-02
dont worry its installing now, ppl said its due to my low ram so i had to wait for a while

---

### Post by fela on 2008-04-02
yeah, 128mb isn't exactly cutting edge....if i may say so :D

---

### Post by erginemr on 2008-04-02
If your machine is connected to Internet during the installation, it may also be the case that the installer is trying to update the packages from the net. 

For more info:
[http://ubuntuforums.org/showthread.php?p=4525801](http://ubuntuforums.org/showthread.php?p=4525801)

---

### Post by ZALMAN on 2008-04-02
I agree with erginemr that the installation is probably looking for update packages, also at that stage of installation it's also comparing image files.If there is an internet connection available the deflault connection in in roaming mode, therefore it will even log on on a connection sharing machine, ie windows ics etc.

---

### Post by RobbanC on 2008-04-02
I had this problem as well when my box wasn't connected to my network. It hung at 82% and said it was looking for apt...something. I let it try for about 30min, then I gave up. 
The first time I simply killed the process (apt), but the system probably didn't finish install itself then. 

I run the installer again, this time with a functional internet connection and presto: no problems.
Therefore, my guess would be that your computer can not connect to the internet for some reason... And here is were my knowledge ends.

---

