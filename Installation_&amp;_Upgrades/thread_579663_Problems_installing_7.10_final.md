---
title: "Problems installing 7.10 final"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Jake77 on 2007-10-18
I just downloaded ubuntu 7.10 final amd64 cd image, burned it to disk, and tried to install it. But no luck..
it loads the kernel from cd and shows the ubuntu text but does not get any further. the 3,5" disk drive light keeps blinking, but nothing more. After some time, it drops to busybox and this can be seen on screen:
[IMG]http://koti.mbnet.fi/jarkko77/tmp/mesg.jpg[/IMG]

About my configuration, I have 2 sata hard disks in ahci mode, 2 dvd-drives on ide bus. 
Asus p5b deluxe wifi motherboard and e6400 cpu.

I have previously installed the 7.10 amd64 gutsy beta (not rc), and it installed just fine.

Any ideas what I could try?

---

### Post by Topsiho on 2007-10-18
I have the same, or nearly the same, problem installing Kubuntu, from the RC, and from the final release. I did not have this problem installing from the tribal releases (the releases prior to the RC).
I have reported this in bug report #152054, without any reaction, after the RC failed to install.
Same problem I had with Feisty, as many other people did (don't know the percentage relative to the total Ubuntu users :) ).
With Feisty I solved the problem by using the alternate disk. It has an other installer and that one (named a graphical installer but is just as easy to use, if not easier) works perfect, and I suppose that that was used in the tribals too.
I don't know whether this has anything to do with the problem: the computer on which I have this problem has two hard disks, just as yours, while my two other computers, each having only one hard disk, install the Live CD fine.

Hope this helps, and suggest you confirm my bug report, and use the alternate CD....

---

### Post by Jake77 on 2007-10-18
Thanks for the reply Topsiho :)

I just confirmed your bug report. I'll try the alternate installation cd, thanks for the tip.
Would be nice though, if the default installation worked also, especially because it did already 
work in the earlier betas.. ;)

---

### Post by qwicfingers on 2007-10-18
I downloaded the 64bit torrent and I'm having a similar problem. At the CD boot menu I choose an option the kernel loads and then the screen goes back and turns off. Will have to try the alt CD.

---

### Post by Jake77 on 2007-10-18
Now running ubuntu 7.10 64bit succesfully :)

At first I tried the alternate cd. It printed out the same thing to the screen as the normal installation cd, plus some more stuff about usb etc.. 

Then, I just decided to try and unplug my another dvd-drive, so there was only 1 dvd drive connected. The installation went just fine, no problems whatsoever :guitar: So maybe it has something to do with the ide controller. My motherboard uses the JMicron JMB363 chip to connect the ide devices to the system, and both my dvd drives were connected to that controller. I am now running ubuntu with 1 dvd drive.. I will try to reboot later, and connect the other dvd drive too to see if the problem appears again.

---

### Post by Topsiho on 2007-10-19
Glad all is OK now, and thanks for confirming my bug report on Launchpad.
Maybe you can add your solution to this report, might be of assistance for the developers to find the cause of what was your problem.
It is by these reports that we ordinary users can do something back, and help improve (K)Ubuntu, and generally Linux  ....

:guitar:


Topsiho

---

