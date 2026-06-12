---
title: "No GRUB after dual WinXP/Ubuntu installation"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by Salk on 2008-09-17
After following carefully the instructions at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), I completed the installation with apparently no issues. However, at reboot, GRUB does not appear and windows XP boots as if nothing has changed. I searched for similar problems, but haven't been able to find anything. Running Ubuntu from the CD appears to work fine. 

Can anyone help me with this problem? I am new to Linux... Thanks!

Salk

---

### Post by caljohnsmith on 2008-09-17
First try the following from your Ubuntu Live CD, in a terminal (Applications > Accessories > Terminal):
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If the above "find" command doesn't return anything, then post the following:
```
sudo fdisk -lu
```
And we can go from there.

---

### Post by Salk on 2008-09-18
Hello, caljohnsmith!

First, thanks for your interest and help.

Now I am gonna relate to you exactly what happens when I apply your solution.

I go to Terminal and write:

```
sudo grub
grub> find /boot/grub/stage1
```

It reports:

```
HD2,4
```

Then I write:

```
grub> root (hd2,4)
grub> setup (hd2)
```

and it reports:

```
Checking if "/boot/grub/stage1" exists ... yes
Checking if "/boot/grub/stage2" exists ... yes
Checking if "/boot/grub/e2fs_stage1_5" exists ... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd2)" ... 16 sectors are embedded. Succeded
Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,4)/boot/grub/stage2 /boot/grub/menu.lst" ... succeded
Done
```

After I quit and reboot the system, Grub finally appears showing also WindowsXP among the other options.

But none works.

I chose first Windows XP and I got the following error message:

```
NTLDR is missing
```

Then I tried starting Ubuntu instead and got the following error message:

```
Error 22: No such partition
```

Needless to say, I didn't do anything hardware or software-wise since the "Quit" command in the terminal and the reboot of the system.

If any more hardware informations might be useful, I'll happily provide them here.

Now I am able to even come here and post just thanks to the Live CD because my Windows system is no longer working. :(

Thanks for your time!

---

### Post by caljohnsmith on 2008-09-18
It's OK, Salk, we're making progress even though you can't boot Windows or Ubuntu yet. Your problem now will most likely be easy to correct, so first do the following from the Live CD:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output of the above commands, and we'll go from there. :)

---

### Post by pbags on 2008-09-18
CalJohnSmith, I am also new to Linux and I was wondering whether you have a suggestion for the following circumstances. I have an AMD Athlon64 computer with 2GB of memory and two identical 250GB hard drives. I installed Ubuntu 8.04 onto drive 1 yesterday, and it worked great. This morning I installed XP(and then SP3) onto drive 0. My intention is to use Ubuntu for most things, but XP for a couple of programs that run only under Windows. When I boot now, of course XP comes up...and it doesn't recognize the second drive at all (which makes sense). Is it possible now to configure this to dual-boot by manipulating the Windows loader or GRUB? or do I have to re-install Ubuntu on drive 1 to make this work? Many thanks for any advice you might have.

---

### Post by caljohnsmith on 2008-09-18
> **pbags said:**
> CalJohnSmith, I am also new to Linux and I was wondering whether you have a suggestion for the following circumstances. I have an AMD Athlon64 computer with 2GB of memory and two identical 250GB hard drives. I installed Ubuntu 8.04 onto drive 1 yesterday, and it worked great. This morning I installed XP(and then SP3) onto drive 0. My intention is to use Ubuntu for most things, but XP for a couple of programs that run only under Windows. When I boot now, of course XP comes up...and it doesn't recognize the second drive at all (which makes sense). Is it possible now to configure this to dual-boot by manipulating the Windows loader or GRUB? or do I have to re-install Ubuntu on drive 1 to make this work? Many thanks for any advice you might have.
Hi pbags, can you set your BIOS to boot the Ubuntu HDD? If you can do that, it will be ideal, because then you can always boot from the Ubuntu HDD and have the choice of booting either Windows or Ubuntu. Also, if we do it that way, you won't have to touch your Windows drive.

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> Hi pbags, can you set your BIOS to boot the Ubuntu HDD? If you can do that, it will be ideal, because then you can always boot from the Ubuntu HDD and have the choice of booting either Windows or Ubuntu. Also, if we do it that way, you won't have to touch your Windows drive.

I will try that. But that sounds like I would have to go into the BIOS every time -- to change OS -- right?

---

