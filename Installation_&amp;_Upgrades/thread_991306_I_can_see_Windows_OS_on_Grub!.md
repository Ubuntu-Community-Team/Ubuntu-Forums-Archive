---
title: "I can see Windows OS on Grub!"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by dimis80 on 2008-11-23
Friends good evening...

To take things from the beginning:

I have on my desktop 3 hdd installed.

1st - 160gb -> windows installed
2nd - 250gb -> for files (and after for Ubuntu 8.10)
3rd - 500gb -> Ubuntu installed

I wanted to transfer Ubuntu to my 250 hdd so i got into windows, free up the 250hdd from files and i made a format to the 500gb that my ubuntu was installed. so i had 2 drives empty.

Then i installed in the 250gb my Ubuntu and i put on hd0 the boot loader.
When Ubuntu and Grub started i only had the 3 choices of Ubuntu. normal, safe and memory test.

Where the windows gone??? any ideas on that...??? I would appreciate your help on this.. :confused:
Also i cannot see the windows drive when i am on ubuntu..

---

### Post by caljohnsmith on 2008-11-23
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
So we can get clearer picture of your setup.

---

### Post by dimis80 on 2008-11-23
here goes my results from sudo fdisk -lu:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d2e2d2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ad72833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   468648179   234324058+  83  Linux
/dev/sdb2       468648180   488392064     9871942+   5  Extended
/dev/sdb5       468648243   488392064     9871911   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x270a5521

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976773166   488386552    7  HPFS/NTFS
```

---

### Post by caljohnsmith on 2008-11-23
Looks like your Windows is there, so how about booting into Ubuntu, opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end of the file add:
```
title Windows 
root (hd0,0)
chainloader +1
```
Reboot, select Windows from the Grub menu, and let me know what happens. :)

---

### Post by melojo on 2008-11-23
this guide below worked for me

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dimis80 on 2008-11-23
> **caljohnsmith said:**
> Looks like your Windows is there, so how about booting into Ubuntu, opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end of the file add:
```
title Windows 
root (hd0,0)
chainloader +1
```
Reboot, select Windows from the Grub menu, and let me know what happens. :)

i cant edit the file... why i am on as admin..

ohhh Ok i did it...i go through restart...

---

### Post by dimis80 on 2008-11-23
ubuntu loaded after selecting windows in grub :(.

---

### Post by caljohnsmith on 2008-11-23
Make sure the "hiddenmenu" line in your menu.lst has a pound sign # in front of it:
```
#hiddenmenu
```
Also please post:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sda1 count=1 2>/dev/null | strings | grep -ie grub -ie ntldr -ie bootmgr
```

---

### Post by dimis80 on 2008-11-24
Thanks for the reply!

I should give a reply later today cause i'm in office now.

Can you explain what the last codes mean? it should help me learning.. thanks!;-)

---

### Post by caljohnsmith on 2008-11-24
> **dimis80 said:**
> Thanks for the reply!

I should give a reply later today cause i'm in office now.

Can you explain what the last codes mean? it should help me learning.. thanks!;-)
Well the first code basically looks inside the first sector of the HDD (Master Boot Record) and sees whether the text string "grub" or "missing operating system" is there; if the string "grub" is in the MBR, then you have Grub installed to the MBR, but if the string "missing operating system" is in the MBR, that means you have a Windows type MBR. 

The second code looks a few sectors past the MBR where Grub's stage1.5 file gets embedded, and then it returns a hex code that when deciphered, it will tell you which drive and partition Grub points to for its boot files (stage2 and menu.lst). So basically it lets you figure out which drive/partition controls Grub in the MBR, which is extremely useful when troubleshooting many Grub problems. 

