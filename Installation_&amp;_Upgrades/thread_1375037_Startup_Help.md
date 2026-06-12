---
title: "Startup Help"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by viper3ez on 2010-01-07
i have 9.10 installed beside windows 7. at first, the dell logo shows, it gave me the option to pick ubuntu or windows 7 loader.

after that, every time i do an update, it adds one more option so i now have something like

ubuntu version x.x x.17generic
ubuntu version x.x x.17generic (recovery)
ubuntu version x.x x.16generic 
ubuntu version x.x x.16generic (recovery)
ubuntu version x.x x.14generic 
ubuntu version x.x x.14generic (recovery)
windows 7 loader.

in summary, when i need to pick what OS i want loaded, i see 4 options now instead of 2.

how can i get rid of the extras?

---

### Post by gordintoronto on 2010-01-07
Assuming you installed 9.10 from scratch, not as an upgrade from 9.04:

You can open Accessories/Terminal and enter the command:
gksudo gedit /etc/default/grub 

If you would like to know what you are doing, have a look at:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by viper3ez on 2010-01-18
i could not tell what to do in grub config

i just dont want to see the version 14.

i want it to show ver 17 and win7 as list of OS when grub starts

i know it does no affect the system, it just irritates the crap out oof me

---

### Post by audiomick on 2010-01-18
There is, by coincidence, a thread running right now on that subject here
[http://ubuntuforums.org/showthread.php?t=1384601](http://ubuntuforums.org/showthread.php?t=1384601)

---

### Post by presence1960 on 2010-01-18
You want to leave the two most recent kernels in case the newest one borks, that way you can boot Ubuntu from the second newest kernel. I would leave 17 & 16.

Go to Synaptic Package Manager and mark for complete removal linux-headers-2.6.31-14 & linux-image-2.6.31.14

Once removal is complete open a terminal and run ```
sudo update-grub
```
This will refresh grub.cfg to reflect the kernel removal. When you boot next time the GRUB menu will reflect that.

This is assuming you use GRUB2 not legacy GRUB 0.97

On a lighter note if that irritating you is the worst thing that happens today you are fortunate indeed!

---