### Post by caljohnsmith on 2008-09-18
> **pbags said:**
> I will try that. But that sounds like I would have to go into the BIOS every time -- to change OS -- right?
Most newer BIOSes have an option on start up where if you press F12/F10 or something similar, you can choose the device to boot from, and it is only temporary. That is probably what you are thinking. But you can permanently change which HDD you want to boot first by going into the BIOS settings and changing the boot order; then you won't have to choose the Ubuntu drive at every start up. 

Once you get BIOS set to boot the Ubuntu drive, boot your Live CD, open a terminal (Applications > Accessories > Terminal), and do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all you need to do to get the Grub menu when booting the Ubuntu drive, but you may need to modify your Grub's menu.lst to make Ubuntu actually boot. Try the above first and let me know the results.

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> Hi pbags, can you set your BIOS to boot the Ubuntu HDD? If you can do that, it will be ideal, because then you can always boot from the Ubuntu HDD and have the choice of booting either Windows or Ubuntu. Also, if we do it that way, you won't have to touch your Windows drive.

OK, caljohnsmith, I tried that, but it didn't work. Actually, my BIOS choices seem to be have "slots" for four different devices. The first two were "CD ROM" (which I'd set earlier to boot from for the 8.04 distro) and "Hard Disk". The third and fourth are "Disabled". And the only two options, though, for each "slot" are "CD ROM" and "Hard Disk", i.e. not "HD 0" and "HD 1"... So, anyway, what I did was I left slot 1 at CD ROM, I made slot 2 "Disabled", and slot 3 "Hard Disk", thinking that perhaps it would go to the second hard drive, finding the first disabled...but no, it booted into XP anyway.  Other suggestions?

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> Most newer BIOSes have an option on start up where if you press F12/F10 or something similar, you can choose the device to boot from, and it is only temporary. That is probably what you are thinking. But you can permanently change which HDD you want to boot first by going into the BIOS settings and changing the boot order; then you won't have to choose the Ubuntu drive at every start up. 

Once you get BIOS set to boot the Ubuntu drive, boot your Live CD, open a terminal (Applications > Accessories > Terminal), and do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all you need to do to get the Grub menu when booting the Ubuntu drive, but you may need to modify your Grub's menu.lst to make Ubuntu actually boot. Try the above first and let me know the results.

OK, I'll take a look at the BIOS some more; sorry, my last response crossed this suggestion of yours!

---

### Post by Salk on 2008-09-18
Hello caljohnsmith!

Here is the output of "sudo fdisk -lu":

```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7aae7aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   144536804    72268371    7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7d0d7d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   281860424   140930181    7  HPFS/NTFS
/dev/sdc2       281860425   390716864    54428220    5  Extended
/dev/sdc5       281860488   386170469    52154991   83  Linux
/dev/sdc6       386170533   390716864     2273166   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdde1dde1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   488375999   244187968+   7  HPFS/NTFS
```

and then I typed:

ubuntu@ubuntu:~$ sudo mount /dev/sdc5 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst

getting this output:

