---
title: "Black Screen of Death - Part II"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by myke on 2008-01-10
OK  ... after trying some fixes from some very helpful forum members to fix my shutdown/freeze problem which eventually led to Grub not booting up fulling and freezing after the K/Ubuntu load up splash screen and blanking to a black screen with a blinking cursor .... it's gotten even WORSE.

Didn't think that was possible but it is.

Now .... I Grub doesn't come up at all and I can't even get into my computer at all even thru the WinXP side.  I had to shut it down last night and wait until arriving to work early this morning in order to post a message requesting help.

Is there anyway to fix Grub (maybe with the live cd?) so I don't have to not only fresh install K/Ubuntu but my WinXP partition (which I still need for work) as well???     I was already leaning toward starting my Kubuntu side fresh as I could back up the data on my portable hard drive or the WinXP side but now I can't even do that because I can't access either partition.

HELP!   HELP!   HELP!       How do I fix Grub and get something to load??? Does the live cd come with a repair utility???    When I start the pc, the grub version number appears at the top and then it says error 13...    I don't remember the full number but it was 1300 something.

Thanks a load if anybody can help to keep me from a double fresh install.   It'd take forever and I'd lose loads of settings and data.

---

### Post by Partyboi2 on 2008-01-10
Try super grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by myke on 2008-01-10
I'm at work so I can't say whether it will work or not but thanks for the suggestion.   I've already went to the site and asked my IT guy here to burn the ISO for the program to cd for me and he's fine with that.  So ... when I get home in a few hours I'll try it and hope it works.  If it does, I'll owe you a big big thanks from across the big pond.

---

### Post by ericartman on 2008-01-10
Second on Super Grub, great learning tool and their page is full of helpful info. Saved my rear more than once. Good Luck

Cart

---

### Post by dabl on 2008-01-10
Herman's Grub site is also a nice one to bookmark for such situations:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

:)

---

### Post by jwmislan on 2008-01-22
Hi Myke
Ubuntu install cd has the option to run (Live), or to install.
If you choose run Live from cd,  then you can get into a Ubuntu Gui where you can do repairs, and get help from the internet as well.

May be that simply, in an xterm, running update grub will fix grub boot ?
If not, reboot back into the live cd system again to further investigate - check output of the, dmesg | less command in an xterm, also look at /var/log/messages - for boot errors clues.

JWM

---

