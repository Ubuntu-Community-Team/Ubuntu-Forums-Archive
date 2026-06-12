---
title: "Dual Boot &quot;NTLDR is missing&quot; Win XP Error."
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by outerspacerace on 2008-11-12
I have a dual boot Ubuntu 8.10 64bit/XP machine which was going fine until tonight, when upon attempting to boot into XP I get a "NTLDR is missing, press control-alt-delete to restart" error.

I navigated to my Windows partition and backed up my boot.ini, the contents of which are:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

Is there something in there I can edit so that XP will boot again?

Thanks in advance on this one.

---

### Post by Herman on 2008-11-12
If your partition number or your hard disk number has changed somehow, you might want to edit boot.ini, have you done anything unusual lately that might cause your hard disk or partition number to change?
Have you plugged/unplugged any hard disk(s)?
Have you been working with partition editing software?

If yes to one of the above, then possibly editing boot.ini might help, and here's a link to a great website dedicated to helping people with that problem, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")
You should be able to download an .iso file with NTLDR, NTdetect.com and a generic version of boot.ini, and burn that to a CD which should at least boot your Windows for you.

If your Windows is on a non-first hard disk, it's easier to use a pair of  GRUB's 'map' commands. instead of editing boot.ini. [Chainloading on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") .

Maybe running CHKDSK /R from a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") will help.

To get specific help, you should post a copy of 'sudo fdisk -lu', or a screencap from Gnome Partition Editor , and a copy of the bottom half of your /boot/grub/menu.lst file.


Regards, Herman :)

---

### Post by outerspacerace on 2008-11-12
Hi Herman,

I actually just bookmarked your great site and intended to read it tomorrow when I have more time.

I'll detail the situation as you asked here then too.

Thanks from a fellow Aussie!

---

### Post by psusi on 2008-11-12
Messing with boot.ini isn't going to help since NTLDR is what reads boot.ini, and it is missing.  The most likely cause is that you have more than one NTFS partition, and grub is trying to boot one that does NOT have windows installed on it.

What does sudo fdisk -l say?  And what does your /boot/grub/menu.lst contain?

---

### Post by outerspacerace on 2008-11-12
fdisk -l says:

Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc


Menu.lst says:

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
# kopt=root=UUID=36f68791-365d-412d-adde-39e44fe12a81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=36f68791-365d-412d-adde-39e44fe12a81

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
uuid		36f68791-365d-412d-adde-39e44fe12a81
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=36f68791-365d-412d-adde-39e44fe12a81 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		36f68791-365d-412d-adde-39e44fe12a81
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=36f68791-365d-412d-adde-39e44fe12a81 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		36f68791-365d-412d-adde-39e44fe12a81
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


sudo fdisk -lu says:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x161d161d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    65529134    32764536    7  HPFS/NTFS
/dev/sda2        65529135   156296384    45383625    5  Extended
/dev/sda5        69625710    89160749     9767520   83  Linux
/dev/sda6        65529261    69625709     2048224+  82  Linux swap / Solaris
/dev/sda7        89160813   156296384    33567786   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x101ada18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb971dd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976770143   488385040+   7  HPFS/NTFS


... Basically the system has always detected my disks out of order but with manual partitioning I've had a few versions of ubuntu working fine - this old post of mine elaborates on the problem:

[http://ubuntuforums.org/showthread.php?t=872252](http://ubuntuforums.org/showthread.php?t=872252)

My set up is still the same since then too.

In regards to Herman's questions, I did do a LOT of partitiong/resizing/moving (manually) right before I intsalled 64bit Intrepid, though I am almost 100% certain that since then Windows has been ok.

I remember booting it up to move the last of my pics over to linux and to remove some things like Google Desktop so it ran better. I wonder if somehow the indexing feature of Google desktop caused issues with the disk?

The only other two things that happened since then is that whilst installing the restricted drivers for DVD in Intrepid I had to leave the house and the system continued on it's own, eventually shutting down before I returned.

Also, my girlfriend used my linux account during the day to check her emails but that wouldn't have affected anything, she always shuts it down correctly and never tweaks a thing.

Hope that helps?

---

### Post by caljohnsmith on 2008-11-12
Since Windows XP is on the same drive as Ubuntu, just replace your existing Windows entry in your menu.lst with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
And I should mention, you can modify your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Give that a shot and let us know how it goes. :)

