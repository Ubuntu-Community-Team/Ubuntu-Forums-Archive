---
title: "[SOLVED] Error 17"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Bruener on 2008-05-23
Hey, Ive been trying to get this Linux up and running for about two days now, and I cant seem to do it. I tried most of the steps listed for general problem solving and couldnt fix it. Basically I installed Ubuntu on a hard drive in a portable case (160GB) that is connected to my laptop via USB. My internal HD runs XP and I wasnt to play around with Windows. After usingt he CD to install, I had to change my boot order to start from the portable HD to get the GRUB menu. Now when I try to start ubuntu I get an error 17: Cannot mount selected partition. Any advice?

---

### Post by tamoneya on 2008-05-23
put the live CD in again since you need to edit some of the files on the harddrive.  Once you are in the live environment you should mount the drive if it hasnt already been automounted.  Then you need to look at /etc/fstab.  Post the results of the two following commands:```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Bruener on 2008-05-23
The first command gives
ubuntu@ubuntu:~$ sudo fdisk -l
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2787912e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12137    97490421    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007771

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19078   153244003+  83  Linux
/dev/sdb2           19079       19452     3004155    5  Extended
/dev/sdb5           19079       19452     3004123+  82  Linux swap / Solaris

```

The second one does
cat /etc/fstab

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0

```

---

### Post by tamoneya on 2008-05-23
type ```
sudo nano /etc/fstab
```and change it to this:
```
/dev/sdb1 / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

---

### Post by Bruener on 2008-05-23
alright, did that

---

### Post by Bruener on 2008-05-23
Should I try starting now?

---

### Post by meierfra. on 2008-05-23
But that won't solve your problem. A grub error can not be fixed by editing "fstab" (Grub does not even look at "fstab"). Also you did edit the fstab of the Live CD. So  that definitely won't make any difference.


Do this: At the grub menu at boot up, select ubuntu, but to not press "enter". Press "c" instead.
Next press "e" to edit the first line. It should say something like

"root (hd1,3)"  

change the first number to "0", do NOT change the second number:

so "root (hd1,3)" needs to be changed to "(hd0,3)"

Press "enter" and then "esc". This gets you back to the grub menu. You now should be able to boot into ubuntu.


You still have the make these changes permanent:

```
gksudo gedit /boot/grub/menu.lst
```

change "#groot ... " the same way you just changed "root ..."

for example change "#groot (hd1,3)" to "#groot (hd0,3)"

Save the file. Then 

```
sudo update-grub
```

and you should be all set.

---

### Post by Bruener on 2008-05-23
Thankyou!!!!!
It worked!
Now to figure out how to do that 3d cube desktop. Hehe

---

