---
title: "Dual Booting XP and Ubuntu on 2 drives [XP as master -- SATA and IDE I think]"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by ridsicle on 2008-09-09
Hey guys I took a brief look around the forums and I couldn't find anything relating to my problem. So I thought I'd make this post to get some help :KS

Anyways, to the point:
I've recently decided I want to configure my installation of XP to dual boot along side Ubuntu. I'm only 14 so as you can probably guess, I've never done this before. I am however able to understand the computer tech language quite well since it's a skill that runs through the family, so you don't need to talk "Nub" language to me.

I want to make it so that I can boot into XP from my master and have Ubuntu on my slave. [I have 2 HDs]

I went ahead and booted into the Ubuntu installer and I got as far as the partition, I didn't understand how to configure the partitioner to install Ubuntu on to my 2nd HD, Leaving my primary XP HD untouched.

Thanks in advance to all who help! :)

Regards,
-Dale.

---

### Post by confused57 on 2008-09-09
It would actually be easier to install grub to the Ubuntu drive's mbr & boot Windows from grub...here's how I have a couple of my computers set up:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
The above method involves switching the Ubuntu drive to master and the Windows drive as slave...the method below, you would leave Windows as master & Ubuntu as slave, if your bios can boot first to the slave drive.

You shouldn't have to disconnect any drives, if your bios is capable of being set to boot first to your slave drive.  If it is, set the bios to boot first to the slave drive, before you boot up with the live cd to install Ubuntu.  Your Windows drive should be designated as /dev/sda and the slave drive as /dev/sdb...what you would want to do to ensure grub's IPL(Initial Program Loader) is installed to the slave drive's mbr is to click on the "Advanced" button in the lower right near the end of the install process.  Change the default (hd0) to /dev/sdb, or however your slave drive is designated.

Added:  Before you start trying to install, you might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

This will show how your 2 drives are designated.

---

### Post by ridsicle on 2008-09-10
Thanks for your help confused57

It helped a lot:)

---

### Post by confused57 on 2008-09-10
> **ridsicle said:**
> Thanks for your help confused57

It helped a lot:)
Glad to help, hope you were able to successfully install Ubuntu or wish you luck if you haven't already.

One thing to keep in mind is that it seems when there is a mix of SATA & IDE drives, the Ubuntu installer seems to install grub's IPL to the mbr of the IDE drive, regardless of which drive you installed Ubuntu on.  The results of "sudo fdisk -l", as well as the partitioner on the install cd, should show you which drive is the one you're installing Ubuntu to, e.g. /dev/sda or /dev/sdb.

Once you determine which is the Ubuntu drive, clicking on the "Advanced" button and installing to /dev/sda or /dev/sdb, depending on your Ubuntu drive, should ensure that grub gets installed to the correct drive's mbr.  This way, your Window's drive will not be affected in any way by the installation of Ubuntu.  Even if grub's IPL is accidentally installed to the mbr of the Window's drive, there are several methods to restore Windows IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
In fact, you might want to burn a copy of Super Grub Disk to have if you have booting problems.

---

### Post by ridsicle on 2008-09-14
> **confused57 said:**
> Glad to help, hope you were able to successfully install Ubuntu or wish you luck if you haven't already.

One thing to keep in mind is that it seems when there is a mix of SATA & IDE drives, the Ubuntu installer seems to install grub's IPL to the mbr of the IDE drive, regardless of which drive you installed Ubuntu on.  The results of "sudo fdisk -l", as well as the partitioner on the install cd, should show you which drive is the one you're installing Ubuntu to, e.g. /dev/sda or /dev/sdb.

Once you determine which is the Ubuntu drive, clicking on the "Advanced" button and installing to /dev/sda or /dev/sdb, depending on your Ubuntu drive, should ensure that grub gets installed to the correct drive's mbr.  This way, your Window's drive will not be affected in any way by the installation of Ubuntu.  Even if grub's IPL is accidentally installed to the mbr of the Window's drive, there are several methods to restore Windows IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
In fact, you might want to burn a copy of Super Grub Disk to have if you have booting problems.

I tried to make sense of this and came to no avail, the previous reply you put made it sound fairly simple, this shows to me it isn't.

So...I did however decide to use the "Install in windows" option. This apparently worked fine but it turns out it didn't.

Here's what happened:
Now when I boot my PC I get the boot loader come up fine, but when I select "Ubuntu" it takes me to something called the "GRUB4DOS".

---

### Post by caljohnsmith on 2008-09-14
EDIT: Sorry, didn't see that confused57 outlined the same method as what I was going to propose. I would follow that if I were you ridsicle.

---

### Post by Pumalite on 2008-09-14
confused57 thread is the best there is in my opinion.

---

### Post by confused57 on 2008-09-15
> **ridsicle said:**
> I tried to make sense of this and came to no avail, the previous reply you put made it sound fairly simple, this shows to me it isn't.

So...I did however decide to use the "Install in windows" option. This apparently worked fine but it turns out it didn't.

