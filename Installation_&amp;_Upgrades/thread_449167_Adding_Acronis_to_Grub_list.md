---
title: "Adding Acronis to Grub list"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by tormentum on 2007-05-20
Hi Guys and Girls,

I'm wondering if anyone has tried adding the files from the Acronis True Image CD to a partition and managed to boot it from the Grub list?

I found this: [http://bbs.wuyou.com/viewthread.php?tid=33903](http://bbs.wuyou.com/viewthread.php?tid=33903) which looks like it may work, but it's all Chinese to me unfortunately.  If I don't get any comments I'll probably just try creating a new partition and seeing what happens, but I'm curious to see if anyone else has tried this and what degrees of success they have had.

Essentially I want to get away from needing the Acronis CD to restore images.  I want to be able to boot it from Grub.  Cheers!

---

### Post by tormentum on 2007-05-20
Well, I did a bit more reading and found i could place acronis either in the /boot folder or in a partition of it's own.  Then add an entry to the Grub menu.lst file and hey presto, it booted no problem.

[B]HOWTO: Boot Acronis TrueImage Home v10 without a CD
[/B]This HowTo will show you how to do away with your Acronis bootable CD that you use to create backup images of different partitions on your system.  If you're anything like me, you kill your Windows and Ubuntu partitions regularly, and hence have "perfect installation" images that you can throw back on whenever needed.  Acronis TrueImage allows you to image your system quickly and easily and _usually_ boots straight off a bootable CD.  What if you dont want to have to carry an Acronis disk everywhere you go?  Solution:  copy the files off the CD and boot them using Grub.  Acronis is essentially a linux distribution in its own right, so Grub boots it gracefully.  Here's how:

**Step 1: Extract the Acronis files from the bootable CD**
As root (sudo -s) do the following:
```
mount /media/cdrom 
mkdir /boot/acronis
cp /media/cdrom/Recovery\ Manager/* /boot/acronis
umount /media/cdrom
```This will copy all the files off the Acronis bootable CD to a new folder "/boot/acronis"

**Step 2: Extract the initrd file:**
Acronis compresses the *initrd* file to *ramdisk.dat*, so we'll extract it:
```
gunzip -c ramdisk.dat > initrd
rm ramdisk.dat
```You should now have a list of files as follows:
```
-rw-r--r-- 1 1.8M 2007-05-20 02:07 bootmenu.exe
-rw-r--r-- 1  22K 2007-05-20 02:07 bootwiz.sys
-rw-r--r-- 1  268 2007-05-20 02:07 f11.cfg
-rw-r--r-- 1  29M 2007-05-20 14:44 initrd
-rw-r--r-- 1 659K 2007-05-20 02:07 kernel.dat
-rw-r--r-- 1 4.8K 2007-05-20 02:07 mouse.com
-rw-r--r-- 1  23K 2007-05-20 02:07 splash.run
```I'm fairly certain you dont need all the files, but for simplicity we'll copy them all.

**Step 3: Edit the Grub menu.lst file:**
The next step is to add an entry to the end of the */boot/grub/menu.lst* file:

```
#Acronis Grub menu.lst entry
title    Acronis Home v10.0
root    (hd0,0)
kernel    (hd0,0)/boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000
initrd    (hd0,0)/boot/acronis/initrd
```Note: you will need to change the (hd0,0) to reflect the hard disk and partition that you are booting acronis from.

**Step 4: Restart and check your Grub menu**
Nuff said.

I'll put together a proper howto on one of the HowTo forums.

Any questions, message me or post here :)

---

### Post by tormentum on 2007-05-20
Upon closer inspection and futher "tweaking" I've found that the only two files you need from the CD are the two mentioned in Grub's menu.lst file.  Namely:
```
-rw-r--r-- 1  29M 2007-05-20 14:44 initrd (or ramdisk.dat from the cd)
-rw-r--r-- 1 659K 2007-05-20 02:07 kernel.dat
```

Works a charm

---

### Post by weedenbc on 2007-05-21
I extracted the files from the Acronis Recovery cd to /boot/acronis just fine.  But when I type 

```
gunzip -c ramdisk.dat > initrd
```

from the /boot/acronis dir I get

```
bash: initrd: Permission denied
```

So I tried running

```
sudo gunzip -c ramdisk.dat > initrd

```

and I got the same error message.  Am I missing something?  I didn't think there was anything sudo couldn't do.

---

