---
title: "triple boot XPH/XPP/ubuntu"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by magnethead on 2007-06-17
I guess i'm running off into uncharted territory. I have a 145 GB SATA hard drive with windows XP home on it (via dell), a 320 GB IDE hard drive with XP pro on it, and a 6 (six) GB IDE hard drive that i am trying to put linux on. Also i have my jump drive plugged in currently.

can somebody please help me and point me in a good direction?

ok, in leu of all the text i had put here (9 long edits), i completely blew out the hard drive again and started fresh yet again. Still no grub prompt, so i installed grub manually. Additionally, i gave ubuntu all one partition. no swap (1.5 gigs of RAM), no home, no share, just 6.0 gig's of ext3 formatted root partition. 

now, /boot/grub/stage1 is located (found) in HD1,0 and that's it. I assume that is the 6 gig drive.

In the "filesystem" drive, i have /boot/grub, but only one file, "device.map". on the "6.0 GB volume:disk" drive, it has /boot/grub and it is full. Is there supposed to be a descepancy there?

Now how am to perform what this page ([http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)) says to do, at the point i am at currently?

(hd0)	/dev/sdb (6 GB IDE EXT3)
(hd1)	/dev/sda (320 GB IDE NTFS)
(hd2)	/dev/sdc (145 GB SATA NTFS)
(hd3)	/dev/sdd (256 MB USB FAT)

booting by override to secondary slave, the window just sat there with no HDD activity. Booting off a floppy, the screen sat with GRUB at the top left corner for several minutes before i powered down. Boot override to jump drive gave a code 15.

If somebody could even get me to a point that it would boot on it's own on an override that would be great. Being as i can't get into it at all.

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         784     6297448+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           4       32098+  de  Dell Utility
/dev/sdc2   *           5       19057   153043222+   7  HPFS/NTFS
/dev/sdc3           19058       19457     3213000   db  CP/M / CTOS / ...

Disk /dev/sdd: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)