```
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
# kopt=root=UUID=bf0ca8cb-8b26-47e5-8c40-e8862d378a53 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bf0ca8cb-8b26-47e5-8c40-e8862d378a53 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bf0ca8cb-8b26-47e5-8c40-e8862d378a53 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Eagerly waiting for the next step! :popcorn:

Thanks!

---

### Post by caljohnsmith on 2008-09-18
EDIT: My mistake, Salk, I passed over in your previous post where you said you could get the Grub menu on start up. 

To get Ubuntu booting, first boot your Live CD, open the terminal and do:
```
sudo mount /dev/sdc5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Then change the Ubuntu entries to use (hd0,4) instead of (hd2,4). Also, I don't think you mentioned which HDD has your Windows, because all three of them have NTFS partitions. If your Windows is on the same HDD as Ubuntu, then add the following entry to the end of the menu.lst
```
title Windows
root (hd0,0)
makeactive
chainloader +1
```
If Windows is on one of your other drives, add the following:
```
title	   Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Let me know how it goes or if you run into problems.

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> Hi pbags, can you set your BIOS to boot the Ubuntu HDD? If you can do that, it will be ideal, because then you can always boot from the Ubuntu HDD and have the choice of booting either Windows or Ubuntu. Also, if we do it that way, you won't have to touch your Windows drive.

So I figured out how to set the BIOS to boot from HD 1 (where I installed Ubuntu), but it wouldn't boot (in fact, I got an error message, asking for a boot disk). So I set it back to  HD 0 and XP came up fine again. Not sure what to do next.

---

### Post by caljohnsmith on 2008-09-18
> **pbags said:**
> So I figured out how to set the BIOS to boot from HD 1 (where I installed Ubuntu), but it wouldn't boot (in fact, I got an error message, asking for a boot disk). So I set it back to  HD 0 and XP came up fine again. Not sure what to do next.
OK, that's great you can set the Ubuntu drive to boot first, just follow the directions in post #2 for installing Grub to the master boot record (MBR) of your Ubuntu HDD. Then when you boot the Ubuntu drive, you should get a Grub menu on start up. If you can get that far, we should be able to get Ubuntu booting quite easily.

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> Most newer BIOSes have an option on start up where if you press F12/F10 or something similar, you can choose the device to boot from, and it is only temporary. That is probably what you are thinking. But you can permanently change which HDD you want to boot first by going into the BIOS settings and changing the boot order; then you won't have to choose the Ubuntu drive at every start up. 

Once you get BIOS set to boot the Ubuntu drive, boot your Live CD, open a terminal (Applications > Accessories > Terminal), and do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all you need to do to get the Grub menu when booting the Ubuntu drive, but you may need to modify your Grub's menu.lst to make Ubuntu actually boot. Try the above first and let me know the results.

OK, I did the above, then did what you suggested for Salk in this thread. Here is my menu.lst now:
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
# kopt=root=UUID=e918d4a5-0e9d-4a1c-8b4b-cd689657b8a1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e918d4a5-0e9d-4a1c-8b4b-cd689657b8a1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e918d4a5-0e9d-4a1c-8b4b-cd689657b8a1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Suggestions? We were able to get the GRUB boot menu to load off the Ubuntu HDD, but neither the Ubuntu nor XP worked, neither booted.

---

### Post by caljohnsmith on 2008-09-18
That's great you have the Grub menu, pbags, we're just about there. I'm going to make an educated guess since you didn't happen to post "sudo fdisk -lu", but I think all you need to do is change the (hd1,0) references in the Ubuntu entries to (hd0,0). That will probably be all it takes to boot Ubuntu. To boot Windows, replace your existing Windows entry with:
```
title	   Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
If that doesn't make both Ubuntu and Windows bootable from Grub, then be sure to post:
```
sudo fdisk -lu
```
Otherwise let me know how it goes. :)

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> That's great you have the Grub menu, pbags, we're just about there. I'm going to make an educated guess since you didn't happen to post "sudo fdisk -lu", but I think all you need to do is change the (hd1,0) references in the Ubuntu entries to (hd0,0). That will probably be all it takes to boot Ubuntu. To boot Windows, replace your existing Windows entry with:
```
title	   Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
If that doesn't make both Ubuntu and Windows bootable from Grub, then be sure to post:
```
sudo fdisk -lu
```
Otherwise let me know how it goes. :)

THAT WORKED!! Many thanks for the help!! Here's a couple of questions, though:
Can you describe the boot sequence, i.e. what actually happens upon booting up? What happens if my Ubuntu drive dies? will I still be able to boot under XP? And vice versa? Where is the boot loader exactly? And I assume the mapping commands above are there because I put Ubuntu on HD1 and I changed my BIOS to load HD1 first, correct?

---

### Post by caljohnsmith on 2008-09-18
> **pbags said:**
> THAT WORKED!! Many thanks for the help!! Here's a couple of questions, though:
Can you describe the boot sequence, i.e. what actually happens upon booting up? What happens if my Ubuntu drive dies? will I still be able to boot under XP? And vice versa? Where is the boot loader exactly? And I assume the mapping commands above are there because I put Ubuntu on HD1 and I changed my BIOS to load HD1 first, correct?
That's great you have it booting OK now. :) You are in really good shape, because what we did is install the Grub boot loader to the master boot record (MBR) or your Ubuntu HDD, leaving your Windows HDD untouched. That means if your Ubuntu drive dies, you should be able to boot your Windows drive just fine. 

About the mapping commands, those are just for whenever you boot Windows, because Windows XP will refuse to boot if it is on any drive other than the boot drive (the drive first in the boot order). But Grub is a sophisticated enough boot loader that it can fool Windows into thinking it is on the boot drive by using the mapping commands, even though Windows is on some other HDD.

---

### Post by pbags on 2008-09-18
> **caljohnsmith said:**
> That's great you have it booting OK now. :) You are in really good shape, because what we did is install the Grub boot loader to the master boot record (MBR) or your Ubuntu HDD, leaving your Windows HDD untouched. That means if your Ubuntu drive dies, you should be able to boot your Windows drive just fine. 

About the mapping commands, those are just for whenever you boot Windows, because Windows XP will refuse to boot if it is on any drive other than the boot drive (the drive first in the boot order). But Grub is a sophisticated enough boot loader that it can fool Windows into thinking it is on the boot drive by using the mapping commands, even though Windows is on some other HDD.

Will I need to change the BIOS back so that HD0 loads first since HD1 is dead? Or will it be smart enough to know that?

---

### Post by caljohnsmith on 2008-09-18
> **pbags said:**
> Will I need to change the BIOS back so that HD0 loads first since HD1 is dead? Or will it be smart enough to know that?
Most recent BIOSes are smart enough to boot the second HDD if the first one is missing I think. But I don't know your BIOS so I can't say for certain. Even if your BIOS didn't load the other HDD, it should only take a few moments to pop into BIOS and make it the first drive in the boot order.

---

### Post by Salk on 2008-09-19
Hello again caljohnsmith!

Thanks to you, I managed to solve the problem and now the system boots GRUB first and the changes made to menu.lst have had the desired effects: both Ubuntu and Windows XP loads without any hassle.

If I may abuse a little longer of your kind and patience, would you mind speculating as to why the automated installation failed?

In short, for what I understood, the second problem was that GRUB was directing to two partitions were the systems were not present while I fail to even guess what was that made the Ubuntu installer fail to let the PC boots the GRUB.

If it can be of any help, some time ago I installed in this very system both Windows XP and Windows XP 64. I had to manually correct the boot.ini because even then, the system was looking in the wrong partition. Perhaps that's a lead.

I have four physical hard drives: 2 EIDE and 2 on a RAID 0 mode. The 2 RAID ones are connected to a PCI card. Might this be what "confuses" the installers?

Thank you for any further explanations you will want to give me! ;)

---

### Post by caljohnsmith on 2008-09-19
> **Salk said:**
> Hello again caljohnsmith!

Thanks to you, I managed to solve the problem and now the system boots GRUB first and the changes made to menu.lst have had the desired effects: both Ubuntu and Windows XP loads without any hassle.

If I may abuse a little longer of your kind and patience, would you mind speculating as to why the automated installation failed?

In short, for what I understood, the second problem was that GRUB was directing to two partitions were the systems were not present while I fail to even guess what was that made the Ubuntu installer fail to let the PC boots the GRUB.

If it can be of any help, some time ago I installed in this very system both Windows XP and Windows XP 64. I had to manually correct the boot.ini because even then, the system was looking in the wrong partition. Perhaps that's a lead.

I have four physical hard drives: 2 EIDE and 2 on a RAID 0 mode. The 2 RAID ones are connected to a PCI card. Might this be what "confuses" the installers?

Thank you for any further explanations you will want to give me! ;)
Because your Ubuntu entries in your original menu.lst used drive (hd2), and also because you probably didn't change the default setting of where Grub was installed to when you installed Ubuntu, Grub was most likely installed to the master boot record (MBR) of whichever of your other HDDs that was first in the boot order at that time. But you also said in your original post that after installing Ubuntu and rebooting, you didn't get Grub, but instead booted straight into Windows; so something obviously didn't go quite right, because you should have gotten Grub on start up. As you mention above, the problem might have to do with your BIOS settings, using RAID for instance. I can't be sure, so bottom line is: I don't know. :) 

What we did to fix your problem is make sure you set your Ubuntu HDD to boot at start up, we installed Grub to the MBR of that drive, but then we also had to correct your menu.lst entries for Ubuntu/Windows since the Ubuntu installer previously set them up under the assumption that the Ubuntu drive was not the first in the boot order.

One last detail: I would change the "groot" line in your menu.lst to:
```
#groot=(hd0,4)
```
That way when you install new kernels, their entries in menu.lst should use the correct (hd0,4) Ubuntu partition. It's a small detail, but it will save you trouble in the future. :)

---

### Post by demonr675 on 2008-09-19
Along these same lines I am having a problem in which my drive where windows is installed now will not allow me to boot unless the Linux drive is present. It has made some change to how the pc boots where I cannot boot into windows at all. GRUB is trying to load which I do not want. I was trying to install Linux on a HD to run standalone and it seems to have made some change to my Windows HD where I cannot boot from it unless the drive that has Linux is connected. Can anyone shed some light on what I need to do prevent GRUB and Linux from even being a part of my Windows HD?

---

### Post by caljohnsmith on 2008-09-19
> **demonr675 said:**
> Along these same lines I am having a problem in which my drive where windows is installed now will not allow me to boot unless the Linux drive is present. It has made some change to how the pc boots where I cannot boot into windows at all. GRUB is trying to load which I do not want. I was trying to install Linux on a HD to run standalone and it seems to have made some change to my Windows HD where I cannot boot from it unless the drive that has Linux is connected. Can anyone shed some light on what I need to do prevent GRUB and Linux from even being a part of my Windows HD?
Yes, yours is a very common situation where you installed Ubuntu to your external HDD, and Ubuntu installed Grub to the master boot record (MBR) of your internal Windows drive so that Ubuntu would be an option at start up. But if you remove your Ubuntu drive, then Grub can no longer load on start up, and you'll get a Grub error.

So bottom line, you could restore the Windows MBR of your Windows drive, and then install Grub to the MBR of your Ubuntu drive; if you then set the Ubuntu drive first in your BIOS boot order, you can boot it up just fine, and you can configure it so that it will give you the option to boot Ubuntu or Windows. And if you disconnect your Ubuntu drive, you can still boot the Windows drive since it has its own boot loader. 

To restore your Windows MBR, just boot your Windows Install CD, go to the "recovery console" by pressing "r" in the first menu, and run:
```
fixmbr
```
Let me know how it goes.

---

### Post by daviebasite on 2008-11-12
Hi guys,
I also have a missing grub at booting. I tried this procedure:

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

but after restart grub is still missing!

On first physical disk I have windows 2003 server 64x, the second physical disk is separated on two ntfs partitions and two linux partitions "\ and swap"
In bios I have option to boot only from the first hdd (maybe because it's the only disk with mbr information?)

here some history which may be useful:
I had ubuntu 8.04 on the same partitions (for learning purposes), but decided to delete them and to wait for the new release because there where a network problem. Then I fixed the windows mbr with the recovery console and everything worked fine. One week after that the new ubuntu was released and then I faced a big problem with trying to install both 8.04 or 8.10. the installations every time finished in BusyBox (in the forum peoples are saying that this is because the J-micron ide controller) but then how I installed 8.04 the first time? That's weird because the hardware is still the same without any changes (only that mbr fixing stuff is the difference between the first installation and the current tryouts).
Anyway to avoid this now I'm using usb memory stick to install from. With the same manual partitioning options as I installed 8.04 before, the new installation doesn't show grub at a boot time and windows is starting directly like nothing was made.
Please help :)

---

### Post by caljohnsmith on 2008-11-12
Daviebasite, since you say you can only boot from the Windows drive, you could install Grub to the MBR of the Windows drive with:
```
sudo grub
grub> root (hdX,Y)
grub> setup [COLOR="Blue"](hd0)[/COLOR]
grub> quit
```
Give that a shot and let me know how it goes.

---

### Post by daviebasite on 2008-11-12
thanks for the fast reply caljohnsmith :)

> **caljohnsmith said:**
> Daviebasite, since you say you can only boot from the Windows drive, you could install Grub to the MBR of the Windows drive with:
```
sudo grub
grub> root (hdX,Y)
grub> setup [COLOR="Blue"](hd0)[/COLOR]
grub> quit
```
Give that a shot and let me know how it goes.

thanks, currently with this code the grub become avaible at boot:
```
sudo grub
grub> root [COLOR="Blue"](hd2,5)[/COLOR]
grub> setup [COLOR="Blue"](hd2)[/COLOR]
grub> quit
```

and now there is the error 22 message. Now I'll give you all the other info:
```
sudo fdisk -lu



