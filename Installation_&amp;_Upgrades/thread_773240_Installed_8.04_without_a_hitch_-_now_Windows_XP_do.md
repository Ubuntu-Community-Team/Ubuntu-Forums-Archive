---
title: "Installed 8.04 without a hitch - now Windows XP does not boot. Help?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by pitscar on 2008-04-28
Hey guys,

Please help me troubleshoot. I'm new to ubuntu and was able to install 8.04 without any hassles or troubles at all. However, at the grub dual boot loader, trying to launch Windows XP now does next to nothing - once selected, "Starting up......" appears, with no activity and the PC just sits there.

Any help getting windows working again would be great!

Here's the sudo fdisk -l:

> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf235746a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18987   152513046    7  HPFS/NTFS
/dev/sda2           18988       24321    42845355    5  Extended
/dev/sda5           18988       24097    41046043+  83  Linux
/dev/sda6           24098       24321     1799248+  82  Linux swap / Solaris


---

### Post by pitscar on 2008-04-28
I'm really finding this strange!

Here's what I get from **gksudo gedit /boot/grub/menu.lst**:

"# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=cf711757-5b74-4198-92c8-f98daeb18e5f ro

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cf711757-5b74-4198-92c8-f98daeb18e5f ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cf711757-5b74-4198-92c8-f98daeb18e5f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1"

********************************** end menu.lst

I'm not a Linux expert, but to me it doesn't look like the grub menu item for Windows XP is pointing to the correct location. . .

Please, any help at all, even just to say that either you haven't heard of this or that you have and I'm facked :) thanks.

---

### Post by Pumalite on 2008-04-28
I looked at your fdisk and menu.lst and they are correct. The only thing I could suggest is to change 'root' to 'rootnoverify' in the Windows entry, but I'm not sure it will change things much.

---

### Post by pitscar on 2008-04-28
Thanks for the help, but unfortunately that did not do anything, like you thought.

I'm not sure if the entire file structure has been changed now, but is it possible to format the current partition that ubuntu is installed to and leave it wiped, and then have windows boot up by default off the other partion when restarting the computer?

---

### Post by Pumalite on 2008-04-29
Super Grub can fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by pitscar on 2008-04-29
Awesome! Thanks - I will update if it helped.

It's just too bad I read this this early in the day... now I have to wait forever to get home

---

### Post by Rallg on 2008-04-29
If you think that (hd0,0) is the wrong location for XP, then just change it on menu.lst. It won't hurt. The worst that will happen is that you still won't boot to XP.

I'm not enough of a guru to know whether you have dmraid (whatever that is), but if so, try removing savedefault from the boot instructions for XP. Again, the worst that will happen is that you still won't boot XP.

Finally, do you have copies of Grub lurking in several places? On XP, it is possible to use the Windows native bootloader to launch Grub (this is not easy on Vista). Could it be that you have an old Grub sitting in the XP partition, fighting with a recently installed Grub elsewhere?

---

### Post by pitscar on 2008-04-29
> **Rallg said:**
> If you think that (hd0,0) is the wrong location for XP, then just change it on menu.lst. It won't hurt. The worst that will happen is that you still won't boot to XP.

I'm not enough of a guru to know whether you have dmraid (whatever that is), but if so, try removing savedefault from the boot instructions for XP. Again, the worst that will happen is that you still won't boot XP.

Finally, do you have copies of Grub lurking in several places? On XP, it is possible to use the Windows native bootloader to launch Grub (this is not easy on Vista). Could it be that you have an old Grub sitting in the XP partition, fighting with a recently installed Grub elsewhere?

... I think this might be possible. I attempted an install from within Windows, but error'd out due to lack of drivespace and canceled. However, it may have put some files in there.

I'm not sure how I would go about locating it though. I can remount my C drive within linux I suppose and starting going through folders, but it would help to know where an install from within Windows dumps its files.

---

### Post by Pumalite on 2008-04-29
Grub is installed to the MBR: the first 512 bytes of your HDD.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Rallg on 2008-04-29
Clarification: The entirety of Grub is NOT installed to the first 512 bytes of the MBR. Rather, the MBR contains pointers to where the rest of the bootloader (whatever it is) may be found.

If a system comes with XP, it is possible to transfer control to Grub (as ordinary files, not in the MBR) from XP's own boot sequence, without modifying the MBR from its original. In Vista, you can't (grrrr). You can also put Grub4DOS on an external device (such as USB stick) without modifying your MBR.