> 
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=9f59d6dd-b777-4290-bff0-7f05d6f54990 ro

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9f59d6dd-b777-4290-bff0-7f05d6f54990 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title		Windows XP Home (loader)
root		(hd2,1)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Pro (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


If somebody could even get me to a point that it would boot on it's own on an override that would be great. Being as i can't get into it at all currently.

---

### Post by sickpuppet on 2007-06-18
Hello magnethead - 

Need a bit more info to help you out...

Are you using the Alternate Ubuntu install CD? Which of your drives contains the MBR (master boot record) from which windows boots? What boot manager do you use to choose between the different versions of Windows currently?

regards
Ben

---

### Post by magnethead on 2007-06-18
All i have is the Live CD i downloaded from the website (iso file). the 145 GB drive contains the master boot.ini file, with which both windows read to bring up the OS choices menu.

---

### Post by magnethead on 2007-06-19
Being assisted by ckempo over IM. To save others from dealing with this for 48-72 hours as i have so far, here is a log of what has taken place:

[03:56] ckempo: I think sick puppet is asking about using the alternate disk because that used to be the only way to get grub installed anywhere other than the MBR of your first disk. But you can install it where you want now, using the live cd, there is a prompt towards the end of the install process... think it's labelled "advanced" (can't recall exactly) but it allows you to specify where to install. So that's cool, you've got the stuff you need on disk
[03:56] ckempo: Shall have a closer read over the details
[03:57] magnethead: yea if i click the advanced button it'll ask where  want it installed, it defaults to hd0 (the linux disk)
[03:58] ckempo: yeah, you've found it then. let me go check something, brb
[03:59] magnethead: ok..meanwhile a topic i read said to install grub to floppy, then extract the floppy contents into a lnx file...might you be able to elaborate on that in relation to where i am now?
[04:00] ckempo: christ! haven't used a floppy in years, no idea about going that route, sorry!
[04:00] magnethead: lol i know..everythig is jump drive now
[04:00] magnethead: heres the topic (Link: [http://ubuntuforums.org/showthread.php?t=56723)(Link:](http://ubuntuforums.org/showthread.php?t=56723)(Link:) [http://ubuntuforums.org/showthread.php?t=56723)http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)http://ubuntuforums.org/showthread.php?t=56723)
[04:01] magnethead: i didnt know a full directory could be compacted to 1 file...if it even can
[04:04] magnethead: so i assume i re-install it, tell it to put grub on sdd (jump drive), restart, boot from jump drive, hope it works, then copy the contents of the jump drive into a .lnx file
[04:04] ckempo: kinda
[04:04] ckempo: I'd try it another way, just looking for confirmation it'll work
[04:06] ckempo: forgetting ubuntu for a mo
[04:07] ckempo: when you boot
[04:07] ckempo: you see the Windows bootloader, prompting you to choose XPH or XPP, correct?
[04:07] magnethead: yes
[04:07] ckempo: and each OS is physically on a separate disk?
[04:07] magnethead: yes
[04:07] ckempo: so what does your current boot.ini look like?
[04:08] magnethead: [boot loader] 
 timeout=3 
 default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 [operating systems] 
 multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noguiboot 
 multi(0)disk(0)rdisk(1)partition(1)\WINPRO="Microsoft Windows XP Professional" /fastdetect /noguiboot /NoExecute=OptIn
[04:10] ckempo: you get that file?

magnethead: k
magnethead: what is the file?
ckempo: get this: [http://www.winimage.com/bootpa26.zip](http://www.winimage.com/bootpa26.zip)
magnethead: ok it's DLing
ckempo: I think the easier way to achieve what youwant, is to install Linux on your 6GB drive, with Grub loaded to the MBR of that drive
ckempo: then, using the bootpart util, create a copy of that disk's MBR
ckempo: and use an entry in boot.ini to call that
ckempo: I do this on my laptop
ckempo: and my desktop at home
ckempo: infact
magnethead: well the main restriction that i have is for some *cough*dell*cough* reason, i can't change my boot drive in bios..it's either flooy, cD, or drive C
magnethead: oh ok
ckempo: infact all machines I use that dual boot and it doesn't fail
ckempo: because you boot from C:\ - but then use the bootloader on C:\ to call another drive
magnethead: ok
magnethead: so redo linux, put grub on hd0 (linux), then create a copy of the MBR?
ckempo: well just before you go to all the hassle
ckempo: drop to a cmd prompt
ckempo: and run the bootpart.exe command
magnethead: in windows or linux
ckempo: windows
magnethead: bootpart.exe is not recognized
magnethead: and it's not in the windows32 bolter either
ckempo: sorry
ckempo: one you download that zipfile
ckempo: extract it
magnethead: oh ok
magnethead: to sys32 folder?
ckempo: then in your cmd window, do :
cd "C:\downloads\bootpa2\" (or wherever you extracted it)
bootpart

and see what you get
magnethead: ok
magnethead: ok got that report up
ckempo: so... does it list partitions from more than one disk or not?
magnethead: yes
ckempo: great stuff. what do you see then?
magnethead: 145 disk first, then 320, then 6, then jump drive
ckempo: I get (on my work machine, only one disk and one partition) this:

Physical number of disk 0 : 9c879c87
0 : C: type=7  (HPFS/NTFS), size= 78140128 KB, Lba Pos=63
magnethead: It shows everything on my system
magnethead: NTFS drives are type 7, linux drive is type 83, jump drive is type 4
ckempo: the linux drive then - is that numbered as 3/4/what?
ckempo: like mine is numbered 0
magnethead: linux is listed as 4
magnethead: 0 is dell utility, 1 is XPH, 2 is Dellrestore, 3 is XPP, 4 is linux, 5 is jump drive
ckempo: right then.
ckempo: nearly there
ckempo: try this comand:

bootpart 4 C:\Linux.bin "Ubuntu Linux"
magnethead: yay
ckempo: you should now see a Linux.bin file in C:\
ckempo: and your boot.ini has a new entry?
magnethead: linux.bin written, boot.ini updated
ckempo: ok.
ckempo: now
magnethead: yes i do see it
ckempo: this may not work yet, because all it's done is copy what it THINKS is the bootloader from the 6gb drive
ckempo: if grub wasn't installed correctly, then that linux.bin file is a dud.
ckempo: so to test it
magnethead: ok
magnethead: be back in 2ish-3 minutes then
reboot, and select the Linux entry when prompted. If grub appears and boots linux, you're sorted. if there's an error, reboot to windows and come back and let me know.  Basically, you need to arrive in a position where grub is on the mbr of the 6gb drive. when it is so, correctly, then you can run that bootpart command again to copy the data into the .bin ile

[04:36] magnethead: no go, said cannot boot from hard disk, instert systemdisk and press enter
[04:37] ckempo: ok. something isn't right with your setup then. I'd go for a complete re-install then
[04:37] ckempo: make sure when it comes to partitioning it that you do it manually
[04:38] ckempo: and can see that the bootable flag is deffo ON
[04:38] magnethead: now where in the window is the bootable flag
[04:38] magnethead: i've lookd for it but never sen it
[04:39] magnethead: (sorry for my typing..i'm getting tires..it's 4:30 AM over here stateside)
[04:39] magnethead: tired*
[04:40] ckempo: hmm. it used to appear as a single "B" char in the column
[04:40] magnethead: for partitioning, i don't need a swap file is i have 1.5 GB of RAM, and i can really care less about a share folder..so do i just partition it full disk size with the mount path of "/"?
[04:41] ckempo: If you want. Although you can't hibernate/suspend without a swap partition
[04:41] magnethead: dont use those functions either
[04:42] magnethead: my computers either all on, all off, or screen saver
[04:42] ckempo: ok that's cool, one partition then
[04:42] magnethead: here's what the manager looks like when i'm dealing with it [http://img.photobucket.com/albums/v295/magnethead/Screenshot-2.jpg](http://img.photobucket.com/albums/v295/magnethead/Screenshot-2.jpg)
[04:43] magnethead: that having been taken several nights ago
[04:45] ckempo: hmm. no bootable flag. it DOES look different to the alternate disk after all
[04:45] ckempo: no problem
[04:47] magnethead: "workaround?
[04:51] ckempo: when you come to reinstall linux again - just do the "use entire disk" option, take whatever it defaults to (even if it gives you swap I guess, keep it as is) and go through the install as normal. Check check and re-check that it is installing onto the 6gb disk... then have it install grub to that  disks' MBR.... then into windows again, repeat the bootpart command I sent you (pull it from this log) and retry.  
[04:51] ckempo: Can't think of any reason why that wouldn't work.
[04:52] magnethead: ok, will do
[04:52] magnethead: like i said it's 4:45 AM now, thanks for helping me, i'll do that tomorrow and get back with you

---

### Post by ckempo on 2007-06-19
<NoteToSelf>
I really should write up a guide to using the Windows bootloader to call grub etc, using bootpart.exe, that kind of stuff... would be great on the Wiki.
</NoteToSelf>

---

### Post by magnethead on 2007-06-19
ok i did a boot override, i get the grub prompt now, but when i choose a linux option it says "Cannot mount the selected partition"

---

### Post by magnethead on 2007-06-19
ok when it tries to run linux.bin, it says 

making new partition
bootsector by (some name)
Cannot load from harddisk
insert systemdisk and press enter

---

### Post by ckempo on 2007-06-20
If the drives are easily removable, and you're comfortable doing this, I'd suggest you remove all drives bar the one you want Linux on, set that drive as a master etc, install it (again) and make sure that before you try changing the boot setup that you can get into Linux without any more issues.  

Once you're in a position where you can happily boot Linux without issues, re-insert the other drives and reset the boot.ini configuration on your main Windows drive as before (using bootpart to generate yourself a Linux.bin file and have it update the file for you).

In theory, grub will install happily when there is only one drive present, and when bootpart takes a copy to create the file for Windows to use, then (again, in theory) everything it needs will be configured correctly and grub should launch, then Linux loads.

If that doesn't work, I'm out of ideas, short of maybe trying to install grub to your current C:\ and using that as the bootloader for all three OSes, but I'm not sure how you'll get on doing this.

Hopefully someone else on here will see what we're trying to do and offer some more suggestions? I'll have another look around in the meantime and see what I find, someone, somewhere must have done this before!

---

### Post by magnethead on 2007-06-20
ok will do that..that was my last idea too but didnt know if grub would like it.

---

### Post by magnethead on 2007-06-20
step 1 of 2 done. 

I'm now running on full ubuntu off hard drive.

---

### Post by magnethead on 2007-11-25
Been a long time, i know, but I just got a 40 GB IDE drive, and i removed the 6 GB drive when i got my new computer (now a complete custom, no more dell BS). Found the liveCD, and i'm now going back through the process. Good thing the forums are still up and i posted these logs!:guitar:

---