### Post by tormentum on 2007-05-22
Make sure you're running the command on the files in the /boot/acronis directory, and not the ones on the CD.  The only reason I can think of that you would get "Permission Denied" as root is if you're trying to run the command on the mounted CD, which is of course read only.

---

### Post by munkyeetr on 2007-05-23
I am having the same problem trying to gunzip the ramdisk.dat file. I am in /boot/acronis and I have the CD ejected.

```

jon@papa-penguin:/boot/acronis$ sudo gunzip -c ramdisk.dat > initrd
bash: initrd: Permission denied

```

Anyone have any ideas of why this would be?

---

### Post by munkyeetr on 2007-05-23
Got it!

Move the ramdisk.dat file to another directory, extract it, and move it back.

```

sudo mv ramdisk.dat /media/storage/TEMP
cd /media/storage/TEMP
sudo gunzip -c ramdisk.dat > initrd
sudo mv initrd /boot/acronis

```

I don't know why it doesn't work in the /boot/acronis directory, but it may have something to do with the fact that I mount my /boot directory on it's own partition? No idea, but the above worked to get it extracted.

---

### Post by wdster on 2007-05-23
Worked like a charm, Thanks. 

I removed the (hd0,0) from both these lines in grub.
kernel and initrd
Hence:

Code:
#Acronis Grub menu.lst entry
title    Acronis Home v10.0
root    (hd0,0)
kernel             /boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000
initrd              /boot/acronis/initrd

---

### Post by tormentum on 2007-05-24
Good to know munkyeetr, i tried it again on my machine and it worked fine, so I'm not too sure why you guys were having problems.  The only thing i can think of is that with /boot being in its own partition, you ran out of space on there?  What does *"df -h"* tell you about the amount of free space on that partition?

Also thanks wdster for your input.  I'm gonna try that tonight when I get home and i'll update the HOWTO with these bits and pieces :)

---

### Post by Quatrix on 2008-06-15
Thanks for saving me from having to insert the CD every time, but I'm having some trouble.  I have both True Image 11 and Disk Director 10 on one disc.  When I boot from that CD, I get an "Acronis Rescue Media" menu with TI, DD, and a few other options.  When I followed your procedure, however, it boots straight into True Image.  My CD has only one folder "Recovery Manager" with the same set of files that you mentioned, so I'm guessing there's some switch I need to put in menu.lst to load the Rescue Media menu instead of TI.  Any ideas?

```

-r-xr-xr-x 1 root root  2276233 2008-06-15 16:18 bootmenu.exe
-r-xr-xr-x 1 root root    22528 2008-06-15 16:18 bootwiz.sys
-r-xr-xr-x 1 root root      268 2008-06-15 16:18 f11.cfg
-rw-r--r-- 1 root root 40964608 2008-06-15 16:19 initrd
-r-xr-xr-x 1 root root   945778 2008-06-15 16:18 kernel.dat
-r-xr-xr-x 1 root root     4850 2008-06-15 16:18 mouse.com
-r-xr-xr-x 1 root root    29465 2008-06-15 16:18 splash.run
```

---

### Post by Quatrix on 2008-06-24
Okay, I was able to set up Disk Director as a separate entry in Grub.  My stand-alone DD boot CD (as opposed to the one I mentioned earlier that has both DD and TI together) has no files visible on it; apparently it boots in a different way than True Image.  However, I found kernel.dat and ramdisk.dat in Program Files\Acronis\DiskDirector and followed the same process as with TI.

---

### Post by hamamelis on 2008-07-04
Here's my solution to boot either Acronis True Image or Disk Director from grub. /boot/grub/menu.lst contains

#Acronis Grub menu.lst entry kernel.dat & ramdisk.dat from boot CD
title    Acronis Home True Image v10.0 
root    (hd0,7)
kernel    (hd0,7)/boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000 acpi=off noapic
initrd    (hd0,7)/boot/acronis/ramdisk.dat 

#Acronis Grub menu.lst entry kernel.dat & ramdisk.dat from /media/WinXP/Program Files/Acronis/Disk Director
title    Acronis Home Disk Director v10.0
root    (hd0,7)
kernel    (hd0,7)/boot/acronisDD/kernel.dat quiet vga=788 ramdisk_size=40000 acpi=off noapic
initrd    (hd0,7)/boot/acronisDD/ramdisk.dat 

This is Ubuntu Hardy. Grub can read ramdisk.dat without gunzip.
acpi=off noapic is needed by my Acer Travelmate 3004.

---

