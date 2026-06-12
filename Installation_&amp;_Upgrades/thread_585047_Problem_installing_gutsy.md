---
title: "Problem installing gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by SledgeHammer_999 on 2007-10-21
I've downloaded Gutsy **twice**. In both cases, when I tried to boot in the "Start or Install Ubuntu"  the graphical progressbar(with ubuntu's logo) came up and after a few seconds I am thrown to a black screen saying something along these lines:

> udevd-event[2452]: run_program: '/sbin/modprobe' abnormal exit


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

and I am not able to install Gutsy. The Beta was installed fine and I am using it with no problem. But I want to use the final version of Gutsy. 

Something I forgot: I am trying to install the AMD64 version(yes my sytem supports it).

Do you have any suggestions?

thank you in advance

---

### Post by SledgeHammer_999 on 2007-10-21
bump

---

### Post by Kaptain Chaos on 2007-10-21
Hello,

Seems to be a general problem with this latest release. I managed to upgrade from 7.04 to 7.10 without problem UNTIL the reboot, get the same black screen but with a [2118] error code. This is happening with the newer kernel, if I use the previous kernel Gutsy boots but I then have problems with X 'forgetting' my settings at every reboot. One thing that has been mentioned [in a bug report]("https://bugs.launchpad.net/ubuntu/+bug/154591") refers to booting with 2 hard drives installed (not sure if this is what the 'udevd-event' refers to.

Hitting the F6 button when the cd first boots up will allow you to enter the boot parameter all_generic_ide. It MAY get you past the first hurdle, but I'm no expert.

My suggestion is continue with the Beta version if it's running well on your set up and wait for the dust to settle on the current distro.

---

### Post by SledgeHammer_999 on 2007-10-21
well I tried this boot parameter->"nosplash" and I erased "quiet". And it seems that it tries to read from my floppy!!!. And after a few I/O failures(floppy) the above message pops.

Indeed I have more than 1 hard drives. I have 3. 1pata and 2sata. I'll try now the "all_generic_ide"

---

### Post by arno77 on 2007-10-22
> **Kaptain Chaos said:**
> Hello,

Seems to be a general problem with this latest release. I managed to upgrade from 7.04 to 7.10 without problem UNTIL the reboot, get the same black screen but with a [2118] error code. 

I have the very same problem. Upgrade fine but after reboot black screen but no error code. I thought first it has to do with that I let gutsy install the proprietary video driver that it detected. 

I have posted this also elsewhere [http://ubuntuforums.org/showthread.php?t=585633](http://ubuntuforums.org/showthread.php?t=585633)

But it seems a more general problem.

My big problem is that when I boot 7.04, which worked perfectly fine, I also only get a black screen back. So I can't do anything anymore.

Would be great if anybody could suggest a workaround.

---

### Post by nikef on 2007-10-22
> **SledgeHammer_999 said:**
> I've downloaded Gutsy **twice**. In both cases, when I tried to boot in the "Start or Install Ubuntu"  the graphical progressbar(with ubuntu's logo) came up and after a few seconds I am thrown to a black screen saying something along these lines:



and I am not able to install Gutsy. The Beta was installed fine and I am using it with no problem. But I want to use the final version of Gutsy. 

Something I forgot: I am trying to install the AMD64 version(yes my sytem supports it).

Do you have any suggestions?

thank you in advance

I get this error 2  :confused:

---

### Post by pgarrett on 2007-10-23
I've run into a similar problem.  Install goes fine but system then locks up on reboot.  I get the message:

udevd-event[2393]: run_program: &#8216;/sbin/modprobe&#8217; abnormal exit

Seeing the note above about a possible problem w/ two hard drives, I disconnected my secondary IDE.  Now I get:

udevd-event[2405]: run_program: &#8216;/sbin/modprobe&#8217; abnormal exit
(different event ID).

If I remove 'quite' from the boot commnd line, the system halts at 'waiting for root file system'.

This in on an AMD Sempron 3000+ with 512mb ram and IDE drives.  System ran 7.04 perfectly fine.

edit: I left the system waiting while I typed this message.  After a while the following message came up:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /prc/modules ls /dev
ALERT! /dev/mapper/Ubuntu-root does not exist. Dropping to a shell!

---

### Post by SledgeHammer_999 on 2007-10-23
plz post it to the bug report mentioned. I think this is the fastest way to get noticed by the developers and fix it. 
I hope there will be a new iso very soon. Otherwise I have to stay with Feisty.

---

### Post by Mr_Ada on 2008-04-06
I have been using Gutsy for some time and now all of a sudden it doesn't want to boot.  The initramfs Busybox stuff comes up and I don't know what to do.  I'll try to capture the information next time but all of this nonsense seems to have occurred when I tried to install Windows XP64 on another disk in the same PC.  I don't believe I allowed windows to mess with the MBR but you never know what they'll do.

Sheeshhh.

Well at least I have Windows running.  I can see my Linux Harddrive using "explore2fs" but I'd sure love to get my system working too.

Also I thought I had RAM issue so I did memtest.  I moved the memory to the other 2 slots and Windows seems happy for the moment.  Would moving RAM cause linux to hurl chunks?

chris

---

### Post by Pumalite on 2008-04-06
You can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dobrowski on 2008-04-25
I am facing the same issue trying to install Hardy Heron.  Please bear with me since it is my first install and it may be an obvious error.  

I was receiving the /sbin/modprobe error mentioned by others.  I searched here and saw it was related to multiple harddrives which I have also. 

I tried, using the install disk to hit F6 and then added "all_generic_ide" after the text line that appeared.  After hitting enter it seemed to run and then freeze on the splash screen without the orange bar moving back and forth.  

Is this typical? A problem with having multiple drives?  My misentering the boot parameter in the wrong way? 

Thanks for any guidance.

---