You can have several copies of Grub in different places. But if you do, then the boot sequence needs to know which one to use, and exactly where to find it. It determines this from the MBR (or from the boot record in your external media, if that's what you are using).

However, if your only means of installing Grub is via the Ubuntu installation CD (or any Linux, to my knowledge), it will probably modify your MBR so that it points to wherever Grub is currently being installed. The other methods, which do not modify the MBR, are done using a separate technology.

My point is that it is indeed possible to have conflicting Grub installers in different places, containing the parts of Grub that are invoked after the MBR. Only one of them will be picked out during boot. If it's the wrong one, or if it contains obsolete information in its menu.lst, you are hosed until the situation is straightened out.

---

### Post by Pumalite on 2008-04-29
That would result in an error message which I haven't seen so far.

---

### Post by xzero1 on 2008-04-29
Be very careful when messing with your MBR since it contains your current partition tables! Use non-destructive methods first. Try super grub to try to boot directly from the partition. If you can boot with super grub then there is a problem with menu.lst. If that fails create an ntldr boot cd which will boot xp directly from the cd.

For super grub see:
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

For ntldr see:
[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm]("http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm")

---

### Post by xzero1 on 2008-04-29
> Clarification: The entirety of Grub is NOT installed to the first 512 bytes of the MBR. Rather, the MBR contains pointers to where the rest of the bootloader (whatever it is) may be found.

If grub has been installed then "whatever it is" *is* grub. So grub inserts itself before the xp loader and can chainload xp or boot to another os.

---

### Post by pitscar on 2008-04-29
Well, unfortunately I've been home and still not having any success.

I've tried booting with Super GRUB Disk, but to no avail. I've tried pretty much every option available but can not boot Windows XP.

I then just cycled through hd0,0 - hd0,5 with no luck.

Ive remounted my main C drive and I can see what I believe are the critical boot files for Windows (boot.ini, ntldr, etc) - see attached pic.

I'm entertaining all ideas now. Maybe its best to take the drive in and get everything off of it... but I'd rather not do that.

Still, taxes are due tomorrow... :eek:

---

### Post by Pumalite on 2008-04-30
It looks like a corrupted filesystem in Windows. Look for the missing file and add it. Maybe you can take it from a friend.

---

### Post by xzero1 on 2008-04-30
Did you try the ntldr boot disk I mentioned above?

---

### Post by pitscar on 2008-04-30
I've tried, but even that is making me feel useless. Didn't run under ubuntu, so I ran it under wine and it errors out - its an extractable executable, which can not be extracted to a location of your choice (ie. my desktop, or a CD) - instead demanding a floppy and, my guess, the A:\ (the thing is from 2002, so who knows) drive. If you know how I could go about using that tool it would be great.

---

### Post by frodon on 2008-04-30
I was thinking about your issue pitscar, and considering that you menu.lst is fine i'm thinking that the install process may have not installed GRUB directly in the disk MBR which is fine but can create some issues when dual booting.

This may not be the case, anyway one painless and safe thing to do would be for you to boot your liveCD again and reinstall GRUB on the MBR, detailled instruction there :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

### Post by roypk on 2008-04-30
You can try using Windows XP recovery console and fixmbr to restore the MBR.  If XP still doesn't boot then there may be errors on the XP partition.  I had both screwed up MBR and errors on the XP partition when I tried installing 7.10.  There are many utilities that can fix the errors.  I got PartitionMagic(DOS) from a friend and it loaded some kind of DOS driver for my SATA drives.  After the errors were fixed, Win XP booted up normally again.  You may want to look at the following sites for more information. 
[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm) 
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

HTH

Best regards,
Roy

---

### Post by xzero1 on 2008-04-30
> I've tried, but even that is making me feel useless. Didn't run under ubuntu, so I ran it under wine and it errors out - its an extractable executable, which can not be extracted to a location of your choice (ie. my desktop, or a CD) - instead demanding a floppy and, my guess, the A:\ (the thing is from 2002, so who knows) drive. If you know how I could go about using that tool it would be great.

You create an NTLDR boot disk that you burn to a cd and boot your computer to xp independently of Ubuntu. See the website again. The idea is to find out whats wrong with your system before writing over anything.

---

### Post by pitscar on 2008-04-30
> **xzero1 said:**
> You create an NTLDR boot disk that you burn to a cd and boot your computer to xp independently of Ubuntu. See the website again. The idea is to find out whats wrong with your system before writing over anything.

I understood that - however, creating that CD is the problem. A step by step would be nice - the executable on the site will not extract for me, unless I'm supposed to burn it directly to CD as it is (fixntldr.exe) which Im sure is not the case.

Others, thanks for the help. Again, I will update once I get home and have a change to try everything out. Some interesting reads out there.

---

### Post by xzero1 on 2008-04-30
There is a version "fixntldriso.zip" that is meant to be burnt to a cdr. Do you know how to burn an iso image? Try this updated link and read under _Make a NTLDR boot disk to get back into Windows_. I once had a similar problem caused by a grub install and at least I was able to boot to xp with that cdr. Later, I was able to fix the problem and didn't loose anything -- but it wasn't easy.

---

### Post by pitscar on 2008-04-30
> **xzero1 said:**
> There is a version "fixntldriso.zip" that is meant to be burnt to a cdr. Do you know how to burn an iso image? Try this updated link and read under _Make a NTLDR boot disk to get back into Windows_. I once had a similar problem caused by a grub install and at least I was able to boot to xp with that cdr. Later, I was able to fix the problem and didn't loose anything -- but it wasn't easy.

:redface: Sorry for taking offence initially. I completely overlooked the CD link and just saw the other executable file. Found the iso though.

And - I'm now typing from Windows XP!

So it looks like my MBR is screwed. I brought home the NTLDR, boot.ini, and NTDETECT.com from my work PC, but it's XP Pro and not XP Home like I'm running at home here. I think I'll grab someone else's HOME files, replace them all, and see if it works.

So, thank you to everyone who has helped me in this thread! Now I at least can get some stuff done, and it's only a CD insert away.

I truly appreciate everyone's input, and I've used all of it. Thanks to all :)

