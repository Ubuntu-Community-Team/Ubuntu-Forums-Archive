---
title: "Grub editing after install"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by Schnippzle on 2007-11-17
Howdy and thank you for letting me on the forum, its a pleasure to be here.

Having used Ubuntu 7.10 in work a fair bit I thought Id install it on my pc at home...which is when I ran into trouble.

I have Vista 64 bit installed on two 36GB raptors in RAID 0  which is controlled by the raid controller on my mobo (Asus P5K) which is ofc FakeRAID.  My Ubuntu installation is on a partition on an 80GB Maxtor SATA drive.

When I rebooted after finishing the installation I get the Error 21 on stage 1.5 of Grub loading and I assume that this is because it cant find one of the two OS's?  I did a bit of reading and found that Grub and Ubuntu do not come with FakeRAID support and I need to dl dmraid in order to get it working.  However, as I can only boot into the Live CD which I used to install Ubuntu, Im in a bit of trouble.  I understand I may need to edit the menu.lst file in the Grub directory on the partition with my Ubuntu installed on it but I really dont know how.  Here is what is in the menu.list file so far:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3471548-27b8-4b97-88cb-c42c5e707898 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3471548-27b8-4b97-88cb-c42c5e707898 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,2)
kernel		/boot/memtest86+.bin
quiet

I would really appreciate it if any one could help me as I need to get my pc up and running to record a live set later on tonight :)

Thank you very much in advance,

Schnippzle.

---

### Post by ajgreeny on 2007-11-17
I know nothing about RAID setups but wonder if you can use the live CD to run ```
sudo fdisk -l
``` in terminal to find what the system thinks the partitions are, then mount the partition (using the disk mounter on the panel which you can add it if necessary) and edit the **/boot/grub/menu.lst** on that partition to coincide with the fdisk output.  If RAID makes this impossible, my apologies for wasting your time, but I thought it worth suggesting.

---

### Post by Schnippzle on 2007-11-17
Without loading the dmraid utility, Ubuntu (Live CD) just sees the two drives as two unknown partitions in partition editor.  Thing is, I get the feeling I need to load dmraid during Grub loading in order to actually allow me to boot into Windows.

---

### Post by Schnippzle on 2007-11-17
Bump :)

---

### Post by confused57 on 2007-11-17
You can try installing grub's IPL to the mbr of the Ubuntu drive, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the instructions in the thread, but you would do something like:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd3,2)", if it does, you would enter:
```
root (hd3,2)
setup (hd3)
quit
```

Then go into your bios setup and make your Ubuntu drive the first hard drive in the boot sequence...boot your computer...you "should" be presented with a grub boot menu.  If you are, make sure the first Ubuntu entry is highlighted(selected), press "e" to edit, select the line with root, press "e" again, change root from (hd3,2) to (hd0,2), press "enter", then "b" to boot.  This change isn't permanent, but hopefully it will enable you to boot into Ubuntu.   It can be made permanent in your /boot/grub/menu.lst.

Before you do the above you might want to restore Window's IPL to the mbr of the first hard drive in your Raid:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Added: Or if you're able to boot into Ubuntu, download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is only a 5-7 Mb download & should be able to boot your Windows or Ubuntu(and reinstall Windows IPL to the mbr).

---

### Post by Schnippzle on 2007-11-17
Cheers for the reply.  Ill give it a try now :)

---

### Post by Schnippzle on 2007-11-17
Tried and tested and now getting an Error 22 when loading grub :( Will try SGD now :)

---

### Post by confused57 on 2007-11-17
> **Schnippzle said:**
> Tried and tested and now getting an Error 22 when loading grub :( Will try SGD now :)
If you have a Vista install DVD(not a recovery disk), you can use the bootrec utility to restore Windows IPL to the mbr:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
You would probably need to set your bios boot order back to how you had it originally.

If you don't have a Vista install DVD, SGD "should" be able to this...I think the option is "Fix Boot of Windows".

Here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Did "find /boot/grub/stage1" return "root (hd3,2)"?

---

### Post by Schnippzle on 2007-11-18
Been working with SGD now since last night and it cant fix my mbr for either my raptor array or my maxtor hdd, even when I use the Windows feature.

I do have a Vista DVD and will try that now :)

---

### Post by Schnippzle on 2007-11-18
Booted off the Vista DVD and used the following commands in the recovery console:

bootrec.exe /fixmbr
bootrec.exe /fixboot

Now Im in Vista and just need to set up the windows boot manager to allow me to boot into Ubuntu as well :)  Cheers for your help.

---

### Post by confused57 on 2007-11-18
> **Schnippzle said:**
> Booted off the Vista DVD and used the following commands in the recovery console:

bootrec.exe /fixmbr
bootrec.exe /fixboot

Now Im in Vista and just need to set up the windows boot manager to allow me to boot into Ubuntu as well :)  Cheers for your help.
Glad you were able to get Vista booting...I should have thought of it before, but EasyBCD may be what you're looking for:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For this to work, grub's IPL needs to be installed to the root partition, rather than the mbr...use the link I gave you earlier:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If "find /boot/grub/stage1" returns "root (hd3,2)", you then would:
```
setup (hd3,2)
```

---

### Post by rzlorayes on 2007-11-18
Hello. 

I installed Ubuntu 7.04 into my computer running Windows XP. I now have the GRUB but other users want to have Windows XP as the default boot choice. How do I go about editing GRUB?

Thanks very much in advance for your help.

Ric

---

### Post by pyrocloud on 2007-11-18
I have never done this for Vista but it should be the same as XP.
Insert this code at the very end of /boot/grub/menu.lst, just before it says END OF DEBIAN AUTOMAGIC KERNELS LIST, to tell grub that you have a RAID in use.

title            Windows
rootnoverify     (hd1,0)
map               (hd0) (hd1)
map               (hd1) (hd0)
makeactive
chainloader +1

While you have menu.lst open to add the RAID to it, look around to make sure the timeout is as long as you want it, and that the secret menu is # out.

You will need to restore GRUB's MBR to the 80GB sata though, as of current there is no great way to let Vista control booting.
you might have to manually edit grub the first time you boot, just make sure that your Ubuntu path is set to (HD0,0)
If there are drivers for your raid you might be able to mount the NTFS partitions. :D

---

### Post by confused57 on 2007-11-18
> **rzlorayes said:**
> Hello. 

I installed Ubuntu 7.04 into my computer running Windows XP. I now have the GRUB but other users want to have Windows XP as the default boot choice. How do I go about editing GRUB?

Thanks very much in advance for your help.

Ric
I personally prefer the first method in this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by Schnippzle on 2007-11-18
> **confused57 said:**
> Glad you were able to get Vista booting...I should have thought of it before, but EasyBCD may be what you're looking for:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For this to work, grub's IPL needs to be installed to the root partition, rather than the mbr...use the link I gave you earlier:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If "find /boot/grub/stage1" returns "root (hd3,2)", you then would:
```
setup (hd3,2)
```

Will give that a go tomorrow after work mate, cheers :)

---

### Post by rzlorayes on 2007-11-19
> **confused57 said:**
> I personally prefer the first method in this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

thanks very much. i'll try that method.:)

---