Disk /dev/sda: 81.9 GB, 81964302336 bytes

255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x375c375b



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   160071659    80035798+   7  HPFS/NTFS



Disk /dev/sdb: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xe58ae580



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *          63   625137344   312568641    5  Extended

/dev/sdb5        62926668   625137344   281105338+   7  HPFS/NTFS

/dev/sdb6             189    41013944    20506878   83  Linux

/dev/sdb7        41014008    43006004      995998+  82  Linux swap / Solaris



Partition table entries are not in disk order



Disk /dev/sdc: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x35f5b7ef



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *          63    62926604    31463271    7  HPFS/NTFS

/dev/sdc2        62926605   976768064   456920730    7  HPFS/NTFS



Disk /dev/sdd: 2091 MB, 2091646976 bytes

8 heads, 32 sectors/track, 15958 cylinders, total 4085248 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x221e5780



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *          32     4085247     2042608    b  W95 FAT32
```

sdc1 is my windows boot disk

here is the menu.lst
```

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
# kopt=root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=58b4d5b4-d5ca-4466-9cf0-628a1afc2173

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Server 2003 Enterprise x64 Edition
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
makeactive
chainloader	+1

```

hope that this will clear the things :)
10x in advance

---

### Post by caljohnsmith on 2008-11-12
So you are sure you used "root (hd2,5)"? Because (hd2) is sdc, yet your Linux installation is on sdb according to fdisk. Are you booting the Linux sdb drive on start up? And do you get the Grub error 22 before seeing a Grub menu, or after you get the Grub menu and select Ubuntu to boot? 

Also, please post:
```
sudo blkid
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

