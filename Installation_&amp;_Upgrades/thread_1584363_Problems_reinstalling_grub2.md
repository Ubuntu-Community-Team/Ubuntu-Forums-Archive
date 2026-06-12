---
title: "Problems reinstalling grub2"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by themadjester on 2010-09-29
Hello all,

I am having trouble reinstalling grub so That I can see both my linux and windows partitions in the cain loader.

Originally I had ubuntu, then I installed window, this wiped out grub so I had to reinstate it, and that went ok. Then I tried to get fancy and install another Linux on my machine. It did not wipe out my partitions but is defunct

I have been following these instructions,

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

To no success. Grub2 installs fine, 
sudo grub-install --root-directory=/media/(my part ion) /dev/sda2
and I install it to sda2, but the 
"
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
" 
only shows the 1st line, and when I boot grub is there are a grub command prompt but there are no os to load :(
Thanks in advance,
Jester
I have no idea were to go from here except try and try again again again :(

---

### Post by garvinrick4 on 2010-09-29
Find out what partition your Ubuntu is on.
```
sudo fdisk -l 
```(lower case L)
Lets say it is in sda5 for this reference (use what your install is)
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
``` (not a typo)

Boot into Ubuntu Linux install on hard drive and:
```
sudo update-grub
```

Always install grub in sda not sda1 or sda2 or sda5 just sda
Notice in grub-install we tell it to find it in the ubuntu install and put it in sda

---

### Post by themadjester on 2010-09-29
Thanks for the reply garvinrick4 :)

still no love from the chainloader :(

I followed the steps you indicated, I will paste the console so we can be sure I was correct in this:

**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x165c165c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9518    76453303+   7  HPFS/NTFS
/dev/sda2            9519       11123    12885862+  83  Linux
/dev/sda3           11123       12161     8343329+   5  Extended
/dev/sda5           11900       12161     2104483+  82  Linux swap / Solaris
/dev/sda6           11123       11859     5915648   83  Linux
/dev/sda7           11859       11899      321536   82  Linux swap / Solaris

Partition table entries are not in disk order
**ubuntu@ubuntu:~$ sudo mkdir /media/root**
**ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/root**
**ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/media/root /dev/sda**
Installation finished. No error reported.
**ubuntu@ubuntu:~$ sudo umount /media/root**

I ran these and I am brought to the grub boot screen command prompt. grub is version 1.98, there are no os listed to boot into :(

---

### Post by themadjester on 2010-09-29
Hello again :)

good news, I reread the bit in your reply about sda and used the **last** linux partition (for me sda6).

this seems to be essential and did the trick.

for anyone else who is working at this and reading the thread make sure you try that, as gavin says, load the linux partition that shows in grub and then run: sudo update-grub
and boom, works.

I think the wiki page I posted at the top needs some detail added to it(by someone more qualified than myself) to state some of these things. I may be mistaken, however I do not think the explanation is adequate in explaining what is actually happening (as to clue in a user unfamiliar with grub2/grub legacy as to how these commands do their work)

Many thanks.

---

