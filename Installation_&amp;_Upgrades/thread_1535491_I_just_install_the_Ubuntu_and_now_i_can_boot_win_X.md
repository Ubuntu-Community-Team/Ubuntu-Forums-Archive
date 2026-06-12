---
title: "I just install the Ubuntu and now i can boot win XP cus the pc this is Win Vista"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by juanclunac on 2010-07-21
Well, thats it, i just installed ubuntu, but in the but i cant choise to star win XP (my win previows OS) just appears Win Vista and when chose vista givesme an error saying that cant find the file windows/system32/hal.dll, i can see the windows partitions trough Ubuntu, and looks fine, all the archives are there, the entire OS and my Win Documents, i think its a problem with the boot program. can anyone help me?

---

### Post by oldfred on 2010-07-21
Sometimes the recovery partition is identified as Vista for many of those XP installs after Vista was released.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by juanclunac on 2010-07-21
i just seen the boot.ini now i just have a little problem, kid of embarrassing, i don't know in which number partition i installed windows, i think in the 1, but if don't there is a way to now for sure?

doing a little more of research, i have notice that for some reason the boot is not on my windows installed partition, but in my windows dates partition, ill adjunt a screen of my partitions administration.

Windows is installed on the first NTS partition /dev/sda5
NOTE: the boot.ini also was on /dev/sda2
[U][[IMG]http://img197.imageshack.us/img197/3015/screenpc.th.png[/IMG]]("http://img197.imageshack.us/i/screenpc.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")[/U][URL="http://imageshack.us"]
[/URL]

---

### Post by juanclunac on 2010-07-21
Ive already solved the problem. the partition was the number 4. thanks for the help :)

---

### Post by oldfred on 2010-07-21
Windows does not boot directly from extended partitions but has to boot from a primary partition. Linux does not care, it will boot from primary or extended partitions.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

