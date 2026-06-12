---
title: "configuration for multi OS mulit HD"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by scojopa on 2015-02-28
I am running ubuntu on my master hard drive. I have a second hard drive that I just installed another linux OS. I screwed up and let the second install write to the MBR. Now I cannot boot into my original OS with all my data. 

Can someone please help point my in the right direction to resolve this. I am booting into the second system now - and if I manually select the HD that has the original ubuntu system, It does not boot. 

Thank you very much for any help. 

SP

---

### Post by oldfred on 2015-02-28
Best to see details. Do not run autofix, that installs one grub to all drives. And with two drives & two installs you want each boot loader in the same drive as install, so you could choose from BIOS which to boot. But grub should give you choice.
What brand/model system & what video card? Or what motherboard?

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
Normally you should be able to just boot into first install and from that install grub to MBR. There should not normally be any reason why installing to another drive would create issues with another install on different drive except if you let it overwrite MBR with grub boot loader.

---

### Post by scojopa on 2015-02-28
I did let it overwrite MBR w/ grub boot loader - during the install of the second OS on the second drive. So right now the machine will auto boot to /sdb but if I manually select the original drive to boot - it does not load the OS just blinking cursor. 

So I want "each boot loader in the same drive as install"   I already tried boot repair but the original drive is encrypted to it wanted to decrypt it first and I didnt proceed. 

Isnt there a way I can just re-run a live install on and fix the MBR on the original drive? Without redoing the install?

Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00022b94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1000214527   499856385    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1000214527   499856384   83  Linux

Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006939f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758   500117503   249807873    5  Extended
/dev/sdb5          501760   500117503   249807872   8e  Linux LVM

---

### Post by grahammechanical on 2015-02-28
I had a similar problem when I installed Windows 8 preview on to a second hard drive. Windows wrote its boot loader into the MBR of both drives. My solution was to

1) Load the Ubuntu live session.
2) Use the file manager to open the Ubuntu drive. Is that sda in your case?
3) Open the terminal and run these two commands

```
update-grub
grub-install /dev/sda
```

I do not think that a live session will need sudo prefixed to those commands and I am assuming that the Ubuntu drive is sda. In my case the Ubuntu drive was sdb. So, in my case the second command was

```
grub-install /dev/sdb
```

regards.

---

### Post by oldfred on 2015-02-28
Do not know why from second install's grub you cannot boot first install. 
Have you tried, just to see if it updates boot?
sudo update-grub

Are similar versions of grub2 with both installs?
If using Boot-Repair or from live installer you must mount /boot & / (root), so you would have to un-encrypt / to have install of grub work.

Advanced mode of Boot-Repair should let you choose first install and choose sda as where to install grub. But then if you do not install the second install's grub to sdb, it may not boot from first install. Again you would need to mount encrypted partition and run sudo update-grub from first install for it reinstall. You may just be able to copy boot stanza from grub in second install to first install as an alternative.

---

