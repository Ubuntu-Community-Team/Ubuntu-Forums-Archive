---
title: "WinXP Missing from GRUB"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Maelgwyn on 2008-01-07
Ok, so I didn't have any luck with my previous question, so I ended up wiping everything on the PC and starting again.

I have 2 HDDs:

/dev/hda - 40Gb - Ubuntu 7.10.
/dev/sda - 300Gb - WinXP Pro.

XP was installed first, onto the larger HDD. Then I installed Ubuntu. Now WinXP doesn't show in my GRUB list at all!

I've fiddled with menu.lst and this is as far as I managed to get...

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3ac91ce7-e74d-4524-8cc2-59546718559f ro

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3ac91ce7-e74d-4524-8cc2-59546718559f ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3ac91ce7-e74d-4524-8cc2-59546718559f ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

 title        Windows XP Professional
 rootnoverify    (sd0,0)
 chainloader    +1

```

Now when I try to boot into WinXP, I get told error 23 and that the number is incorrect... Can someone please help? I'd really rather not just do the Windows Way and kill everything and try again! ^.^

---

### Post by logos34 on 2008-01-07
> **Maelgwyn said:**
> Now when I try to boot into WinXP, I get told error 23 and that the number is incorrect... 

change it to this:
> 
title        Windows XP Professional
[B]root        (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive[/B]
chainloader +1

Add windows disk to /boot/grub/device.map if it doesn't already exist:

> (hd0) /dev/hda
**(hd1) /dev/sda**

Or if it doesn't work try it without the 'map' lines.

---

### Post by logos34 on 2008-01-07
afterthought:

are you sure linux is seeing the drives as sda and hda, or sda and sdb?

> /dev/hda - 40Gb - Ubuntu 7.10.
/dev/sda - 300Gb - WinXP Pro

check with 

**sudo fdisk -l**

---

### Post by Maelgwyn on 2008-01-07
> **logos34 said:**
> afterthought:

are you sure linux is seeing the drives as sda and hda, or sda and sdb?



check with 

**sudo fdisk -l**

```
nik@tane:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44959918

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57a77e9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38912   312560608+   7  HPFS/NTFS

```


>.<

I tried your way, and when I tried to boot WinXP, I got ```
NTLDR is missing. Press Ctrl+Alt+Del to restart.
```

Then when I rebooted I couldn't even boot Ubuntu! Thankfully I have my trusty SuperGRUB cd to boot stuff ^.^

---

### Post by logos34 on 2008-01-08
rats...had to be the device.map edit that threw it for a loop.  Boot the ubuntu live cd, mount root hda1, and change device.map back to what it was.

---

### Post by logos34 on 2008-01-08
windows should boot with one of the following: 

root (hd1,0)

root (hd0,0)

or 

root (hd1,0) with the 'map' lines

note: even though linux OS sees the drives as 'sda' and 'hda', grub uses 'hd_' notation for all drives, whether sata, ide, usb, usb, etc

---

### Post by Maelgwyn on 2008-01-08
> **logos34 said:**
> rats...had to be the device.map edit that threw it for a loop.  Boot the ubuntu live cd, mount root hda1, and change device.map back to what it was.

I didn't change the device.map... I loaded it as is, and Windows was already in there...


Could it be the ```
map        (hd0) (hd1)
map        (hd1) (hd0)
```?

Oh, and I am currently logged into my Ubuntu partition... SuperGRUB allows me to do so =)

---

### Post by logos34 on 2008-01-08
> **Maelgwyn said:**
> I didn't change the device.map... I loaded it as is, and Windows was already in there...


Could it be the ```
map        (hd0) (hd1)
map        (hd1) (hd0)
```?

Oh, and I am currently logged into my Ubuntu partition... SuperGRUB allows me to do so =)

oh, I see...hmm...what I don't get is how the ubuntu boot got screwed up if all you changed was the windows entry.  

To the best of my knowledge you need those map lines when using grub to boot windows on a non-first hard disk.  It's in the official Gnu Grub manual and on the Grub page.  Maybe there's something wrong with windows partition since grub trying to chainload XP but NTLDR can't be found

---

### Post by logos34 on 2008-01-08
At least super grub allows you to boot into ubuntu, but you shouldn't have to use it because you hardly changed anything.  Try to boot through the grub menu again, but this time on the ubuntu kernel press 'e' to edit and check the root line--should read (hd0,0).  If so 'b' to boot.

---

### Post by Maelgwyn on 2008-01-08
But should both of them be hd, seeing as Win is on sd?

---

### Post by logos34 on 2008-01-08
> **Maelgwyn said:**
> But should both of them be hd, seeing as Win is on sd?

see note post #6 above.

actually you don't need to reboot and do the 'e' key stuff...just check menu.lst again--maybe it got changed accidentally somehow, dunno.  it should still show (hd0,0)

---

### Post by Maelgwyn on 2008-01-08
ah... lol

menu.lst shows

```

