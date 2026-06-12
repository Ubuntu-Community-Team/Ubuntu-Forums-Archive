---
title: "Ubuntu 5.10 Install Woes"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by Kheldar on 2005-12-04
Getting a little fustrated with Ubuntu installation ](*,) 

I downloaded the ISO, bured to CD (Tested okay, installed to a vmware session fine). So we know the CD is fine ....

Started install on my PC, install hung while copying files (Upon investigation it was due to my Sony DVD/Rw needing DMA enabled, so upon investigation I need to boot and use 'expert' mode and use the -d1 switch). Okay did that, seemed to install fine....BUT (Here is where my troubles begin)

Cannot use any kind of administrative functions (It prompts for a password), I used my password that I defined on install and the root password that was defined in the install and neither work.

If I do a default install as a test on my vmware session, (non-expert) everything runs and works beautifully. (This is what I want)

I am not overly happy that I am forced to use 'expert mode' and then have issues with the useability of the system. Is there any way to correct the problem or is there a way to use the default option with a simple switch to enable DMA? 

Replacing the DVD with another CD player is not an option, PXE install pukes because it is missing base files (from unreachable ftp, http, etc). I just want to drop the cd in and go. Other distro's work fine (Suse, Mandravia) but not Ubuntu. I do LIKE ubuntu the best so far, but will have to do with another distro if I cannot get the install quirks worked out....


Fustrated ......#-o

---

### Post by doitashimashite on 2005-12-04
Setting a root password could help:

sudo -s
(enter your user password)
passwd root
(enter desired root password)

Then see if this solved your problem.
The root password should only be entered in case you start processes for which administrator rights are required. During normal use, this is not necessary.

---

### Post by SilentCacophony on 2005-12-04
Hi. If I understand your post correctly, the fact that you used the 'expert' install, which has you set up a root account by default, is now interfering with things which require sudo or gksudo.

I do believe that I remember specifying options on a 'normal' installation, so I'd say that's worth a try. There may be a way to fix it, without reinstalling, though.

I've heard of people who have enabled the root account and regretting it (for different reasons, including sudo problems,) and disabling the root account seems to sometimes help. If you wish to try it, AFAIK you just issue this in a terminal:

**sudo passwd -l root**

Of course, you may reverse this using the commands in the above post if you wish (or I believe the -u option works.)

---

### Post by Kheldar on 2005-12-04
I figured it out :) 

When doing a 'expert install', at the point it asks for a root password, leave it blank and the system then sets up sudo like the default install.....

Thanks for the help all!

:grin: 

Kheldar

---

### Post by taygan on 2006-02-05
you can also enable dma on your dvd drive from the console (alt-f2?) during the beginning of the regular setup and type sudo hdparm -d1 /dev/hdd (or whatever /dev your dvd drive is)

It's been months since I had this problem, sorry I forgot the exact details.

Then make sure you permanently enable DMA after you're installed:

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

