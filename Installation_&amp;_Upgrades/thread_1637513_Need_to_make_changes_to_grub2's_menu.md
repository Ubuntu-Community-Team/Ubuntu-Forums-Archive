---
title: "Need to make changes to grub2's menu"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by obarthelemy on 2010-12-04
Hi.

I'm trying to switch to Linux (total Linux noob here, sorry, bear with me ?). I have it installed and running multi-booting on my Win7 HP Mini 100 Netbook; things are mostly fine, I'm trying to both tweak the config and add some creature comforts right now.

My first issue is the GRUB2 boot menu. Though it works, it has 2 issues:

1- It lists one OS per partition, and since I have 2 OSes (Win7 + Ubuntu) plus 1 Win7 recovery partition, and 6 partitions total, this is way too much and confusing. How do I get rid of the extraneous entries ? I'm pretty sure I know which those are; but the startupmanager won't let me change much, and the /etc/default/grub file loudly states DO NOT EDIT, and looks complicated (compared to the older menu.lst which I've looked at before). How can I at least comment out useless/redundant grub boot menu choices ?

2- the grub boot menu is ugly and all jumbled. Is there any way, assuming I can trim it down to Win7, Ubuntu, and then Win7 recovery and Ubuntu recovery, that I can put the entries in that order, with a separation (a few blank lines and a solid line ?) between the 2 main choices, and the 2 recovery ones ? I'll add a nicer background image too, but I seem to have instructions for that.

I've read the grub2 doc, installed startupmanager... neither helps ?

I don't want the first impression of people (including me ^^) I'll be showing it to to be "wow, what a mess").

Thanks for any help,

Olivier

PS I know 6 partitions is a lot on a small netbook. Blame HP for needing 3 for their Windows setup, and me for being anal retentive and liking my docs NOT on my sys/apps paritions.

---

### Post by Quackers on 2010-12-04
The grub.cfg file has "do not edit" but the /etc/default/grub file doesn't.

Have a look at these guides by drs305

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by obarthelemy on 2010-12-04
Thanks, that seems to be it... Skimming the articles, the process is frighteningly complex though... didn't anyone realize that the first impression of Linux people get is the grub menu, at that it needs to be, if not sexy, at least not overwhelming, and riddled with false, redundant, un-prioritized items ?

Oh well... I'll probably leave it as is...

---

### Post by Quackers on 2010-12-04
That's what most new users would do. 
It takes a little time to get used to using Ubuntu and in particular the terminal. Once you've run a few things you will be a little more confident. Most of it is quite simple (eg just one command to get rid of the Memtest entries) and some are a little more complicated. You'll doubtless have a go when you feel a bit happier about it :-)
Don't forget, you can always copy a file you are thinking of editing, so at least you can always go back!

---

### Post by oldfred on 2010-12-04
I started off with a partial custom menu by copying my windows entry and a few others into 40_custom, editing to suit (like old menu.lst editing), turning off the osprober so I did not have duplicate entries and did edit some code to limit it to two Ubuntus. After any changes you have to run sudo update-grub (which I always forget, reboot find it did not update and then run it.).

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