EDIT - in case it is not clear, the fixntldriso.zip file was what fixed my boot problems.

---

### Post by frodon on 2008-05-01
@pitscar, could you detail step by step how you solved your issue, there're other users with similar issues on the forum so this would greatly help them especially those who are new to ubuntu.

---

### Post by Eddie Wilson on 2008-05-01
The problem with my dual boot after I installed 8.04 is a blank screen when I try to boot into Xp. I can boot into Xp if I use the SuperGrub cd and Xp works fine. My menu.lst also looks good. I've been using Ubuntu for several years and this is the first time I've had this problem. Very strange. If it wasn't for the ton of games I own and my grandchildren I wouldn't worry about it because I use Ubuntu for everything else. Will try to redo grub per the earlier post and see what happens. I will let everyone know how it works out.

Eddie

---

### Post by pitscar on 2008-05-01
> **frodon said:**
> @pitscar, could you detail step by step how you solved your issue, there're other users with similar issues on the forum so this would greatly help them especially those who are new to ubuntu.

Definitely! I intend to do that, but it will not be until tomorrow. I'll edit this post with every step I took for future help.

---

### Post by xzero1 on 2008-05-01
A possible complete solution? 
In my case, the problem was completely solved; but that was about a year ago, when I installed my first Linux, Feisty Fawn. The issue seems to be Grub and particular hardware. My guess is that grub sometimes has problems with older MBRS that were initially created before xp was patched to accomodate larger disks.

But the fix, if it works is simple. One only needs to change the number of Heads from ( in my case 16) to 255. First, determine if you might have this problem. If editing menu.lst, supergrub and all other methods fail, *and* you can boot using the NTLDR boot disk described elsewhere in this thread proceed as follows:

Download PTedit32.exe
[http://www.geocities.com/thestarman3/tool/FreeTools.html](http://www.geocities.com/thestarman3/tool/FreeTools.html) (Bottom of page) I would virus check it too.


[ATTACH]68387[/ATTACH]
Select hard disk disk 1 and row 1.
Now click the Boot Record button at the bottom.

If the number of heads is not 255 (I had 16) this *might* work for you.
**Warning:** You are about to modify the master boot record, do not change anything else. I strongly suggest you make a backup of your MBR before trying this. Use at your own risk!
 
All that is required is to change the number of heads to 255, click the write button close the program and reboot.

Should you try it? Its up to you.

---

