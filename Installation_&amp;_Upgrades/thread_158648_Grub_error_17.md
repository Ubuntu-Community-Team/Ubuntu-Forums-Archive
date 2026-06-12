---
title: "Grub error 17"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by khegel on 2006-04-11
After installing ubuntu and rebooting, Grub error 17 comes up. I have a dual boot system with Windows on hda (hd0 the master drive) and ubunu on hdb2 (the second partition on the second slave harddrive which is the second partition after a ntfs partition) So basically windows is on my first drive then on my second drive is a windows partition then ubuntu. I have my bios set to user which seems to work fine. I have tried everything described in the forums and searched everywhere and after three days of troubleshooting I have not come to a solution. Here is my fdisk -l

Disk /dev/hda: 15.3 GB, 15307407360 bytes
255 heads, 63 sectors/track, 1861 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1861    14948451    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       22733   182602791    7  HPFS/NTFS
/dev/hdb2   *       22734       24252    12201367+  83  Linux
/dev/hdb3           24253       24321      554242+   5  Extended
/dev/hdb5           24253       24321      554211   82  Linux swap / Solaris

If you need any more information in order to assist me than I will be happy to provide it. Thanks!

---

### Post by GrootBrak on 2006-04-11
I am experiencing almost the same problem, the difference is I had a good working system, them since yesterday, I get the following screen when booting.

> Grub loading, please wait...
Error 17

That's it nothing more. It don't even get to the option of choosing what OS i want to run. For the fun, I re-installed the whole shebang, formatted all partitions and made a fresh install. Still the same thing, the setup stopped right there where you have to remove the CD and the PC reboots.

I have three disks, one for WinXP, One for Linux boot and the third is split between Windows and Linux. 

So far all my Google and this forum searches have yielded nothing.
I hope I can get some help!!!

---

### Post by OMRebel on 2006-04-11
I don't know if this will help you guys or not:

[http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5)

---

### Post by khegel on 2006-04-11
I have viewed the gentoo forums regarding this issue, however, they have not given me any information to help me resolve my issue. Thanks anyway for the link though.

---

### Post by GrootBrak on 2006-04-12
Thanx, been through the link myself. Does not work. For all practical purposes I am doing a new install. The only disk I am not formatting is the one with my windows on it. Even though I format all partitions, I still get the same error. I checked if one of my disks failed, but that is not the case.

---

### Post by piejay on 2006-04-12
Where did you put grub?
I have the same, it only boots when the cd is in (cd first in BIOS) and I choose the option "start from first disk".
Then grub starts and I can choose ubuntu or windows.

......
pj

---

### Post by khegel on 2006-04-12
Grub is on hd0 the windows drive on the first disk. I have not tried to do a boot with the cd but I would prefer to get grub working without it.

---

### Post by petri on 2006-04-13
You might need reinstall grub. [Here]("http://ubuntuforums.org/showthread.php?t=76652&highlight=howto+install+grub") you will find a howto do it.

And [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors") you will find what those error codes really want to say...

---

### Post by khegel on 2006-04-13
I have already tried the steps outlined in the post for reinstalling grub. I think that the problem is with the installation of grub so reinstalling grub would just put back what didn't work in the first place. The problem is with grub recognizing the fact that the boot partition is on one disk while the root partition is on another disk (on the second partition). Before I had a windows partition preceding the ubuntu root partition, ubuntu worked fine. The problem now is that there is a windows partition before the ubuntu partition. I tried to install grub with root(hd1,2) and various combinations of that but none have worked. Any help in resolving this issue would be greatly appreciated.

---

### Post by GrootBrak on 2006-04-14
Thanx, still no help. I have made sure to format my disks, then setup partitions. Installed Breezy and now I get error 22. While partitioning, I get no funny/suspicious problems. The worst is that I had a perfectly working working dual boot system. Now its all gone. I can't seem to get WinXP back either. My hard disks report no errors anywhere. I have a Hirense rescue disk, but even with its help, I cannot get my system back. I am trying to boot WinXP only at the moment. For some reason or other, I am unable to setup XP fresh, unless I first install WinME and then upgrade to XP, and believe me that is a ROYAL PIA cause I loose every last bit of what I had! (The friendly goons at MS don't know why I cannot install XP on a fresh system either!)

---

### Post by petri on 2006-04-14
GrootBrak, ...
Sorry, now I see that you have reinstalled Ubuntu. :rolleyes: 

khegel, I really don't know if the partition thingy has something to do with your problem. It should be in the grub manual (my previous post) if your partition is nono thing to do.

You two could post your menu.lst and a complete fdisk -l 

Maybe somebody can tell you when they see those files whats the problem. I my self have had some fights with errors 17 and 22 :D and it's quite annoying when nobody answers.

---

### Post by khegel on 2006-04-14
I have my fdisk -l output on my first post but how do you find the menu thing?

---

### Post by petri on 2006-04-14
Yes of course you have :rolleyes: 

The grub menu, type in terminal

```
sudo  gedit /boot/grub/menu.lst
```

copy and paste it here. Close gedit and don't save changes if it asks :mrgreen:

---

### Post by khegel on 2006-04-14
The grub menu doesn't come up but can I do this from a live cd?

---

### Post by petri on 2006-04-14
Thats difficult to me to explain because I don't master the CLI [-( 
but I'll try the GUI:

On the top of the screen choose menu: System >> Administration >> Disks

There you find your harddisk (you have only one?) and mount the partition there you have linux (or just mount them all) in Access path >> Change and choose mnt folder >> create folder *linux* and on the line Status >> Activate and then click button Browse.

If you mounted the right partition you will see folder *boot* doubleclick on it and choose *grub* there you will see you *menu.lst*

Because you are using LIVE cd you already have **root** permissions...

Text above doesn't look nice [-(  maybe I do have to learn CLI :)

---

