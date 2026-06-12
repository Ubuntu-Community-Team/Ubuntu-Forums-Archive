---
title: "Vista won't show in grub"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by texter2468 on 2008-10-11
I have installed windows vista, windows xp, and ubuntu 8.10 on my computer. When I try to boot into grub though, it only shows ubuntu and windows xp. Here is how I installed the operating systems.

1. Installed Vista
2. Installed XP
3. Installed Ubuntu

Here is my output of sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ce69ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        3570    28675993+   7  HPFS/NTFS
/dev/sda3            5720        9729    32210325    5  Extended
/dev/sda4            3581        5719    17181517+   7  HPFS/NTFS
/dev/sda5            5720        9558    30836736   83  Linux
/dev/sda6            9559        9729     1373526   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2008-10-11
OK, so which partition of sda2 and sda4 is Vista and which is XP? Also, when you boot into Ubuntu, please post:
```
cat /boot/grub/menu.lst
```

---

### Post by texter2468 on 2008-10-11
> **caljohnsmith said:**
> OK, so which partition of sda2 and sda4 is Vista and which is XP? Also, when you boot into Ubuntu, please post:
```
cat /boot/grub/menu.lst
```

sda2 is xp. sda4 is vista.

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
# kopt=root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2008-10-11
Unless you have some issue with Vista, all you need to do is add the following to your menu.lst to boot Vista:
```
title Windows Vista
root (hd0,3)
chainloader +1
```
To edit your menu.lst, you can pull it up with: 
```
gksudo gedit /boot/grub/menu.lst
```
And add the above entry to the bottom of the file. Let me know how it goes or if you run into problems. :)

---

### Post by texter2468 on 2008-10-11
> **caljohnsmith said:**
> Unless you have some issue with Vista, all you need to do is add the following to your menu.lst to boot Vista:
```
title Windows Vista
root (hd0,3)
chainloader +1
```
To edit your menu.lst, you can pull it up with: 
```
gksudo gedit /boot/grub/menu.lst
```
And add the above entry to the bottom of the file. Let me know how it goes or if you run into problems. :)
thanks I'll try it and get back to you in a few minutes.

---

### Post by texter2468 on 2008-10-11
It didn't work. I get the error

"ntldr missing press ctrl+alt+del to restart"

I have uninstalled the vista longhorn bootloader. Could this be the problem?

---

### Post by meierfra. on 2008-10-11
> Here is how I installed the operating systems.

1. Installed Vista
2. Installed XP
3. Installed Ubuntu

caljohnsmith, did you overlook this in the  first post?  Xp overwrote the Vista boot sector.