title         Windows XP Professional
root         (hd1,0)
map         (hd0) (hd1)
map         (hd1) (hd0)
makeactive
chainloader     +1
```

---

### Post by logos34 on 2008-01-08
no, I meant menu.lst **ubuntu** entries should still show **(hd0,0)**.  That's the XP entry exactly as you edited i, right?

---

### Post by Maelgwyn on 2008-01-08
Just tried to boot WinXP via superGRUB, and here's the error:
```

Booting '!WIN
rootnoverify (hd0,0)
chainloader +1

Error 13: Invalid or unsupported executable format.
```

I tried booting without the CD, but it doesn't even let me get as far as GRUB, it just pops up with the NTLDR is missing message....

---

### Post by Maelgwyn on 2008-01-08
> **logos34 said:**
> no, I meant menu.lst **ubuntu** entries should still show **(hd0,0)**.  That's the XP entry exactly as you edited i, right?


```
## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3ac91ce7-e74d-4524-8cc2-59546718559f ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3ac91ce7-e74d-4524-8cc2-59546718559f ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows XP Professional
root         (hd1,0)
map         (hd0) (hd1)
map         (hd1) (hd0)
makeactive
chainloader     +1
```

---

### Post by logos34 on 2008-01-08
> **Maelgwyn said:**
> Just tried to boot WinXP via superGRUB, and here's the error:
```

Booting '!WIN
rootnoverify (hd0,0)
chainloader +1

