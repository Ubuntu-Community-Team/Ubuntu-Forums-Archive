---
title: "Not Again"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Barryr on 2008-04-04
Hea All
 
I have been mad to starting using Linux for a long time but also needed windows, so I decided to try Dual boot again on my new xps laptop,(the last time I tried I deleted the windows partition..) This time around I thought I did everything correctly following all the right instructions, I got Ubuntu installed and it works fine but I am unable to access Vista now, I have given Ubuntu 3gb of space or there abouts and thats what shows up in the file system so surely I have not erased the windows partition.

When installing in the first place I selected the use free space option.

Very confused is windows gone and an ideas how to get back into vista, is it something to do with grub...very new to Linux so take it easy on me.

Thanks in advance

---

### Post by Pumalite on 2008-04-04
Post:
sudo fdisk -lu
If Windows exists, you can boot it or fix its MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
I can also help you add your Windows to your menu.lst.

---

### Post by mikewhatever on 2008-04-04
Can you post the outputs of <sudo fdisk -l> and <cat /boot/grub/menu.lst>.

---

### Post by Barryr on 2008-04-04
Ya here it is:  


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29645   238123431   83  Linux
/dev/sda2           29646       29909     2120580    5  Extended
/dev/sda3   *       29910       30401     3951990   83  Linux
/dev/sda5           29646       29879     1879573+  82  Linux swap / Solaris
/dev/sda6           29880       29909      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x487359d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
barry@barry-laptop:~$

---

### Post by Pumalite on 2008-04-04
Unless it is in sdb1, there is no Windows. What do you have in your second hard drive?

---

### Post by Catalyst2Death on 2008-04-04
There are no non-linux file systems in your output.. It looks like ubuntu took the whole hard drive... In the future, manually format you hard drive  this way you have complete control over where ubuntu installs itself.

this is a good guide on how to partition the harddrive:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Barryr on 2008-04-04
Only one drive, when I got the laptop there was a recovery partition that was around 5gb in size! I'm sure that I did not delete it, like I said above in windows I did the shrink volume and made some free space to put Ubuntu on, hope its not gone!

---

### Post by Pumalite on 2008-04-04
If there is a Windows to boot, Super Grub will do it, but it seems it's gone.

---

### Post by mikewhatever on 2008-04-04
Not sure what happened, but you seem to have done the installation twice. There are two swap partitions and two other Linux ones, probably roots. One way or the other, somewhere in the process, your Vista partition got deleted. Sorry.:(

---

### Post by Barryr on 2008-04-04
Well that really sucks :( thanks for the help anyway

---

