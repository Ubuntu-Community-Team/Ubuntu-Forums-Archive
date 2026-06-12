---
title: "Ubuntu 6.10 installation hangs on partioning"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by jalov on 2007-03-11
Hello everybody,

I've been trying to install Ubuntu 6.10 on a new hd. It's a Hitachi Deskstar 160 GB SATAII.
Windows XP is on another hd. I'm hoping to set up a dual boot.

I'm using ubuntu-6.10-desktop-i386.iso.

I chose the option "erase entire disk". The progress bar then gets stuck at 15% with the 
message: "Creating ext3 file system for / in partition # 1 of SCSI1 (0,0,0)...".  I used XP's disk
manager to clear the Hitachi disk, then tried it again and it hung at 11%.

I really don't have a clue what I'm supposed to do next.

Regards,

Jos

AMD Athlon 64 3800+
Asus M2NPV-MX ACPI BIOS Revision 0405
1 GB ram
Hitachi Deskstar T7K250 160 GB SATAII
NVidia Geforce 7600 GS

---

### Post by bulldog on 2007-03-11
Download the GParted live cd,burn it to a cd-r and boot from it. [only 30MB]

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You'll have a graphical interface which is some what easier to use.

Create a root partition ( / ) of about 10GB format as ext3
Create a swap Partition 1GB format as swap
Create a partition for /home [as big as you like] and format ext3
Apply and when done exit GParted live cd and boot from the ubuntu install cd.

When you come to the partitioner,choose manually partition [you've already done this]
Mount your 10GB partition as /   [root] and format as ext3
Mount your swap as swap and format as swap again
Mount the other partition as /home and format as ext3

Now the install should go smooth.

Good luck.

---

### Post by jalov on 2007-03-11
Thanks Bulldog. I did get past the partition dialog this time. 

But now I have the same problem as some other posters: when I boot, I just go to windows. I tried some of the suggestions in the other threads but I get a lot of "does not exist" type of errors.

The only thing I've been able to get to work is this :

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
cd /mnt/ubuntu
ls -al

total 36
drwxr-xr-x 7 root root  4096 2007-03-11 17:44 .
drwxr-xr-x 4 root root    80 2007-03-11 21:53 ..
drwxr-xr-x 2 root root  4096 2007-03-11 17:44 etc
drwxr-xr-x 2 root root  4096 2007-03-11 17:44 home
drwx------ 2 root root 16384 2007-03-11 17:33 lost+found
drwxr-xr-x 2 root root  4096 2007-03-11 17:44 media
drwxr-xr-x 4 root root  4096 2007-03-11 17:44 var

There's no /boot

Maybe the installation failed?

Thanx,

Jos

---

### Post by jalov on 2007-03-11
Some more information:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        1912     5116702+  82  Linux swap / Solaris
/dev/sda3            1913        7275    43078297+  83  Linux
/dev/sda4            7276       20023   102398310   83  Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hdb2            3188       24791   173534130    f  W95 Ext'd (LBA)
/dev/hdb5            3188       15935   102398278+   7  HPFS/NTFS
/dev/hdb6           15936       24791    71135788+   7  HPFS/NTFS

---

### Post by bulldog on 2007-03-12
Your problem isn't that big.
I presume you boot from the hdb disk with windows and you never see the GRUB menu.
So it should be installed on the other sda disk.
Change the boot order in your BIOS,and set the sda disk as the first boot device.
Now you should see the GRUB menu and you can boot into ubuntu,but **not** into windows.
To enable windows to boot,you'll have to change your menu.lst.
So you have to boot into ubuntu and type the next command into a terminal.
```
gksudo gedit /boot/grub/menu.lst
``` and look for your windows entry.

Make it look like this,don't change anything, just add some extra information to it.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)<-----change this
map          (hd0) (hd1)<------ add this line
map          (hd1) (hd0)<----- add this line   
savedefault
makeactive
chainloader	+1

You may also post your menu.lst to the forum so we can have a look at it,if you choose.

---

### Post by jalov on 2007-03-12
I get a black screen with the cursor blinking in the upper left corner.

When I partitioned the disk originally I didn't set the boot flag for sda1, should
I have? I changed it just now, but that doesn't help. (With the boot flag set the
live cd takes forever to scan the devices).

What I intend to do now is clear the disk and redo the entire installation, unless
you have a better idea.

Thanks,

Jos

---

### Post by bulldog on 2007-03-12
Forget about the bootflag.
Try boot ubuntu,but if this isn't possible,boot the live cd and mount your existing install.

I would like to see your menu.lst and your fstab.

---

### Post by bulldog on 2007-03-12
Double post.

---

### Post by jalov on 2007-03-12
The live-cd doesn't seem to be able to see "sda" anymore

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
mount: special device /dev/sda1 does not exist

When I start Gnome partition editor it only brings up "hdb". I'm now
going back to WinXP to see if the disk manager can still see the disk.

---

### Post by jalov on 2007-03-12
Windows doesn't see the disk either anymore. So I'll have to look into that first.

Edit: checked the connectors, but it looks like the disk is dead. That's the second
Hitachi drive I'm going to have to send back. The first one was DOA. 

to be continued...

---

### Post by bulldog on 2007-03-12
Give me a PM when you're ready.

---