Here's what happened:
Now when I boot my PC I get the boot loader come up fine, but when I select "Ubuntu" it takes me to something called the "GRUB4DOS".
I've never used the Wubi installer, but you might want to start a new thread in the Wubi section of the forum describing your problem.

If you still want to try setting up a dual boot with Ubuntu "installed" on a separate hard drive from Windows, you really need to post the output of "sudo fdisk -l" and which drive you want to install Ubuntu to.  This way someone could give you more specific instructions on how to go about installing Ubuntu.
It is relatively simple, and if you install grub's IPL to the mbr of your Ubuntu drive, your Window's drive won't be affected in any way...regardless of whether you have a mix of SATA + IDE.

---

### Post by ridsicle on 2008-09-15
> **confused57 said:**
> I've never used the Wubi installer, but you might want to start a new thread in the Wubi section of the forum describing your problem.

If you still want to try setting up a dual boot with Ubuntu "installed" on a separate hard drive from Windows, you really need to post the output of "sudo fdisk -l" and which drive you want to install Ubuntu to.  This way someone could give you more specific instructions on how to go about installing Ubuntu.
It is relatively simple, and if you install grub's IPL to the mbr of your Ubuntu drive, your Window's drive won't be affected in any way...regardless of whether you have a mix of SATA + IDE.

sudo fdisk -l OUTPUT:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x03c900eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20673   156287848+   7  HPFS/NTFS

```

I want to install it to my second HDD[It's my slave drive right now]

---

### Post by caljohnsmith on 2008-09-15
First, make sure you know which is your slave drive; it is most likely /dev/sdb, or your 160 GB drive. If it is instead your 120 GB drive, then obviously it would be /dev/sda. When you get to the part in the Ubuntu installer where you can choose your HDD, just choose the correct HDD (sda or sdb), and partition it for Ubuntu. You'll need one partition for the main Ubuntu install and one partition for swap space.

By the way, your sda drive looks a little screwy. sda3 is a zero length partition for one thing. I would recommend running testdisk on it just to make sure it's partition table isn't completely messed up. If you need details let me know.

---

### Post by ridsicle on 2008-09-15
> **caljohnsmith said:**
> First, make sure you know which is your slave drive; it is most likely /dev/sdb, or your 160 GB drive. If it is instead your 120 GB drive, then obviously it would be /dev/sda. When you get to the part in the Ubuntu installer where you can choose your HDD, just choose the correct HDD (sda or sdb), and partition it for Ubuntu. You'll need one partition for the main Ubuntu install and one partition for swap space.

That's the part that came to confuse me bud.

I want it on my 120 GB drive but it's being marked as /dev/sda when I thought that'd work out to be my master drive[My 160 GB]

I don't want to wipe my 160 GB as it holds my windows OS plus all my programs, music etc...


> **caljohnsmith said:**
> By the way, your sda drive looks a little screwy. sda3 is a zero length partition for one thing. I would recommend running testdisk on it just to make sure it's partition table isn't completely messed up. If you need details let me know.
How do I go about doing this?, I don't even know how it's happened TBH.

---

### Post by caljohnsmith on 2008-09-15
I don't think it should be a problem that your slave drive is sda instead of sdb. I'm glad you are going to use sda, because then you can completely wipe it clean and start fresh before installing Ubuntu; so no need to worry about using testdisk. When you use the Ubuntu installer, just tell it to "use the whole disk" and choose sda. I think it should be mostly self-explanatory, but if you run into problems or have questions, let us know.

---

### Post by ridsicle on 2008-09-15
> **caljohnsmith said:**
> I don't think it should be a problem that your slave drive is sda instead of sdb. I'm glad you are going to use sda, because then you can completely wipe it clean and start fresh before installing Ubuntu; so no need to worry about using testdisk. When you use the Ubuntu installer, just tell it to "use the whole disk" and choose sda. I think it should be mostly self-explanatory, but if you run into problems or have questions, let us know.

I show my increased gratitude to you and confused57 for helping me!

I will happily give this a shot and see what happens :)

---

### Post by ridsicle on 2008-09-15
I just tried this method and it got a lot further than my attempt with WUBI.

However when I select Ubuntu and try to boot into it, it cant find some file and then ceases to boot[I already try recovery mode and I get the same error]

The file name is pretty long so I don't remember what it was.

---

### Post by caljohnsmith on 2008-09-15
> **ridsicle said:**
> I just tried this method and it got a lot further than my attempt with WUBI.

However when I select Ubuntu and try to boot into it, it cant find some file and then ceases to boot[I already try recovery mode and I get the same error]

The file name is pretty long so I don't remember what it was.
So you restart your computer, you get a Grub menu, you select Ubuntu, but then Ubuntu complains it can't find some file? If you can write down the name of the file and let us know that would probably help, as well as any other details of what happens.

---

### Post by ridsicle on 2008-09-15
> **caljohnsmith said:**
> So you restart your computer, you get a Grub menu, you select Ubuntu, but then Ubuntu complains it can't find some file? If you can write down the name of the file and let us know that would probably help, as well as any other details of what happens.

I viewed somebody else's post and the name had quite a big resemblance of the kernel file name.

---

### Post by ridsicle on 2008-09-15
I gave it another shot to get the file name here's what I got for you:

"kernel /boot/vmlinuz-2.6.24-generic root=UUID=9a95f81b-641d-42a3-9c53-baff3 7090692 ro quiet splash"

---

### Post by caljohnsmith on 2008-09-15
OK, so please describe exactly what happens on start up: do you get the Grub menu, select one of the entries for Ubuntu, and then what? Does Grub return an error number, like error 15? And that's when Grub complains it can't find that kernel file?

---

### Post by Pumalite on 2008-09-15
Post:
blkid

---

### Post by ridsicle on 2008-09-16
> **caljohnsmith said:**
> OK, so please describe exactly what happens on start up: do you get the Grub menu, select one of the entries for Ubuntu, and then what? Does Grub return an error number, like error 15? And that's when Grub complains it can't find that kernel file?

What you just described their is absolutely right.

---

### Post by ridsicle on 2008-09-16
> **Pumalite said:**
> Post:
blkid

This means...?

---

### Post by Pumalite on 2008-09-16
Compare your UUID's:
blkid against /etc/fstab against /boot/grub/menu.lst

---

### Post by ridsicle on 2008-09-16
> **Pumalite said:**
> Compare your UUID's:
blkid against /etc/fstab against /boot/grub/menu.lst

How do I actually go about doing this?

And if they don't match what do I do then?

---

### Post by caljohnsmith on 2008-09-16
Like Pumalite says, you'll need to check your UUIDs since Grub is complaining about the kernel missing. Boot your Live CD, and do the following from a terminal:
```
sudo blkid
sudo fdisk -lu
```
Post the results of the above, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
Please post the results.

---

### Post by ridsicle on 2008-09-16
> **caljohnsmith said:**
> Like Pumalite says, you'll need to check your UUIDs since Grub is complaining about the kernel missing. Boot your Live CD, and do the following from a terminal:
```
sudo blkid
sudo fdisk -lu
```
Post the results of the above, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
Please post the results.

I'm accessing this forum from school right now but when I get back home I will do this and post all the results as you requested.

I know we havn't fixed it yet but thanks to you all who have helped me so far, if it wasn't for you guys I would've just given up.:lolflag:

---

### Post by ridsicle on 2008-09-16
sudo blkid:
```

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="9a95f81b-641d-42a3-9c53-baff37090692" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a48a64c0-423f-47bd-a317-92eaa35a5207" TYPE="swap" 
/dev/sdb1: UUID="8068BC9468BC8B04" LABEL="Dale's HDD" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

