---
title: "Help with Grub menu please?"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by Katin Crawford on 2006-07-09
After some experimentation with Windows and Ubuntu on different drives and partitions I found a setup that works, sort of. I have 2 SATA drives with Windows on the first SATA (sda) and the second SATA having 2 FAT32 partitions (sdb1 and sdb2). Ubuntu is installed on a IDE drive along with a swap partition. I have tried installing the grub menu over the master boot record and when i reboot the grub menu does not start and the computer boots into Windows instead. After installing the grub menu to the first SATA (sda), when booting up I get a screen that scrolls GRUB across, like this:

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB

and so on and so forth.

any insight on how to fix this?

---

### Post by woedend on 2006-07-09
eek...never heard of that so searched google.
A search for "grub grub grub"  brings up a lot of results and different things to try.  There's even one on ubuntu...here is a short list of links perhaps you could read through.
Would be nice if the bios autodetect fixed it though, since that seems to be the easiest.
[http://doc.rocklinux.org/wiki/InstallationProblems](http://doc.rocklinux.org/wiki/InstallationProblems)
[http://www.ubuntuforums.org/showthread.php?t=24113&page=3](http://www.ubuntuforums.org/showthread.php?t=24113&page=3)
[www.kclug.org/pipermail/kclug/2002-October/010821.html](www.kclug.org/pipermail/kclug/2002-October/010821.html)
[www.gentoo.org/doc/en/grub-error-guide.xml](www.gentoo.org/doc/en/grub-error-guide.xml)
[http://64.233.187.104/search?q=cache:XmcKEDsGcVQJ:www.linuxquestions.org/questions/showthread.php%3Fthreadid%3D171636+%22grub+grub+grub%22&hl=en&gl=us&ct=clnk&cd=18&client=firefox-a](http://64.233.187.104/search?q=cache:XmcKEDsGcVQJ:www.linuxquestions.org/questions/showthread.php%3Fthreadid%3D171636+%22grub+grub+grub%22&hl=en&gl=us&ct=clnk&cd=18&client=firefox-a)

also, if you can, can you post your
/boot/grub/menu.lst  file so that others more knowledgable in that particular area may recognize a problem.

---

### Post by Katin Crawford on 2006-07-09
I don't have a /boot/grub/menu.lst. I did not install the grub on the drive with Ubuntu on it, but rather the Windows drive. When looking in windows I do not see anything with boot or grub or menu...just the boot.ini and ntldr.

I have no idea where the silly grub went. 

I will look through those links though. thank you!

---

### Post by woedend on 2006-07-09
ah I see, dopey me!  (sorry haven't slept in a long long time).
If you do find a solution please remember to post it here.

---

### Post by confused57 on 2006-07-09
It may not help, but here's an excellent grub tutorial:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I don't have any SATA drives, but I've seen quite a few posts of people having problems installing grub to a SATA drive.

You might be able to fix the mbr on the SATA drive by booting up with the Windows Install CD(not the recovery CD), press "r", then enter   fixmbr

Maybe you can reinstall grub to Ubuntu on the IDE drive, set your bios to boot the IDE drive first...once you're able to boot into Ubuntu, you could add the Windows entry to your /boot/grub/menu.lst file...see this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Someone else familiar with SATA drives can probably give you some better advice, but thought I'd give you some options.  Good luck.

---

### Post by Katin Crawford on 2006-07-10
thanks! i tried installing the grub to the IDE drive to no avail. the computer just boots into windows when i do that...and my bios is a little weird...i cant seem to get it to boot to the ide first.

i also cant choose to select the hard drives myself, just auto detect.

---

### Post by confused57 on 2006-07-10
> **Katin Crawford said:**
> thanks! i tried installing the grub to the IDE drive to no avail. the computer just boots into windows when i do that...and my bios is a little weird...i cant seem to get it to boot to the ide first.

i also cant choose to select the hard drives myself, just auto detect.

On my Dell Dimension 4550, I can press F12 during startup, which gives me various boot options.  Possibly, your computer may have something similar...check the motherboard documentation, if you have it or maybe do a google search for your system bios.

---

### Post by Muppeteer on 2006-07-10
I'm getting this same grub error too...

I've got 2 drives. Windows on a partition on the first drive and ubuntu on a partition on the second drive. They're both sata. I've had Suse 10 with grub working on this system, which is why i can't understand the problems with ubuntu. I aswell don't have any option in my bios to auto detect HDD's...

Seems though it's a Ubuntu prob and not grub...

---

### Post by shuflie on 2006-07-10
I've got WindowsXP on my IDE master and Ubuntu on the slave, with GRUB installed on the master. Whenever I boot I get "error 17" reported by GRUB. I've found that setting the computer to boot from CD and keeping the WindowsXP CD in the drive lets me boot and GRUB shows the boot menu.

---

### Post by Katin Crawford on 2006-07-10
well, in my bios setup I turned on the SATA drives and re-installed grub on the IDE drive and I can now boot into Ubuntu, but now Windows. Now that the grub menu does load I can poke around with the menu.lst

---

### Post by confused57 on 2006-07-10
> **Katin Crawford said:**
> well, in my bios setup I turned on the SATA drives and re-installed grub on the IDE drive and I can now boot into Ubuntu, but now Windows. Now that the grub menu does load I can poke around with the menu.lst

Maybe this thread can help:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