---

### Post by psusi on 2008-11-12
Accessing the raw disks to mess with the partition table is a privileged operation, so you need to prefix fdisk with sudo.

It looks like your grub is trying to boot windows from the second disk.  Did you recently add a new disk to cause this?

---

### Post by outerspacerace on 2008-11-13
No BUT I remembered the last time I booted I had left my flash drive plugged in.

The problem may come from the fact that it had 8.10 on it which I installed on my brother's Eee PC... toally forgot about that one! oops!

Will try the suggestions now, thanks!

---

### Post by outerspacerace on 2008-11-13
Arghhh man I must have been tired when I posted the fdisk results, I actually did sudo it but for some reason pasted in a time whn I didn't - doh!

Anyway here's the output;

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x161d161d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080        9729    45383625    5  Extended
/dev/sda5            4335        5550     9767520   83  Linux
/dev/sda6            4080        4334     2048224+  82  Linux swap / Solaris
/dev/sda7            5551        9729    33567786   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x101ada18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb971dd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      969018   488385040+   7  HPFS/NTFS

---

### Post by outerspacerace on 2008-11-13
Awesome folks, just awesome!

Fixed right away, I'm typing from XP at the moment.

Thanks all round for the wonderful help ;)

BTW do you think all the partitioning caused the problem or rebooting with a distro on a usb drive plugged in?

I'm leaning towards the latter, either way I won't be doing it again.

Cheers.

---

### Post by Herman on 2008-11-13
Is your Windows in hard disk number 1, with Ubuntu? Or is it in one of the other hard disks?

:) I you have Windows XP in your first hard disk, partition number 1 then your boot.ini file is correct and you should do as caljohnsmith said and change your Windows entry in your /boot/grub/menu.lst in Ubuntu to something like:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
The error messages from Windows can be very confusing because sometimes NTLDR really is missing, but most of the time it's not, it's there but Windows can't find it.

If you want to see if NTLDR is really missing or not, do this, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting.
You should be able to see your NTLDR, NTdetect.com and boot.ini, which are the three most important files for Windows XP to boot.
Sometimes, Windows really does delete those files, especially if you install more than one Windows in a computer. Normally the second Windows will turn out to be in a logical partition and it will give up it's boot loader files to the first Windows installation.

Most of the time the error message is caused by the partition number for Windows getting accidentally changed by a hard disk partition editor, and then Windows can't find NTLDR because boot.ini has the old partition number in it.
I know that does not make sense, because as psusi said, it is NTLDR which reads boot.ini, but remember, we are talking about Windows now, and so we should not expect things to be sensible or logical. I cannot explain the stupid error messages, or why Windows likes to frighten and mislead it's paying customers.  I do know from experience that one way to fix that error message is to edit boot.ini if that's what is needed, but in this case I don't think so.
Your boot.ini file looks okay to me, it is very similar to the one I posted for comparison in that web page I already linked you to, so it is correct for a number 1 partition.

---

### Post by Herman on 2008-11-13
> I'm typing from XP at the moment.We must have both posted at about the same time - good! I'm glad you got it fixed. :)
> BTW do you think all the partitioning caused the problem or rebooting with a distro on a usb drive plugged in?

I don't know, it looks like Ubuntu originally set up GRUB to boot your Windows in a second hard disk, I don't know why.

Unplugging  hard disk(s) and plugging it/them in again might cause or changing the hard disk boot priority in your BIOS could have that effect booting.

It should be okay to reboot with a USB drive plugged in, I do that all the time and it doesn't seem to cause any problems in most of my computers. My Asus EeePC does seem to have difficulties when there are other USB flash memory sticks plugged into a hub. I run Ubuntu in my EeePC from a USB flash memory stick, and it likes to be the only one plugged in during boot-up.