```




sudo fdisk -lu:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4de6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   228444299   114222118+  83  Linux
/dev/sda2       228444300   234484739     3020220    5  Extended
/dev/sda5       228444363   234484739     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03c900eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312575759   156287848+   7  HPFS/NTFS

```




sudo mount /dev/sdXY /mnt

ls -l /mnt/boot

cat /mnt/boot/grub/menu.lst:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 11088
-rw-r--r-- 1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x 2 root ubuntu    4096 2008-09-15 23:38 grub
-rw-r--r-- 1 root ubuntu 7874524 2008-09-15 23:37 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9a95f81b-641d-42a3-9c53-baff37090692 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9a95f81b-641d-42a3-9c53-baff37090692 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9a95f81b-641d-42a3-9c53-baff37090692 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

As requested.

---

### Post by caljohnsmith on 2008-09-16
Your UUIDs and the kernel/initrd files used in your menu.lst look fine from what I can see. Maybe you are booting off your sdb drive, instead of the sda drive. How about rebooting, and when you get the Grub menu, select Ubuntu, press "e" to edit it, select the line that says "root (hd0,0)", and then change it to "root (hd1,0)", press return to save the change, and then press "b" to boot. Let me know if that works or what errors you get.

---

### Post by ridsicle on 2008-09-16
> **caljohnsmith said:**
> Your UUIDs and the kernel/initrd files used in your menu.lst look fine from what I can see. Maybe you are booting off your sdb drive, instead of the sda drive. How about rebooting, and when you get the Grub menu, select Ubuntu, press "e" to edit it, select the line that says "root (hd0,0)", and then change it to "root (hd1,0)", press return to save the change, and then press "b" to boot. Let me know if that works or what errors you get.

Indeed this was the cause. 

Big thanks to all especially you caljohnsmith!

---

### Post by caljohnsmith on 2008-09-16
> **ridsicle said:**
> Indeed this was the cause. 

Big thanks to all especially you caljohnsmith!
You're welcome, and I'm glad you can at least boot into Ubuntu now. In case you haven't done it all ready, to make that change permanent, you'll need to modify your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then change all the "root (hd0,0)" Ubuntu entries to use (hd1,0). Also, to boot Windows, you'll then need to change its entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Then I think you'll finally have access to both Ubuntu and Windows. Or if not, you know where to find us. :)

---