---

### Post by daviebasite on 2008-11-12
hi, the error is appearing before seeing the grub menu 
when I do:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,5)
```
thats why I've used root (hd2,5)
when tested with setup (hd0),result was direct boot to windows and when tried with (hd2) the grub become available at boot with error 22 before the menu shows

```
sudo blkid
/dev/sdb2: UUID="4648EE8848EE75D9" LABEL="Work" TYPE="ntfs" 
/dev/sdc5: UUID="9C1C17171C16EC50" LABEL="Library" TYPE="ntfs" 
/dev/sdc6: UUID="58b4d5b4-d5ca-4466-9cf0-628a1afc2173" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc7: TYPE="swap" UUID="51000025-2e62-4797-825d-e64aeaa31a71" 
/dev/sdd1: LABEL="FLASH MP3" UUID="88E0-476C" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system.
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8105
```

Edit:
hmm, with fdisk -lu the output is different than the posted above
```
 sudo fdisk -lu

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x375c375b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   160071659    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35f5b7ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62926604    31463271    7  HPFS/NTFS
/dev/sdb2        62926605   976768064   456920730    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe58ae580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625137344   312568641    5  Extended
/dev/sdc5        62926668   625137344   281105338+   7  HPFS/NTFS
/dev/sdc6             189    41013944    20506878   83  Linux
/dev/sdc7        41014008    43006004      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 2091 MB, 2091646976 bytes
8 heads, 32 sectors/track, 15958 cylinders, total 4085248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32     4085247     2042608    b  W95 FAT32
```
the boot disk is now "sdb" instead of "sdc", why thats happening ?

---

### Post by caljohnsmith on 2008-11-12
Interesting, everything you've posted except your fdisk output shows that your Linux partition is on sdc, not sdb. It looks like the problem is most likely that you are booting the sdb drive instead of the sdc drive, because both drives have Grub installed to the MBR; but the sdb drive points to another drive for its Grub boot files, so booting the sdb drive would likely result in a Grub error 22. How about again posting:
```
sudo fdisk -l
```
Unless it is exactly the same as your post #27. But I would go into your BIOS and change the boot order so that you are booting sdc first and not sdb, or at least I think that is most likely the problem right now. Try that and let me know what happens.

---

### Post by daviebasite on 2008-11-12
here is 
```
sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x375c375b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35f5b7ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3917    31463271    7  HPFS/NTFS
/dev/sdb2            3918       60801   456920730    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe58ae580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    5  Extended
/dev/sdc5            3918       38913   281105338+   7  HPFS/NTFS
/dev/sdc6               1        2553    20506878   83  Linux
/dev/sdc7            2554        2677      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 2091 MB, 2091646976 bytes
8 heads, 32 sectors/track, 15958 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15958     2042608    b  W95 FAT32
```

in my bios only the SATA device is set for boot on which is windows. It's the 500Gb drive from the list.

Now I'll restart to see in the bios what's happening for shure.

Confirmed that in bios only this device is set for boot (the 500G one, that above is reported as sdb), actually it's the only device that can be chosen from the three disks that I have 
But now after reboot the fdisk command report it as a sdc, again the order was changed. actualy I'm not changing anything just rebooting with live cd from usb stick.

---

### Post by caljohnsmith on 2008-11-12
Since you can only boot the sdb drive on start up, one option is to install Grub correctly to its MBR so that it will point to your sdc drive for its boot files; but because we don't know whether the sdc drive is second or third in the BIOS boot order, there are two possibilities for configuring Grub, so we might have to try twice with that method. Also, the big disadvantage of doing it that way is your sdb and sdc drives will be dependent on each other for booting, so if anything happens to either of them (including simply disconnecting one of them) you most likely won't be able to boot at all. 

I think a better solution would be to install Grub4DOS inside your Windows partition on sdb, and then you can use Grub4DOS to boot either Windows or Ubuntu; that way your sdb drive won't be dependent on your sdc drive for booting. Let me know if you want to pursue either of the choices I outlined above, and I can give you specific directions to use either method if you want.

---

### Post by daviebasite on 2008-11-12
I'm so thankful for taking your time for my problems :)

The most strange thing is that on the same hardware and also partitions I was installed ubuntu8.04.1 and automatically after the installation the grub was working and I have a working dual boot, and that let me think that somehow it must work as is.I was removed this installation a few weeks ago. And now when I tried to make a clean install of ubuntu8.10 I cant boot to it. I tried to reinstall it 3 times and it doesn't finished with correct grub install. Every time it rebooted directly to windows.

I've done some tests with rebooting and checking with fdisk and found some strange behaviour.

When I reboot few times from the live cd, fdisk reports that "finally" this is "sdb".
But when I reboot and remove the usb stick, of course the grub error appear. And after that if I boot from live cd, fdisk reports this disk as "sdc" and now after another reboot with live cd it becomes "sdb" and every next reboot from live cd repots it as "sdb"
So maybe it must be set when it is reported as "sdb"
here is the last I think correct report:
```
sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x375c375b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35f5b7ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3917    31463271    7  HPFS/NTFS
/dev/sdb2            3918       60801   456920730    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe58ae580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    5  Extended
/dev/sdc5            3918       38913   281105338+   7  HPFS/NTFS
/dev/sdc6               1        2553    20506878   83  Linux
/dev/sdc7            2554        2677      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 2091 MB, 2091646976 bytes
8 heads, 32 sectors/track, 15958 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15958     2042608    b  W95 FAT32
```

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,5)
```

