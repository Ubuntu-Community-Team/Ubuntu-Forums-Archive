---
title: "Grub Error 21"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Dad1985 on 2008-06-12
I am trying to install Ubuntu.  I install it fine, I tell it to put the MBR on the hard rive(not partition) in which I installed the os,  which is dev/sdd.

No matter what I do or how much I change the hard drive parameters I cant get it to work.  grub either says, It cant find or mount the partition.

I can install slackware fine with lilo, but grub from my reading doesnt like my motherboard which is a abit ip-35 pro.  I have also tried the Grub Super disk.


anny help would be appreciated.

---

### Post by meierfra. on 2008-06-12
Do your bios detect your ubuntu drive?

Does the grub menu appear at boot up? (you might have to press "Esc" after the bios screen)

Can you set the bios to boot from the ubuntu drive?

Do you have any kind of raid?

Boot from Supergrub disk. Press "c" at the first menu. Type

```
find /boot/grub/stage2
```

and post the output.

Boot from the Ubuntu Live CD and  post the output of

```
sudo fdisk -l
```
(l is a lower case L)


Go to Computer->Places, double click the icon for the ubuntu partition,  go to /boot and then /boot/grub. This folder contains the file "menu.lst" . Open "menu.lst" and  post it content.

---

### Post by xamlah on 2008-06-12
Hey!

I just installed Ubuntu 8.04 on a USB Hard Drive on my laptop. My internal hard drive has some data and Windows XP on it. I forgot to install GRUB on my internal drive, so now I have to connect my USB drive, everytime I boot, to get GRUB.

Is there any way I can shift grub to my internal HDD?

Thanks!

---

### Post by meierfra. on 2008-06-12
xamlah:  I wrote a HowTo for this situation. Click on "Dual" in my signature.
(Since your are using Hardy, there is a small problem with that HowTo. "ms-sys" is not in the hardy repositories. You need to get the Debian package instead:[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys"), Download the i386 version. Right Click to install)

If you have futher question, please respond  in the "Dual" thread.

---

### Post by xamlah on 2008-06-12
Thanx a lottt!

---

### Post by Dad1985 on 2008-06-12
> **meierfra. said:**
> Do your bios detect your ubuntu drive?

Does the grub menu appear at boot up? (you might have to press "Esc" after the bios screen)

Can you set the bios to boot from the ubuntu drive?

Do you have any kind of raid?

Boot from Supergrub disk. Press "c" at the first menu. Type

```
find /boot/grub/stage2
```

and post the output.

Boot from the Ubuntu Live CD and  post the output of

```
sudo fdisk -l
```
(l is a lower case L)


Go to Computer->Places, double click the icon for the ubuntu partition,  go to /boot and then /boot/grub. This folder contains the file "menu.lst" . Open "menu.lst" and  post it content.




**Does the grub menu appear at boot up? (you might have to press "Esc" after the bios screen) **

yes it does and I get the 3 Ubuntu options
[B]
Can you set the bios to boot from the ubuntu drive?[/B]  Yes, and I have

**Do you have any kind of raid?** Yes, I have raid 0 on my first 2 hard drives on a ICH9R controller.

[B]Boot from Supergrub disk. Press "c" at the first menu. Type

```
find /boot/grub/stage2
```

and post the output.[/B]

(hd2,0)

[B]Boot from the Ubuntu Live CD and  post the output of

```
sudo fdisk -l
```
(l is a lower case L)[/B]

```


Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24532453

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18078   145211503+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00320039

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b4aa3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde48cdfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       23330   187398193+  83  Linux
/dev/sdd2           23331       24321     7960207+   5  Extended
/dev/sdd5           23331       24321     7960176   82  Linux swap / Solaris

```


**Go to Computer->Places, double click the icon for the ubuntu partition,  go to /boot and then /boot/grub. This folder contains the file "menu.lst" . Open "menu.lst" and  post it content.[/QUOTE]**


there is no such file or a folder named grub in  /boot/

---

### Post by meierfra. on 2008-06-12
> Yes, I have raid 0 on my first 2 hard drives on a ICH9R controller.

Your raid is probably causing the problem. I don't know much about raid, accept that it is usually best to install grub to the MBR of the ubuntu drive. Try this


At the grub menu at boot up, press "c". Type

```
find /boot/grub/stage2 
```

This should return "(hd2,0)" (the same as from Supergrub)
Type

```
root (hd2,0)   (use the output from "/boot/grub/stage2)
setup (hd2)         (use the first number of the output)
halt

```

"halt" should turn of the computer, but sometimes you will have to press the power button to  turn it off completely.

Set your bios to boot from the Ubuntu Drive.

At the Grub menu select Ubuntu, but do not press enter. Press "e" instead. At the new screen press "e" again. Change

"root (hd?,0)" to "root (hd0,0)"
(So change the first number to zero, but do not change anything else)

 Press "enter" and then "b" to boot.

If you are lucky this boots you into ubuntu. Once you booted into Ubuntu, you need to make this change permanent:

Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```
(l is a lowercase L)

change

# groot=(hd?,0)

to

# groot=(hd0,0)

Save the file. In the terminal type

> sudo update-grub


**If this did not solve your problem:**

> 
there is no such file or a folder named grub in /boot/ 

Very strange. Try this from the LiveCD


```
mkdir ubuntu
sudo mount -t ext3 /dev/sdd1 ubuntu
ls ubuntu/boot 
```


If the grub folder appears on the list

```
gksudo gedit ubuntu/boot/grub/menu.lst
```

---

