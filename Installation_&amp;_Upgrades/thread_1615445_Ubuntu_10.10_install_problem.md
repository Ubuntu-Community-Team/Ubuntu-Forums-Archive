---
title: "Ubuntu 10.10 install problem"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by lhill011 on 2010-11-07
[SIZE=3]Hello guys. I'm having problems with my ubuntu installation, but first let me tell you all the steps i've taken before I ended up here :(.

I downloaded the live cd from the site and booted it up, I have an existing windows xp installation in my hard disk so after running the installation wizard I choose the option use entire disk because I only want to run ubuntu, now the installation was in progress when the power went out so as soon as the power gets back on i booted the live cd again and started the installation wizard but now, it can not detect the hd.

I tried looking it up from disk utility, its in there but it says the HD is unknown. I can not format,delete.

 I tried using gpart but it says 0 device detected, when I open up a terminal and type "sudo fdisk -lu" nothing comes up.

So now I decided to install winxp back but it too wont let me, the hd comes up as unrecognizable disk and I cant format/delete/create partitions [/SIZE]. [SIZE=3]I tried using Active partition recovery, but it was unable to recover anything, it still says unallocated disk.

So now I cant install winxp or ubuntu anymore. I hope someone can help me with this problem I really would appreciate it alot thank you. :KS

P.S.
My hard disk is a seagate baracuda 7200.9 sata 160g
[/SIZE]

---

### Post by Quackers on 2010-11-07
Try booting from the Ubuntu Live CD and select "Try Ubuntu" rather than installing it. When the desktop appears use testdisk to examine the HDD. I'm not sure whether testdisk is acutally on your CD so if it isn't download/install it using Synaptic Package Manager.

---

### Post by sikander3786 on 2010-11-07
I think testdik is not present by default. Needs to be installed.

To the OP:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Please try this command and post the output

```
sudo gpart /dev/sda -W /dev/sda
```

---

### Post by lhill011 on 2010-11-07
[SIZE=3]Hi guys, thanks for the quick response ;) 

To Quacker, I cant seem to get synaptic to download testdisk

To sikander3786 this is the output of that command:

ubuntu@ubuntu:~$ sudo gparted /dev/sda -W /dev/sda
======================
libparted : 2.3
======================
Error fsyncing/closing /dev/sda: Input/output error
/dev/sda: unrecognised disk label
Error fsyncing/closing /dev/sda: Input/output error
Could not stat device -W - No such file or directory.
Error fsyncing/closing /dev/sda: Input/output error
/dev/sda: unrecognised disk label
Error fsyncing/closing /dev/sda: Input/output error

It then opened gparted and I was able to see my hd which i was not able to before, but it shows as unallocated 149.05 gib 


[/SIZE]

---

### Post by Quackers on 2010-11-07
Do you have an internet connection? It may possibly need an ethernet cable.

---

### Post by lhill011 on 2010-11-07
[SIZE=3]Hello Quackers, 

I have succesfully downloaded testdisk, I did the analyze option and this are the results;

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

     Partition                  Start        End    Size in sectors


No partition found or selected for recovery

[/SIZE]

---

### Post by Quackers on 2010-11-07
Is there an option to format the disc?
I wonder if the sata drivers are gone? Do you have them on disc?

---

### Post by lhill011 on 2010-11-07
[SIZE=3]Yes it does, but after applying changes to disk it gives me a result saying "Cant write to disk", about the sata drivers I dont think I have them :([/SIZE]

---

### Post by Quackers on 2010-11-07
I wonder if the power outage borked the disc completely. I didn't like the I/O errors it came up with before. A power outage while disk input/output is occurring seldom has a happy ending, I'm afraid. However, I would have thought that the disc should still be recognised.
It may be beneficial to wait for others' input on this. There are people here who know much more than me about this kind of thing.
Good luck to you :-)

---

### Post by sikander3786 on 2010-11-07
So you have reached a point of no return.

In my opinion, the best way around for now will be to go to your manufacturer's website and download the diagnostic tools to scan your HDD. Hope those are successful for you :-)

---

### Post by lhill011 on 2010-11-07
[SIZE=3]Thank you for your patience Quackers and sikander3786, yes I think that is the best option for now[/SIZE]. [SIZE=3]I will keep you guys updated hopefully theres a fix for it. Again thank you so much and God bless :)[/SIZE]

---

### Post by Quackers on 2010-11-07
I hope so :-)
You're welcome.

---

