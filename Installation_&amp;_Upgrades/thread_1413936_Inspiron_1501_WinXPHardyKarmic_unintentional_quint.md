---
title: "Inspiron 1501 WinXP/Hardy/Karmic unintentional quintuple boot???"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by InspironDualBoot on 2010-02-23
I've just had to reinstall WinXP on a Dell Inspiron 1501. An ideal opportunity to try out Ubuntu. First I tried a WinXP/Hardy Heron dual boot - all seems okay. Next WinXP/Karmic dual boot - all seems okay. Then, why not, WinXP/Hardy/Karmic triple boot - all seems okay.
Playing with each OS I noticed that Hardy had a couple of update notifications. So I opened Update Manager, went on-line, hit [Check] and was informed that there were 200+ Important Security Updates - I installed these. 
Better check Karmic too - similar story, installed 200+ updates.
Everything still seems okay in WinXP, Hardy and Karmic.

However, I've just noticed that the Grub2 boot menu now displays eight "Ubuntu" lines, as opposed to the four lines I had originally

Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
...
Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda7)
Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)(on /dev/sda7)
Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (on /dev/sda7)
Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)(on /dev/sda7)

I guess it's something to do with the updates.
What should I do to tidy it up?

---

### Post by InspironDualBoot on 2010-02-24
It's beginning to make sense - running update-grub (on Karmic, setting up a Grub2 splashscreen) gives:

[FONT=Verdana]$ sudo update-grub
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.tga
Found Debian background: moreblue-orbit-grub.tga
Found Debian background: Lake_mapourika_NZ.tga
[B]Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic[/B]
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
**Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda7**
done
$[/FONT]  

So it's clearly the files in /boot on each filesystem (abi-###-generic, config-###-generic, initrd.img-###-generic, System.map-###-generic, vmcoreinfo-###-generic (on Karmic only) and vmlinuz-###-generic, where ### = 2.6.24-24 and 2.6.24-27 on Hardy, and 2.6.31-14 and 2.6.31-19 on Karmic) being picked up.

Also when I installed the grub2-splashimages package on Karmic I got  this:

$ sudo apt-get install grub2-splashimages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.[/B]
The following NEW packages will be installed:
  grub2-splashimages
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 9,776kB of archives.
After this operation, 14.5MB of additional disk space will be used.
Get:1 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) karmic/universe grub2-splashimages 1.0.0 [9,776kB]
Fetched 9,776kB in 9min 56s (16.4kB/s)                                         
Selecting previously deselected package grub2-splashimages.
(Reading database ... 135138 files and directories currently installed.)
Unpacking grub2-splashimages (from .../grub2-splashimages_1.0.0_all.deb) ...
Setting up grub2-splashimages (1.0.0) ...
$

So I guess that I can just get rid of the 2.6.24-24 and 2.6.31-14 files. But how should I do this? I guess I don't just delete the files. I assume the 'autoremove' mentioned above would only remove the headers packages.

---

### Post by InspironDualBoot on 2010-02-24
...I also noticed a lot on the interweb indicating that multi-booting (as opposed to dual-booting) Windows and Ubuntu is problematic. I didn't realise that, and it appears that my computer (a bottom of the range 3 year old Dell Inspiron 1501) didn't either!

As far as I can tell (no thorough testing, just web-browsing and using a few apps from each of WinXP, Hardy and Karmic boots) everything seems okay (bar some minor Hardy boot glitches , and some Karmic logout/shutdown glitches).

Basically this is what I did. I don't know why I did it this way, and I'm not sure why it appears to work:
1) Repartitioned my disk from the WinXP installation CD during the WinXP install (100MB Dell Utility partition, 3 x 20GB partitions for Windows and data, a 9GB chunk of contiguous free space for Hardy, a spare 9GB partition)
2) Installed Hardy into the largest contiguous free space.
3) Booted from the WinXP installation CD again, as far as the partitioner and deleted the 9GB partition (it's now contiguous free space for installing Karmic) before quitting to avoid reinstalling WinXP again. Rebooting went straight to Windows (no grub).
4) Installed Karmic into the largest free space. Sytem now goes into Grub2 and allows me to select Karmic, WinXP or Hardy.

Sometimes ignorance is bliss!

---

### Post by InspironDualBoot on 2010-03-04
I've learnt my first lesson - keep posts short and to the point!

Queries answered in new threads here [http://ubuntuforums.org/showthread.php?t=1420524](http://ubuntuforums.org/showthread.php?t=1420524) and here [http://ubuntuforums.org/showthread.php?p=8918408](http://ubuntuforums.org/showthread.php?p=8918408)

---