(Edit: hadn't read the last few posts. Something else is going on)

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> caljohnsmith, did you overlook this in the  first post?  Xp overwrote the Vista boot sector.
How should I fix it then?

---

### Post by meierfra. on 2008-10-11
>  I have uninstalled the vista longhorn bootloader

 How did you do that?

---

### Post by caljohnsmith on 2008-10-11
Texter2468, how about doing:
```
sudo mkdir /media/sda2 /media/sda4
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda4 /media/sda4
ls -l /media/sda2
ls -l /media/sda4

```
That will give us an idea of where you boot files are and maybe what is going on.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> How did you do that?
Xp just overwrote it when I installed it.

---

### Post by andrewwg94 on 2008-10-11
after you choose windows xp from grub, press f8 to quickly bring up the windows boot loader. vista should be there

---

### Post by texter2468 on 2008-10-11
Here it is. 

```
user1@user1-laptop:~$ sudo mkdir /media/sda2 /media/sda4
mkdir: cannot create directory `/media/sda2': File exists
mkdir: cannot create directory `/media/sda4': File exists
user1@user1-laptop:~$ sudo mount /dev/sda2 /media/sda2
user1@user1-laptop:~$ sudo mount /dev/sda4 /media/sda4
user1@user1-laptop:~$ ls -l /media/sda2
total 2599924
drwxrwxrwx 1 root root       8192 2008-01-11 09:53 AceReader Pro (Server)
-rwxrwxrwx 2 root root          2 2007-01-15 14:07 AUDIT_INSTALL_IN_PROGRESS
-rwxrwxrwx 1 root root          0 2005-06-22 05:32 AUTOEXEC.BAT
drwxrwxrwx 1 root root          0 2008-10-10 14:32 Boot
-rwxrwxrwx 1 root root        210 2008-10-11 14:24 boot.ini
-rwxrwxrwx 1 root root        210 2008-10-11 14:12 boot.ini~
-rwxrwxrwx 1 root root     333203 2008-04-04 04:45 bootmgr
drwxrwxrwx 1 root root          0 2007-01-15 13:51 Bundle
drwxrwxrwx 1 root root          0 2007-01-15 13:51 CMPNENTS
-rwxrwxrwx 1 root root          0 2005-06-22 05:32 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-08-19 11:30 Documents and Settings
drwxrwxrwx 1 root root          0 2007-01-15 13:51 Drivers
-rwxrwxrwx 1 root root     171136 2006-11-02 14:00 grldr
-rwxrwxrwx 1 root root 1063309312 2008-10-11 15:10 hiberfil.sys
-rwxrwxrwx 1 root root          0 2005-06-22 05:32 IO.SYS
-rwxrwxrwx 1 root root          0 2005-06-22 05:32 MSDOS.SYS
-rwxrwxrwx 1 root root      23732 2007-08-23 17:05 _NavCClt.Log
drwxrwxrwx 1 root root          0 2008-10-11 14:29 New Stuff
-rwxrwxrwx 1 root root      47564 2004-08-04 07:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-08-23 16:41 ntldr
-rwxrwxrwx 1 root root 1598029824 2008-10-11 15:10 pagefile.sys
-rwxrwxrwx 1 root root         90 2007-01-15 14:08 powerdvd.log
drwxrwxrwx 1 root root      24576 2008-10-09 20:37 Program Files
-rwxrwxrwx 1 root root        186 2007-01-15 14:12 RaidApp.log
drwxrwxrwx 1 root root          0 2008-10-10 14:36 $RECYCLE.BIN
drwxrwxrwx 1 root root       4096 2008-08-19 13:00 RECYCLER
-rwxrwxrwx 2 root root          0 2007-01-15 14:30 REQUEST_OEMRESET_ENDUSER
drwxrwxrwx 1 root root          0 2007-01-15 13:51 System Recovery
drwxrwxrwx 1 root root       4096 2008-10-07 10:30 System Volume Information
-rwxrwxrwx 1 root root        191 2007-01-15 14:08 touchpad.log
-rwxrwxrwx 1 root root         11 2007-08-23 17:02 trace.ini
-rwxrwxrwx 1 root root          2 2007-01-15 14:00 USER
drwxrwxrwx 1 root root      98304 2008-10-11 14:26 WINDOWS
user1@user1-laptop:~$ ls -l /media/sda4
total 2382394
-rwxrwxrwx 1 root root         24 2006-09-18 16:43 autoexec.bat
drwxrwxrwx 1 root root          0 2008-10-11 16:20 Boot
-rwxrwxrwx 1 root root     333203 2008-04-04 04:45 bootmgr
-rwxrwxrwx 3 root root         10 2006-09-18 16:43 config.sys
-rwxrwxrwx 1 root root        106 2008-04-07 16:38 desktop.ini
drwxrwxrwx 1 root root          0 2006-11-02 07:00 Documents and Settings
-rwxrwxrwx 1 root root     820767 2008-04-07 10:41 folderbg.jpg
-rwxrwxrwx 1 root root 1061257216 2008-10-11 13:56 hiberfil.sys
-rwxrwxrwx 1 root root 1377116160 2008-10-11 13:56 pagefile.sys
drwxrwxrwx 1 root root          0 2008-04-04 04:55 PerfLogs
drwxrwxrwx 1 root root       4096 2008-10-10 13:47 ProgramData
drwxrwxrwx 1 root root       8192 2008-10-11 15:25 Program Files
drwxrwxrwx 1 root root          0 2008-10-10 14:36 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-10-10 23:09 RECYCLER
drwxrwxrwx 1 root root       4096 2008-10-10 17:38 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-10 13:47 Users
drwxrwxrwx 1 root root      16384 2008-10-10 14:32 Windows

```

---

### Post by texter2468 on 2008-10-11
> **andrewwg94 said:**
> after you choose windows xp from grub, press f8 to quickly bring up the windows boot loader. vista should be there
I installed windows xp after installing vista. Will this still work?

---

### Post by caljohnsmith on 2008-10-11
Well, you've got Vista's boot files in your XP sda2 partition, so I'm not exactly sure how that happened since you installed Vista first, but maybe meierfra knows. I also notice that your boot.ini file was modified at some point from linux, because you have a boot.ini~ file in that directory. What did you do to boot.ini?

EDIT: OK, I see--you have grub4dos (the grldr file) in the Windows XP directory too. Did you try and install Grub4DOS? That would explain your modified boot.ini file.

---

### Post by texter2468 on 2008-10-11
> **caljohnsmith said:**
> Well, you've got Vista's boot files in your XP sda2 partition, so I'm not exactly sure how that happened since you installed Vista first, but maybe meierfra knows. I also notice that your boot.ini file was modified at some point from linux, because you have a boot.ini~ file in that directory. What did you do to boot.ini?

EDIT: OK, I see--you have grub4dos (the grldr file) in the Windows XP directory too. Did you try and install Grub4DOS? That would explain your modified boot.ini file.
well I tryed some other suggestions from people and that may have messed it up. I didn't edit it. I just opened it and saved it accidentally. I don't think that should be the problem though.

EDIT: No how do I do that? What does that do?

---

### Post by caljohnsmith on 2008-10-11
I think it would help if you told us exactly what you did after installing your three OSes, because you say:
[QUOTE=texter2468]well I tryed some other suggestions from people and that may have messed it up.[/QUOTE]
So you installed Vista, you installed XP, and then you installed Ubuntu, and exactly what did you do after that?

---

### Post by meierfra. on 2008-10-11
Fixing your problem should be fairly easy. But I'm still confused. Are you sure that  XP is on sda2 and vista on  sda4?

---

### Post by texter2468 on 2008-10-11
> **caljohnsmith said:**
> I think it would help if you told us exactly what you did after installing your three OSes, because you say:

So you installed Vista, you installed XP, and then you installed Ubuntu, and exactly what did you do after that?
Well first I repaired the vista longhorn loader. Then I decided that I wanted my computer to boot directly into xp so I used this command I found on a website. 

e:\ boot\bootsect.exe /nt52 ALL /force
Then I deleted the boot.BAK and bootsect.BAK files from XP

That command made xp boot up automatically without the vista longhorn booter showing up. This is how I wanted it. Then recently I decided I wanted to install grub on my computer and boot all 3 operating systems from there. Is this possible without using the vista boot loader?

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> Fixing your problem should be fairly easy. But I'm still confused. Are you sure that  XP is on sda2 and vista on  sda4?
Yes I am positive. XP has more hard drive space than Vista.

---

### Post by meierfra. on 2008-10-11
O.k it starts to make some sense. Try this


```
e:\boot\bootsect.exe /nt60 X:
```
where X is the drive letter of your Vista partition.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> O.k it starts to make some sense. Try this


```
e:\boot\bootsect.exe /nt60 X:
```
where X is the drive letter of your Vista partition.
Is it ok if I run that from windows xp? What will that do?

---

### Post by meierfra. on 2008-10-11
Yes. Just make sure that you use the correct drive letters. But you need to have the Vista CD in the CDrom drive (unless you copied "bootsect.exe" to your Windows partition)

---

### Post by meierfra. on 2008-10-11
> What will that do?

It will restore the boot sector of your Vista partition.

("e:\boot\bootsect.exe /nt52 ALL /force" did change the bootsector of sda2 and sda4)

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> Yes. Just make sure that you use the correct drive letters. But you need to have the Vista CD in the CDrom drive (unless you copied "bootsect.exe" to your Windows partition)
What will that do though?

---

### Post by meierfra. on 2008-10-11
> What will that do though?
See my last post. We posted at the same time.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> It will restore the boot sector of your Vista partition.

("e:\boot\bootsect.exe /nt52 ALL /force" did change the bootsector of sda2 and sda4)
But will that make the vista bootloader show up on start? I don't want to use the vista bootloader. I just want to be able to boot vista directly from grub if that's possible.

Edit: Let me explain what I want again. I want grub to boot directly into windows vista without showing the longhorn bootloader. Last time I got it to work by using grub but the only option to boot into windows was "windows xp professional". Then when I selected that the vista longhorn bootloader showed up and I had to select vista. Now I would like it so Vista shows up on the grub menu if that is possible.

---

### Post by caljohnsmith on 2008-10-11
[QUOTE=meierfra.]
e:\boot\bootsect.exe /nt60 X:

It will restore the boot sector of your Vista partition.
[/QUOTE]
And just for my own understanding, meierfra, would "bootrec /fixboot" restore the Vista partition boot sector in the same way?

---

### Post by meierfra. on 2008-10-11
> But will that make the vista bootloader show up on start?

No.  It only lets you boot Vista from the Grub menu.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> No.  It only lets you boot Vista from the Grub menu.
But will that bring up the vista longhorn loader after I tell grub to boot up windows as I explained in the edit of my last post? Sorry for the trouble.

---

### Post by meierfra. on 2008-10-11
> And just for my own understanding, meierfra, would "bootrec /fixboot" restore the Vista partition boot sector in the same way?

Yes. But   "bootsect.exe"  lets you explicitly specify the partition via the drive letter ( and you can choose to install an XP boot sector (with /nt52) or a Vista boot sector (/nt60))

---

### Post by meierfra. on 2008-10-11
> But will that bring up the vista longhorn loader after I tell grub to boot up windows as I explained in the edit of my last post? Sorry for the trouble.

It might. But then you just need to delete XP from the Vista boot loader menu..

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> It might. But then you just need to delete XP from the Vista boot loader menu..
Is there any way to do it without using vista boot loader at all? I am planning on making the computer boot into xp directly later and installing grub on a flash drive later. I can only do this if the vista boot loader is not used.

I am also willing to install the vista longhorn boot loader on a usb or cd if you know how to do that. Thanks for all your help so far.

---

### Post by meierfra. on 2008-10-11
> I can only do this if the vista boot loader is not used.

This is wrong. Just install  grub to the mbr of the USB drive, restore the MBR of the internal drive and leave the boot flag on /dev/sda2.  Then your computer will boot directly into XP (unless you boot from the USB drive)

(since the vista boot loader is on sda4 and the boot flag on sda2, the vista boot loader will not interfere with the XP boot loader)

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> This is wrong. Just install  grub to the mbr of the USB drive, restore the MBR of the internal drive and leave the boot flag on /dev/sda2.  Then your computer will boot directly into XP (unless you boot from the USB drive)
Ok. How would I install grub and vista bootloader on a USB drive then? That will work perfectly for me. I just need to be able to boot into all my operating systems somehow without putting grub or vista on the hard drive MBR. I want it to boot xp directly without showing any boot loaders when I turn on my computer. I think we almost have it here.

---

### Post by meierfra. on 2008-10-11
There is no reason to put the Vista boot loader on the USB. (If you really really want  I can show you how to do it, but it makes no sense what so ever).

---

### Post by meierfra. on 2008-10-11
Vista boot loader will be on  sda4, not on the MBR. It will not interfere with the XP boot loader.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> There is no reason to put the Vista boot loader on the USB. (If you really really want  I can show you how to do it, but it makes no sense what so ever).
That would really help. Thanks.

---

### Post by meierfra. on 2008-10-11
> How would I install grub ... on a USB drive 

Just follow the advice caljohnsmith gave   you in your other thread. But first you need to fix the Vista boot sector. Otherwise you won't be able to boot into Vista.

---

### Post by meierfra. on 2008-10-11
> That would really help. Thanks.

But it would be lots of work and accomplish absolutely nothing.

---

### Post by texter2468 on 2008-10-11
> **meierfra. said:**
> But it would be lots of work and accomplish absolutely nothing.
Well here's a better description. I want to be able to use the flash drive when I want to boot into ubuntu or vista. When I turn on my computer I want it to boot directly into xp without any bootloaders coming up, unless I have the flash drive in. I don't care how this is set up. Can you please tell me how this can be done?

---

### Post by meierfra. on 2008-10-11
Just to clarify: 

 "e:\boot\bootsect.exe /nt60 X:"  

will change the  boot sector of /dev/sda4. It does not change the MBR and it does not change the boot sector of /dev/sda2.  So it will not effect XP in any way.

---

### Post by meierfra. on 2008-10-11
> Well here's a better description. I want to be able to use the flash drive when I want to boot into ubuntu or vista. When I turn on my computer I want it to boot directly into xp without any bootloaders coming up, unless I have the flash drive in.

But that IS exactly what will happen if you follow my advice.

So first 
```

"e:\boot\bootsect.exe /nt60 X:" 
```

Then follows caljohsmith advice how to install  grub to the MBR of the USB drive.

---

### Post by meierfra. on 2008-10-11
There is  one more step.  Run "fixmbr" from the XP CD or "bootrec /fixmbr" from the Vista CD.

---

### Post by texter2468 on 2008-10-11
Alright thanks I'll try it and get back to you.

---

### Post by Louis de Broglie on 2008-10-11
I did not read the whole post. But this might help if xp have overwritten the vista boot loader :)

> 
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)


---

### Post by texter2468 on 2008-10-11
I am still having a problem meierfra. Please reply on the following link if you have any more suggestions.

[http://ubuntuforums.org/showthread.php?t=944420](http://ubuntuforums.org/showthread.php?t=944420)

---

