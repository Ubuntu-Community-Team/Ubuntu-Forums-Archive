---
title: "Installation problem"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by DemoMode on 2008-02-28
Hi,

Im having installation problems with Ubuntu 7.10, when booting the live CD my system either locks up or restarts when the loading bar ( orange ) is full. Running the same disk on VM is perfectly fine and even tried it on several computers, could there be any incompatible hardware on my system that is causing this problem ? Ive also tried it on a IDE harddrive and DVD rom.. my system specs are as follows

Intel Q6600
Abit IP35-E
Team Elite DDR2-800 2GB
Palit 8800GT 1GB
Creative X-Fi Extreme Music
Western Digital 250GB SATA
Samsung 203N DVD+RW SATA
Silverstone Zues 750ZF ( 750watts PSU )

the IDE drives:
Seagate 80GB
LG DVDROM

When i tried it on the IDE drives i made sure i physically disconnected my sata drives.

---

### Post by erginemr on 2008-02-28
You can bypass the orange bar by pressing F6 at the boot selection screen and removing the words "quite splash". Then, please report back the error message you receive when the installer stalls.

---

### Post by dstew on 2008-02-28
> could there be any incompatible hardware on my system that is causing this problem ?Most likely that is the case. See post by erginemr and do that. You can sometimes get the Live CD to work by adding kernel parameters to the kernel line, but not always.

---

### Post by DemoMode on 2008-02-28
Heres the screenshot, i need a fix for both version 6 & 7

[[IMG]http://img148.imageshack.us/img148/9698/v6ft2.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=v6ft2.jpg)
Version 6

[[IMG]http://img167.imageshack.us/img167/418/v7qj5.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=v7qj5.jpg)
Version 7

---

### Post by erginemr on 2008-02-28
I have found a reference to "ata1: failed to recover" error:

[http://ubuntuforums.org/archive/index.php/t-567612.html](http://ubuntuforums.org/archive/index.php/t-567612.html)
[https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25)
[http://ubuntuforums.org/showthread.php?t=590931](http://ubuntuforums.org/showthread.php?t=590931)
[http://ubuntuforums.org/archive/index.php/t-640519.html](http://ubuntuforums.org/archive/index.php/t-640519.html)

but with the exception of the 4th link, all refer to problems on an already installed system. They focus on the use of the keyword "piix". Please read them anyway to see if there is anything valuable in them.

By the way, what is the Logitech USB device?

---

### Post by erginemr on 2008-02-28
Another one:
[http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

Rechecking your screenshots (literally:)) revealed that this is a Logitech mouse. It is probably not the cause of this problem, but for the sake of eliminating the possibilities, can you please unplug it and retry to boot from the Live CD?

---

### Post by erginemr on 2008-02-28
Still another one with a different kernel parameter:
[http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page4.html](http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page4.html)

You should focus on the last post.

---

### Post by DemoMode on 2008-02-28
Tried removing my mouse and keyboard and used a different generic usb keyboard w/o any mouse, same problem

Tried the acpi-off irqpoll, nothing fixed.
The other solutions posted seems to be a problem after installation those cant apply to me yet.

---

### Post by dstew on 2008-02-28
> Tried the acpi-offThe correct parameter is **acpi=off**

---

### Post by aquaticneko on 2008-02-28
Hello,

I am a newbie at installing ubuntu and i recently downloaded the ubuntu gutsy gibbon. I followed tutorials and correctly burned the image to a cd. But my problems lies whenever i try to load the live cd.
It boots correctly and I select install. the first option in the ubuntu menu. The orange bar zooms left and right for a while and then it moves to a screen with this on it.

[*********) "buffer I/O error on device fd0, logical block 0


Where the asterisk is some numbers are. The screen continues to be filled with this line, with the exception that the numbers increase.
After a while it skips to busybox, asking me for a command.


please tell me the problem...

---

### Post by dstew on 2008-02-28
aquatikneko: your problem is similar to, but not identical to, the problem of the original poster (OP). Would you mind starting your own separate thread for your problem? You will get better help that way. Just copy your post and start a new thread.

---

### Post by DemoMode on 2008-02-28
> **dstew said:**
> The correct parameter is **acpi=off**

Yeah, just a typo on my part on the forums.

I guess ubuntu is not for me and my system.

---

### Post by erginemr on 2008-02-29
Before you surrender, here is another thread with very similar symptoms:
[http://ubuntuforums.org/archive/index.php/t-622307.html](http://ubuntuforums.org/archive/index.php/t-622307.html)

a list of available kernel parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

and a few other kernel parameters for you to try:
```
acpi=off noapic, nolapic, pci=routeirq
```

---

### Post by uberlube on 2008-02-29
The 'fix' for this problem is actually a work around. You have to add 'irqpoll' to the boot process. Also delete 'quiet splash' and if it still doesnt work, set the vga. So you will have to add something like:

irqpoll vga=791

---

### Post by erginemr on 2008-02-29
I don't want to bury you under a heap of links, but in case"irqpoll" does not work either...

In this thread a similar problem has been solved by changing the SATA cables or by playing with SATA / IDE settings in BIOS:
[http://ubuntuforums.org/showthread.php?t=637721](http://ubuntuforums.org/showthread.php?t=637721)

---