---

### Post by psusi on 2008-11-13
What did you do to fix it?  Just unplug the usb stick?  Having the usb stick plugged in could cause this depending on how the bios numbered the disks; the usb stick could have changed the disk number of your windows disk, so grub tried to boot the wrong disk.

---

### Post by outerspacerace on 2008-11-13
Following Caljohnsmith's advice I modified my menu.lst to look like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1

Whereas earlier it looked like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

So I didn't paste his exact code in, as I wanted to have XP show up at boot as "Microsoft Windows XP Home Edition".

If there's anything not quite correct please tell me, though the system is booting into either OS's fine.

Now I might shorten the timeout value too, 10secs is a bit too long.

I used to use Start Up Manager for such tasks but it seems to wreak havoc with nVidia drivers - somehow I always end up with a garbled shutdown screen after using it.

---

### Post by psusi on 2008-11-14
Wait, your Windows installation is on the same disk as your Ubuntu installation?  And always has been?  The only way I can think of for the menu.lst entry to get set up the way it was is if Windows was on /dev/sdb when you installed Ubuntu to /dev/sda.

---

### Post by outerspacerace on 2008-11-14
Yup, Ubuntu and Windows are and have always been on the first 80GB drive together, for every version.

There has always been some weird issue with the installers sometimes not detecting the first drive, or only letting me guided resize the second or third drive for whatever reason (like in the above link to my first ever posts here),

I got around it by manual partitioning and have had no problems since.

P.S. No drives have ever been added since I began dual booting XP/Linux.

---

### Post by thermobee on 2009-11-05
Ok I have a very similar problem. Both Ubuntu and XP are on the same hdd and they also share a 40gb. Everything was working fine even after I installed 9.04 for a couple of days until this morning when I got the ntldr missing message as well. I already tried the solution that you did and no luck. Is it possible that the loader is actually missing? And what can I do? Please help, any advice will be appreciated. ):P

---

### Post by thermobee on 2009-11-05
Oh and I cant repair my XP cause I dont have the CD. Please HALP:p

---

### Post by Herman on 2009-11-05
:D Here's a link  to a website from where you can download a free .iso file to burn to disk, (make a CD from), [How to fix: NTLDR is missing, press any key to restart ]("http://tinyempire.com/notes/ntldrismissing.htm")[U]

[/U]The CD that .iso produces contains a generic version of boot.ini, plus NTdetect.com, NTLDR, so you should be able to boot your Windows XP with it almost no matter what. It will only be a matter of choosing the right boot entry according to the hard disk and partition number your Windows XP is in. You may need to keep experimenting until you find it, but that boot disc will surely boot your Windows XP if it is bootable at all. [U]
[/U]

---

