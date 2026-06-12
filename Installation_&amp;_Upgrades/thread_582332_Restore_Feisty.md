---
title: "Restore Feisty"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by bartomania on 2007-10-19
Hey... 
I started the upgrade yesterday and it got kinda stucked.... there were a couple of errors like the installation of [tzdata]("http://ubuntuforums.org/showthread.php?t=581497") and also the same list I saw on that post:
locales
language-pack-en-base
language-pack-gnome-en-base
util-linux-locales
ubuntu-minimal

The thing is I had to reboot my PC and when it started the X wouldn't run. I saw that it had to do with the kernel module(s) for my Nvidia card. I edited the /etc/X11/xorg.conf to enter in failsafe mode and I got the X working.

The thing is that now I'm not sure how to finish up the upgrade or go back to Feisty Fawn
I tried doing apt-get update, apt-get upgrade, apt-get dist-upgrade, etc. and some problems were solved. I actually thing that the problem with tzdata and the other related packages was fixed. 
But now I'm stalled.

Can you give me some ideas?

Some extra info:
I'm running Ubuntu Feisty Fawn 64. I have the Cds (for Feisty, not for Gutsy).
I have a partition for my /home where I have most of the important information that I need to keep. I could format the / but I'd rather not if its possible.

Any ideas can help.

Thanks in advace!!

---

### Post by Pumalite on 2007-10-19
Save your /home and data and do a clean install of the version you want.

---