```
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
# kopt=root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=58b4d5b4-d5ca-4466-9cf0-628a1afc2173

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=58b4d5b4-d5ca-4466-9cf0-628a1afc2173 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		58b4d5b4-d5ca-4466-9cf0-628a1afc2173
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Server 2003 Enterprise x64 Edition
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
makeactive
chainloader	+1
```

can you tell me please how to configure current grub according to reports above?
I'm appreciating your advise, and thank you again :)

---

### Post by caljohnsmith on 2008-11-12
[QUOTE=daviebasite]I'm so thankful for taking your time for my problems :)[/QUOTE]
You're welcome, I know that figuring out booting problems can sometimes be a real pain. :)

OK, if you want to install Grub to the MBR of sdb and get it working similar to what you had before, try the following, but note that the commands assume that linux is on sdc, not sdb:
```
sudo grub
grub> device (hd1) /dev/sdc
grub> device (hd0) /dev/sdb
grub> root (hd1,5)
grub> setup (hd0)
grub> quit
```
Reboot, make sure you don't have your USB flash drive connected, and if you still get a Grub error, then boot your Live CD again and try:
```
sudo grub
grub> device (hd2) /dev/sdc
grub> device (hd0) /dev/sdb
grub> root (hd2,5)
grub> setup (hd0)
grub> quit
```
One of those above cases should work, but only if your drive order stays consistent in BIOS; the fact that the linux drive changes between sdb and sdc is not a good sign, so maybe when you boot it might work and sometimes not. Anyway, let me know how it goes. :)