The third code looks in the boot sector of sda1 (your Windows partition) for the following strings: "grub", "ntldr", or "bootmgr". If you at some point accidentally installed Grub to the boot sector of your Windows sda1 partition like I suspect at this point, that command will return "grub". But if you have a healthy Windows boot sector, the command should return either "ntldr" if you have XP, or "bootmgr" if you have Vista (you never mentioned which Windows version you have--which one is it?) Anyway, that should hopefully help us figure out what your problem is about booting Windows. :)

---

### Post by dimis80 on 2008-11-24
I have windows xp. I will now that i'm home put the above commands you gave me and i'll let you know...:)
do you think we'll fix this?

---

### Post by dimis80 on 2008-11-24
Below you will see also my menu.lst (check if i put correctly the code you gave me):

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=d9100d12-8c07-41de-8e15-e66c36af3ee7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d9100d12-8c07-41de-8e15-e66c36af3ee7

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
# defoptions=quiet

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
uuid		d9100d12-8c07-41de-8e15-e66c36af3ee7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d9100d12-8c07-41de-8e15-e66c36af3ee7 ro quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d9100d12-8c07-41de-8e15-e66c36af3ee7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d9100d12-8c07-41de-8e15-e66c36af3ee7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d9100d12-8c07-41de-8e15-e66c36af3ee7
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional
root		(hd0,0)
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by dimis80 on 2008-11-24
Also:

```
mitsakos@mitsakos-beast:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
[sudo] password for mitsakos: 
GRUB 

```

```
mitsakos@mitsakos-beast:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

```

```
mitsakos@mitsakos-beast:~$ sudo dd if=/dev/sda1 count=1 2>/dev/null | strings | grep -ie grub -ie ntldr -ie bootmgr
GRUB 

```

---

### Post by caljohnsmith on 2008-11-24
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "hiddenmenu" line near the top to:
```
#hiddenmenu
```
Also, the biggest part of your problem right now is that your Windows sda1 boot sector has Grub installed to it when it shouldn't. You didn't mention yet, but are you using Windows XP or Windows Vista?

How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Backup BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "Backup BS" in testdisk, reboot and let me know what happens when you boot Windows from Grub. :)

---

### Post by dimis80 on 2008-11-24
I am using Windows XP. I fixed hiddenmenu...

i will run what you told me... i will be back...

---

### Post by dimis80 on 2008-11-24
It gave me:

Sectors are identical

A valid NTFS boot sector must be present in order to access any data;
even if partition is not bootable

[Quit]  [List]  [Rebuild BS]  [Repair MFT]  [Dump]
[Return to advance menu]

what i should do?

---

### Post by caljohnsmith on 2008-11-24
Sorry about asking whether you had XP or Vista, I see now that you did answer that question before. :) Anyway, I'm really surprised that testdisk says the boot sectors are identical, because according to your post #13, you have Grub installed to the boot sector of sda1. You can go ahead and quit testdisk. Do you have a Windows Install CD? If so, boot that, and at the first main menu press "r" to go to the "recovery console", and then run:
```
fixboot
```
If you don't have your Windows Install CD handy, you can instead download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Give that a shot and let me know how it goes. :)

---

### Post by dimis80 on 2008-11-24
My friend you are awesome! it worked! i am on windows right now!

many many thanks!

(2 more issues left for me on ubuntu,
1st I do not have sound, 2nd my TV card dont work)

I'll post them in the right fields. Can you help on those also???:confused:
[-o<;-);-)

---

### Post by caljohnsmith on 2008-11-24
That's great news it worked and you can use Windows again. About your sound and TV card problems, that might take a bit of troubleshooting, so I would recommend going ahead and starting a new thread for those issues. Anyway, cheers and have fun with your OSes. :)

---

### Post by dimis80 on 2008-11-24
Thank you my friend! I'll do that, hope to meet again!:)

---

### Post by ubuntu27 on 2008-11-24
> **dimis80 said:**
> My friend you are awesome! **it worked**! i am on windows right now!

many many thanks!
[-o<;-);-)

When your issues or problems has been solved, you can mark your thread as "Solved".


[How to mark a thread as Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