Error 13: Invalid or unsupported executable format.
```

I tried booting without the CD, but it doesn't even let me get as far as GRUB, it just pops up with the NTLDR is missing message....

GO into the Bios and change the hard disk boot order so the windows sda is first.  Can you boot into windows directly?

---

### Post by ubutufan on 2008-01-08
Maelgwyn

The message missing NTLDR indicates on of the following (most likely the second)
1. The boot.ini file of XP being corrupted or
2. The XP partition is not Flagged (anymore) as a boot partition

I would recommend that you download GPARTED, burn the iso, boot from it and once on the graphical menu, mark the partition of XP as boot.

Let us know the results

---

### Post by logos34 on 2008-01-08
> **ubutufan said:**
> Maelgwyn

The message missing NTLDR indicates on of the following (most likely the second)
1. The boot.ini file of XP being corrupted or
2. The XP partition is not Flagged (anymore) as a boot partition

I would recommend that you download GPARTED, burn the iso, boot from it and once on the graphical menu, mark the partition of XP as boot.

Let us know the results

yeah, you're right--just noticed the fdisk output in post # 5 is missing the boot flag (*)...But since you can still boot into ubuntu with super grub (unless that's screwed now too!)  it would be faster to do

sudo gparted

then right-click on sda1>manage boot flags

---

### Post by ubutufan on 2008-01-08
There are (rare) occasions that I have witnessed, GParted from within Ubuntu will not change the flag of a partition, especially one of XP. Hence my suggestion to download Gparted. It's a good to tool to have on the side.

---

### Post by Maelgwyn on 2008-01-08
ok, so I've apt-get installed gparted, and both HDDs have the boot flag on...

I'm downloading gparted to burn to disc as we speak, so I'll have a better answer for you in a few minutes ^.^

Thanks everyone for the help so far! =)

---

### Post by Maelgwyn on 2008-01-08
I'm back!

And both HDDs have the boot tag on them....

---

### Post by logos34 on 2008-01-08
can you boot directly into xp by changing the bios boot order, or no?

---

### Post by Maelgwyn on 2008-01-08
short answer? nope. =(

---

### Post by logos34 on 2008-01-08
houston, we have a problem...

seriously though, what on earth happened?  And why did ubuntu stop booting from grub?  It's getting late, so I gotta go. Maybe ubuntufan is right about boot.ini being corrupted.  Some things to consider trying:

--run **fixboot** from the xp install cd recovery console.  And maybe even restore windows bootloader to mbr with **fixbmbr** command.  Then see if you can boot it directly.
--write grub to root partition hda1.  See if that helps. ie,

> sudo grub
> find /boot/grub/stage1
(enter output, e.g. 'hd0,0',in next command)
> root (hd0,0)
> setup **(hd0,0)**
> quit

--reinstall ubuntu.  Doesn't take the long.  (but the updates take a while).  You could back up any pkgs/updates you've installed beforehand, then at least you won't have to download them again.  (/var/cache/apt/archives)

---

### Post by ubutufan on 2008-01-08
I was away for a while.
At this stage I cannot backtrace the changes you have applied to the bootloader.
I suggest the following

Use gutsy livecd. Once up and running go to the xp partition and make a back up of the boot.ini file. Actually rename it into boot.bak
Open the file boot.bak and copy paste in it the following
[boot loader]
timeout=30
default=multi(0)disk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

There should be nothing else in the file. Save it as boot.ini

Exit from ubuntu livecd
Reboot and in the bios setup choose the xp disk to bootup first.

If this does not work then insert the xp disk and follow the instructions given to you. Your XP MBR will reinstall itself and you will be able to boot into windows.

When all that is done, you will not be able to boot into ubuntu. To do that without harming the xp bootloader, I suggest you follow this [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

### Post by Maelgwyn on 2008-01-08
> **ubutufan said:**
> I was away for a while.
At this stage I cannot backtrace the changes you have applied to the bootloader.
I suggest the following

Use gutsy livecd. Once up and running go to the xp partition and make a back up of the boot.ini file. Actually rename it into boot.bak
Open the file boot.bak and copy paste in it the following
[boot loader]
timeout=30
default=multi(0)disk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

There should be nothing else in the file. Save it as boot.ini

Exit from ubuntu livecd
Reboot and in the bios setup choose the xp disk to bootup first.

If this does not work then insert the xp disk and follow the instructions given to you. Your XP MBR will reinstall itself and you will be able to boot into windows.

When all that is done, you will not be able to boot into ubuntu. To do that without harming the xp bootloader, I suggest you follow this [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Rather than booting via the livecd, I just mounted the WinXP partition to have a look at what the boot.ini file currently says, but I can't find it! Where's it located?

Screenshot is the WinXP drive. When I could boot into Windows, this was know as D://, if that's of any help to y'all :)

I truly do appreciate all the effort going into this! ^.^

---

### Post by ubutufan on 2008-01-08
The file boot.ini is located on c:
or
as you mentioned in your case in d:
It is a system hidden file, therefore <show hidden files>
Let me know if you can spot it.

---

### Post by Maelgwyn on 2008-01-08
There's naught there.... >.<

---

### Post by ubutufan on 2008-01-08
I was afraid it would be so. In a nutshell your windows mbr is destroyed. At this stage your only way of recovering this partition is to use the xp disk. For the record boot with it and use the R option to enter recovery mode. The issue fixboot and or fixmbr (most likely in your case the second)
If there is no further damage to the partition you will be able to boot into windows

---

### Post by Maelgwyn on 2008-01-08
SuperGRUB allows to do this as well eh?

---

### Post by ubutufan on 2008-01-09
> **Maelgwyn said:**
> SuperGRUB allows to do this as well eh?

Your windows need-to-boot stuff is not there (judging from your attachment). I don't think supergrub will do the miracle you are looking for. You want to go with the xp disk to recover your windows system.
On another issue, if you are concerned about your windows data, the answer is don't worry.
Ubuntu, even the livecd can read your ntfs partition and your data can be safely stored somewhere else. That will help you in case you cannot make things work and need to proceed with a clean install

---

### Post by Maelgwyn on 2008-01-09
Yeah, so attempting to fix the mbr failed. =( I'm currently using the livecd and have wiped my 30Gb Ubuntu partition, replaced it with FAT32 and am moving everything I can fit across to start from scratch again :confused:

Thanks for all the help anyway guys!:KS

---