---

### Post by daviebasite on 2008-11-12
Finally there is a progress :guitar:

```
sudo grub
grub> device (hd1) /dev/sdc
grub> device (hd0) /dev/sdb
grub> root (hd1,5)
grub> setup (hd0)
grub> quit
```

there is grub and I can boot to ubuntu, but not in windows. There was message saying "Grub Loading..." for ever and I realised that maybe with my previous attempts I was damaged my windows mbr. Then I decided to start over from the beginning.
I formated the linux partitions, fixed booting in windows with recovery console and reinstalled linux :)
After reboot there was the previous situation, directly boot in windows.
Then I booted from live cd, checked that fdisk report is correct and redo the above grub commands with a little difference because after formating the partitions changed their numbers (from sdc6 to sdc5):
```
grub> device (hd1) /dev/sdc
grub> device (hd0) /dev/sdb
grub> root (hd1,4)
grub> setup (hd0)
grub> quit
```

and now I'm at the same position as before, I can boot to ubuntu but not to windows.
Also when I boot from grub there is a new configuration report from fdisk:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe58ae580

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    5  Extended
/dev/sda5               1        2553    20506878   83  Linux
/dev/sda6            2554        2677      995998+  82  Linux swap / Solaris
/dev/sda7            2678        3917     9960268+   7  HPFS/NTFS
/dev/sda8            3918       38913   281105338+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x375c375b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35f5b7ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3917    31463271    7  HPFS/NTFS
/dev/sdc2            3918       60801   456920730    7  HPFS/NTFS
```
```
sudo blkid
/dev/sdd1: LABEL="FLASH MP3" UUID="88E0-476C" TYPE="vfat" 
/dev/sdc1: UUID="3A48B23D48B1F829" LABEL="System" TYPE="ntfs" 
/dev/sdc2: UUID="4648EE8848EE75D9" LABEL="Work" TYPE="ntfs" 
/dev/sda5: UUID="96f00c5b-6405-4385-95eb-727deef1c4f5" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="51252e62-4797-825d-e64a-eaa31a7128cf" 
/dev/sda7: UUID="4228857F288572A9" LABEL="windows SWAP" TYPE="ntfs" 
/dev/sda8: UUID="9C1C17171C16EC50" LABEL="Library" TYPE="ntfs" 
dick@workstation:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
dick@workstation:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
dick@workstation:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
dick@workstation:~$ sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
dick@workstation:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8102
```


So how can I make my windows boot too? Thanks again for your help :)

---

### Post by caljohnsmith on 2008-11-12
That's great news you have Ubuntu booting at least; I should mention though, based on the symptoms you describe, you might be on the verge of having a hardware problem. I would recommend doing a HDD diagnostic test on each of your drives, and also I would run the "memtest86+" option from the Grub menu so you can check your RAM. I really think it would be worth it, because the inconsistent behavior you are seeing is not a good sign at all. If you want directions for doing a HDD diagnostic test from Ubuntu, let me know.

But to answer your question, to boot Windows first open up your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add the following entries:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, and one of those entries should hopefully work. If not, let me know exactly what happens when you try each one from the Grub menu. Let me know how it goes. :)

---

### Post by daviebasite on 2008-11-12
> ```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
I've tried this but without success
when choose (hd1):
```
Starting up...
```
and stays forever,
when choose (hd2):
```
Starting up...
GRUB
```
and again stay forever