### Post by Herman on 2009-11-05
If you can boot Ubuntu and  [mount]("http://members.iinet.net.au/%7Eherman546/p10.html#Click-Icon_Mounting") your Windows XP file system (partition), you should be able to see your vital Windows XP boot loader files.
They should look something like this, [A Birds's eye view of Windows XP]("http://members.iinet.net.au/%7Eherman546/p6.html#A_Birdss_eye_view_of_Windows_XP").
Take a look around and see if NTLDR, boot.ini, and ntdetect.com are there or if NTLDR really is missing. 
If it's really missing you can copy and paste those files from the CD you just downloaded, back into Windows XP and they should make Windows XP boot unless there's some other problem as well.

Check to make sure the boot flag is on your Windows partition by opening GParted partition editor, if you don't have GParted installed in Ubuntu, you can use your Ubuntu 'Desktop' LiveCD. Set the boot flag in your Windows partition if it isn't already.

While you're in GParted, make a note of what partition number you have Windows XP in please, and if you still need help please post back with a brief description of your partitions.

An easy way to describe your partition information would be to use the 'sudo fdisk -lu' command in Ubuntu and copy the results and paste it to your next post,
```
sudo fdisk -lu 
```

---

### Post by thermobee on 2009-11-05
> **Herman said:**
> If you can boot Ubuntu and  [mount]("http://members.iinet.net.au/%7Eherman546/p10.html#Click-Icon_Mounting") your Windows XP file system (partition), you should be able to see your vital Windows XP boot loader files.
They should look something like this, [A Birds's eye view of Windows XP]("http://members.iinet.net.au/%7Eherman546/p6.html#A_Birdss_eye_view_of_Windows_XP").
Take a look around and see if NTLDR, boot.ini, and ntdetect.com are there or if NTLDR really is missing. 
If it's really missing you can copy and paste those files from the CD you just downloaded, back into Windows XP and they should make Windows XP boot unless there's some other problem as well.

Check to make sure the boot flag is on your Windows partition by opening GParted partition editor, if you don't have GParted installed in Ubuntu, you can use your Ubuntu 'Desktop' LiveCD. Set the boot flag in your Windows partition if it isn't already.

While you're in GParted, make a note of what partition number you have Windows XP in please, and if you still need help please post back with a brief description of your partitions.

An easy way to describe your partition information would be to use the 'sudo fdisk -lu' command in Ubuntu and copy the results and paste it to your next post,
```
sudo fdisk -lu 
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3e4f3e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62203679    31101808+   7  HPFS/NTFS
/dev/sda2        62203680   149902514    43849417+  83  Linux
/dev/sda3       149902515   156296384     3196935   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c5e5c5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    78156224    39078081    5  Extended
/dev/sdb5             126    78156224    39078049+   7  HPFS/NTFS

---

### Post by thermobee on 2009-11-05
Let me follow the bird's eye view procedure and ill get back to you as soon as im done.

---

### Post by thermobee on 2009-11-05
Ok I cant see that Hda1 and I dont know why. Maybe cause its not mounted or something, but I cant find any of the XP files at all.

---

### Post by Herman on 2009-11-07
:???: I don't know how I can help you until you can get your file system mounted.
Do you need help with how to get your file system mounted or do you know how to do that and you have some other problem that's making it impossible to mount?

It could be that it needs a file system check. That's the most common reason for a file system to be impossible to mount.

The file system inside the partition consists of 'metadata' ('data about data', such as what sectors in the hard disk your various files and directories are stored in). The file system can be corrupted by physical damage to the hard disk's surface, such as dropping a laptop or external USB drive, especially when the disk is still spinning. In that case the damage may be permanent, but in some cases it's possible for an operating system to survive it. A file system can also be damaged by a sudden shutdown, such as when there's a power blackout or somebody pulls out the extension cord or something like that. In that kind of situation the damage is usually minor and can normally be fixed with a file system check or two. Other times it could be that the hard drive is getting old and worn out and dying from natural causes.

Does it show up in GParted as an NTFS file system with a yellow warning triangle with an exclamation ! mark in it? If so it's not too bad. It's worse when it shows up with a black rectangle around it and the file system can't be recognized at all.

To fix an NTFS file system you need a Windows CD, so you might need to go begging to borrow one from a friend or relative, it's not to install with, it's just to do a small repair. One of the problems with proprietary operating systems is the owners of such disks tend to be rather selfish and suspicious of anyone who needs to borrow one as if they think you're going to steal their operating system or something, but you need one of those disks possibly for overnight to fix your NTFS file system with. 
When you are eventually able to get hold of a Windows XP install CD and boot into the [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), I recommend the CHKDSK /R command (on your C:/ drive). It will take a long time but it will do a much better job than just the quick CHKDSK /F. You might even need to run it several times.

Some Windows installations contains an i386 folder and if so you can make your own Windows installation CD using Ubuntu. It's not an easy job for a beginners though, it requires a few linux commands and besides that, it requires a working Windows installation as well. You need to be able to mount and boot Windows to do it, so you will still need to borrow a CD to fix your Windows XP first. It would mean you won't need to go borrow a CD the next time you have problems though.

Do you have any access to a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") from a 'Recovery Partition' in your computer which the manufacturer gave you instead of a CD? If so you might be able to use that to CHKDSK your Windows.

---