what else I can do?

---

### Post by caljohnsmith on 2008-11-12
I think that may be my mistake, try the following menu entry for Windows instead:
```
title Windows
root (hd0,0)
chainloader +1
```
And just to clarify, your Windows is on the 80 GB drive, is that true?

---

### Post by daviebasite on 2008-11-12
> **caljohnsmith said:**
> I think that may be my mistake, try the following menu entry for Windows instead:
```
title Windows
root (hd0,0)
chainloader +1
```
And just to clarify, your Windows is on the 80 GB drive, is that true?

Yes! Finally everything is working as a charm :)
You Rock!
Thank You very much my friend, I'll never forget your help!
windows is on the 500 GB drive.

---

### Post by unutbu on 2008-11-12
Wow. I'm amazed by what you can do, caljohnsmith. The ubuntu community is really fortunate to have you here. Thank you!

---

### Post by caljohnsmith on 2008-11-12
> **daviebasite said:**
> Yes! Finally everything is working as a charm :)
You Rock!
Thank You very much my friend, I'll never forget your help!
windows is on the 500 GB drive.
You're most welcome, I'm really glad it's all working now for you. Cheers and have fun with Ubuntu. :)

:popcorn:

---

### Post by caljohnsmith on 2008-11-12
> **unutbu said:**
> Wow. I'm amazed by what you can do, caljohnsmith. The ubuntu community is really fortunate to have you here. Thank you!
Thanks so much for the compliment, Unutbu; I try to help out as much as I can. It's a continually learning process for me though. And even though you probably didn't realize it, I've picked up some really useful tips and tricks from you. It's great when we can all share. :)

---

### Post by pmenefee on 2008-12-31
Many thanks from me too!!

I installed on an external HDD and could not get it to boot until I followed your instructions and I'm up and running.  Never would have happened without your directions.

Pete

---

