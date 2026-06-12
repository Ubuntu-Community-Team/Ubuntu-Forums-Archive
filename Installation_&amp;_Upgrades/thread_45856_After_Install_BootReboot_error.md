---
title: "After Install Boot/Reboot error"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by ano1 on 2005-07-01
I just installed ubuntu. However when it goes to boot from my HD it thinks for 2 seconds and reboots. I originally though it might be a HD error so before my install I ran mke2fs and found no errors. I am using the LiveCD to access the system at the moment, so how do I fix this? Could it be a grub issue? If so how do I mount my HD (HDE) from the liveCD so I can change files on it? I tired mounting it myself and am told: mount: can't find /dev/hde1 in /etc/fstab or /etc/mtab . Thanks for all the help, it is greatly appreciated.

---

### Post by thagame on 2005-07-01
can you paste your /etc/fstab file. it would help to see if maybe its just a typo. and also what are your partitions that are being used. eg: mine is hda2 for ubuntu and hda5 for swap.

---

### Post by ano1 on 2005-07-01
Here is my /etc/fstab:

/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hde5 swap swap defaults 0 0


HDE1 is ext3 HDE2 is extended and HDE5 is linux-swap. I went with the default settings form the install cd.

I was fianlly albe to mount HDE1 and looked at /boot/grubmenu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hde1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

and Device.map:

(hd0)	/dev/hde

Hope that helps someone tell me whats up.

---

### Post by P3PP3 on 2005-07-02
Ive got another problem that can fit to the topic,
I just got my Ubuntu-cd and installed it.
Now I cant run it!
WHen I start up I come to the login process, then I get smething like this
You have mail
jan@jan~$:
then what?! Ive tried startx and all the stuff ppl have told me, please help!
I am totally new to this, answer the best you can thanks.

---

### Post by mingus on 2005-07-02
[QUOTE=ano1]I just installed ubuntu. However when it goes to boot from my HD it thinks for 2 seconds and reboots. I originally though it might be a HD error so before my install I ran mke2fs and found no errors. I am using the LiveCD to access the system at the moment, so how do I fix this? Could it be a grub issue? If so how do I mount my HD (HDE) from the liveCD so I can change files on it? I tired mounting it myself and am told: mount: can't find /dev/hde1 in /etc/fstab or /etc/mtab . Thanks for all the help, it is greatly appreciated.[/QUOTE]

this will tell you how to get in with the live-CD and how to reinstall grub
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

and here is the vanilla entry for fstab
/dev/hde1  /   ext3  defaults,errors=remount-ro 0 1

---

### Post by ano1 on 2005-07-03
[QUOTE=mingus]this will tell you how to get in with the live-CD and how to reinstall grub
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

and here is the vanilla entry for fstab
/dev/hde1  /   ext3  defaults,errors=remount-ro 0 1[/QUOTE]


Hi,

I have done all that was suggested and still am not able to boot to my HD. I have also re-formated and re-installed ubuntu. My fstab is now:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

My computer does not even get to a GRUB menu. What would that suggest? Software error? or possibly Hardware issue? 

my menu.lst is: 
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hde1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Does that look correct to you? Thanks for all the help. Hopefully, thanks to you all, I will soon be able to fully use my computer again.

---

### Post by mingus on 2005-07-03
The drive you are installing on is hde - which means that something else is in front of it.  Is this an IDE drive?  Which controller and channel is it connected to?

What is the boot sequence setup in the BIOS?  If your BIOS supports booting from multiple hard drive devices, what is their priority?

In the following HowTo . . .

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

perform the steps under "Preparing Your Work Environment".  Be sure you chroot on the mounted partition.  Then in a terminal do this (which is a bit different than on this webpage):

#grub
grub> device (hd0) /dev/hde
grub> root (hd0)
grub> setup (hd0)
grub> quit

After you enter the root command, you should get a message back indicating a filesystem found.  After you enter the setup command you should see 4 or 5 lines to the effect ("stage1 . . . found?  yes", "embedded . . . yes", etc.).

Reboot.  Post back the result.

---

### Post by ano1 on 2005-07-03
[QUOTE=mingus]The drive you are installing on is hde - which means that something else is in front of it.  Is this an IDE drive?  Which controller and channel is it connected to?

What is the boot sequence setup in the BIOS?  If your BIOS supports booting from multiple hard drive devices, what is their priority?

In the following HowTo . . .

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

perform the steps under "Preparing Your Work Environment".  Be sure you chroot on the mounted partition.  Then in a terminal do this (which is a bit different than on this webpage):

#grub
grub> device (hd0) /dev/hde
grub> root (hd0)
grub> setup (hd0)
grub> quit

After you enter the root command, you should get a message back indicating a filesystem found.  After you enter the setup command you should see 4 or 5 lines to the effect ("stage1 . . . found?  yes", "embedded . . . yes", etc.).

Reboot.  Post back the result.[/QUOTE]

Hi,
I  am using an 120GB IDE HD it is connected via a raid controller on the motherboard. I usualy have 2 HDs installed but have removed the 2nd (a drive I have important files backed up on). My bios is set to boot the floppy, then CD then HD. Here is how the drive is setup:

Disk /dev/hde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       14405   115708131   83  Linux
/dev/hde2           14406       14593     1510110    5  Extended
/dev/hde5           14406       14593     1510078+  82  Linux swap / Solaris


I did what was said in that tutorial. I did as you instructed and this is what happened:

grub> device (hd0) /dev/hde
grub> root (hd0)
 Filesystem type unknown, using whole disk
grub> setup (hd0)
Error 17: Cannot mount selected partition


By the way I have also tried Recovering GRUB Automatically and this happened:

root:/ # /sbin/grub-install /dev/hde
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hde



Hope this helps you better understand my computer and the problem. Please let me know if you need more info. Thanks for the help.

---

### Post by mingus on 2005-07-04
[I]grub> device (hd0) /dev/hde
grub> root (hd0)
 Filesystem type unknown, using whole disk
grub> setup (hd0)
Error 17: Cannot mount selected partition[/I]

Darn it, my error!  Do the above again, but with root (hd0,0), so:
device (hd0) /dev/hde
root (hd0,0)
setup (hd0)
quit

then put a clean formatted floppy in the drive and run grub again
#grub
device (fd0) /dev/fd0
root (hd0,0)
setup (fd0)
quit

This should write grub to the floppy.  Now try to boot again.  If the boot fails from HDD, try it from the floppy.

*I  am using an 120GB IDE HD it is connected via a raid controller on the motherboard . . . My bios is set to boot the floppy, then CD then HD.*

Are you sure you can boot from the RAID controller?  Are you sure that in the BIOS HD boot priority it is set to boot from this controller and not the IDE drive?  If yes to both, do you have the option of using this as a straight IDE controller, and not RAID?

If you can boot from the floppy but not the HDD, and the BIOS is all set up correctly, the issue may be recognizing the RAID controller - did you have to install a driver before under W$ for this controller to work?  During boot do you see the BIOS loading a driver for this controller?

---

### Post by ano1 on 2005-07-05
Hello,

Thank you for all your help. I finally see a light at the end of this computer tunnel.

[QUOTE=mingus]
Darn it, my error!  Do the above again, but with root (hd0,0), so:
device (hd0) /dev/hde
root (hd0,0)
setup (hd0)
quit
[/QUOTE]
I did this but was still unable to boot to the HD.
[QUOTE=mingus]
then put a clean formatted floppy in the drive and run grub again
#grub
device (fd0) /dev/fd0
root (hd0,0)
setup (fd0)
quit

This should write grub to the floppy.  Now try to boot again.  If the boot fails from HDD, try it from the floppy.
[/QUOTE]
Hurray, I was finally able to boot to my HD and finnish my Ubuntu Install. The issue now stands that I can boot to my HD only when the GRUB boot disk is in.

[QUOTE=mingus]
Are you sure you can boot from the RAID controller?  Are you sure that in the BIOS HD boot priority it is set to boot from this controller and not the IDE drive?  If yes to both, do you have the option of using this as a straight IDE controller, and not RAID?
[/QUOTE]
I am pretty sure my BIOS setting should be properly set up. Prior to this Ubuntu install I had a M$ XP/Suse dual boot that was working well. I had recenty decided to upgrade my OS(s). So after I formatted the drive I chose to install Ubuntu, and experienced the problems we are now fixing. I also do not think I have an option of using it at a straight IDE controller but will look into that.

[QUOTE=mingus]
If you can boot from the floppy but not the HDD, and the BIOS is all set up correctly, the issue may be recognizing the RAID controller - did you have to install a driver before under W$ for this controller to work?  During boot do you see the BIOS loading a driver for this controller?
[/QUOTE]
I think you are correct that the error might be in detecting the raid controller. I am using an Asus KR7A-133R Motherboard and in order to get it to work for M$ I had to install a driver. Is there a way to use this with Ubuntu? I have only been able to locate Win Drivers for this. 

I am fine for now having to use the boot floppy but would love to learn how to set up my system so I do not need to use it in the future. Once again thanks a million for all your assistace.

---

### Post by mingus on 2005-07-05
*I did this but was still unable to boot to the HD.*

Can you provide an exact description of the error you get?  This may tell us what grub is missing.

*I am pretty sure my BIOS setting should be properly set up. *

Make sure that the Ubuntu drive is the first HDD in the boot sequence.

*Prior to this Ubuntu install I had a M$ XP/Suse dual boot that was working well. I had recenty decided to upgrade my OS(s). So after I formatted the drive I chose to install Ubuntu, and experienced the problems we are now fixing.*

Was SuSE also on the second drive, and that was being booted from first in the BIOS?

*I also do not think I have an option of using it at a straight IDE controller but will look into that.*

Hmm . . . if this is a mobo controller, there is a good chance you do.  Do you have it set up for RAID?  However, this is probably not relevant after all, so best to not fiddle with it now.  If you had SuSE working dual-boot from grub, should be able to do so with Ubuntu.  YaST is very good at detecting, setting up, and configuring the boot loader, much better than the Debian update-grub script.  You're probably gonna need to do some manual grub work.

*I think you are correct that the error might be in detecting the raid controller. I am using an Asus KR7A-133R Motherboard and in order to get it to work for M$ I had to install a driver. Is there a way to use this with Ubuntu? I have only been able to locate Win Drivers for this.*

Again, probably not an issue given you know it worked before.  (There are likely 2 
RAID drivers, one which is appended to the BIOS that enables the RAID devices to be recognized, and a second for W$ to do RAID administration.)

---

### Post by ano1 on 2005-07-05
Hi,

What happens when I boot up is this:
I press the power button and I get all the standerd messages, press Del to enter setup, Lists of my Drives, Devices etc. Then it gets to the boot section. My boot order is Floppy, CD, then Ubuntu HD. If the GRUB floppy was in it would boot to that at at this step in my computers boot process. However without any boot disks it "boots to the HD" (I assume), the screen blanks for about 2 seconds and then just reboots. 

BTW: Suse was on this same drive. I had two partitions, one for M$ and one for Linux. I have since scapped them both for a single Linux partition. So long M$!!
Thanks again

---

### Post by mingus on 2005-07-05
[QUOTE=ano1]Hi,

What happens when I boot up is this:
I press the power button and I get all the standerd messages, press Del to enter setup, Lists of my Drives, Devices etc. Then it gets to the boot section. My boot order is Floppy, CD, then Ubuntu HD. If the GRUB floppy was in it would boot to that at at this step in my computers boot process. However without any boot disks it "boots to the HD" (I assume), the screen blanks for about 2 seconds and then just reboots. 

BTW: Suse was on this same drive. I had two partitions, one for M$ and one for Linux. I have since scapped them both for a single Linux partition. So long M$!!
Thanks again[/QUOTE]

Sorry, I got your problem confused with another one I'm working on, thought you originally had two drives when you actually had two partitions on the same drive.  Now you only have Ubuntu and the swap, so this *should* be easy.  And obviously, the drive can be booted from with grub, you were doing that with SuSE.

When you ran grub-install, it indicated it has successfully installed grub to the MBR.

But let's try to install grub again with the grub shell commands, and this time capture the screen or write down grub's messages . . . it should look something like this:
#grub
>device (hd0) /dev/hde
>root (hd0,0)
here you should get a message confirming grub found it and its filesystem
>setup (hd0)
here you should get about 6 lines, begining with "stage1 . . . ".

BTW, why don't you just have this drive on one of the two available IDE channels?  I notice you have two CD's, the master on each channel.

---

### Post by ano1 on 2005-07-05
Hi,

This is what I got when I ran the GRUB Comands:

grub> device (hd0) /dev/hde
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub>QUIT

I use the Raid controller becuase I also have a second HD that I use for backups and other tasks. I guess mostly because when I built the comptuer (3 yrs ago) thats the way I set it up and never though of changing. That and as a friend told me some day you might actually use it as raid.

thanks for the help.

---

### Post by mingus on 2005-07-05
[I]grub> device (hd0) /dev/hde
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub>QUIT[/I]

Hmmm . . . the reason the floppy works but the HDD does not, is because the floppy is self-contained; it holds a stage1 (the equivalent of the MBR) and a Stage2, the BIOS just hands off to the floppy, stage1 starts stage2 which calls the init and kernel.  The HDD boot is different; the MBR must have stage1 in it just right, it must be at sector 0, and it must know where to find stage2.  

When you boot you don't even see "GRUB . . . "?  Something is missing in the boot sequence.

Hmm . . . so let's try this:

Boot with your floppy, get into a terminal as root, and do (make sure this is entered *exactly* as below!):
#grub
>root (hd0,0)
>install --stage2=/boot/grub/stage2 /grub/stage1 (hd0) /grub/stage2 0x8000 (hd0,0)/grub/menu.lst
>quit
and reboot.  This is the syntax that SuSE would use to install grub to the MBR.  

If this doesn't work, check that hde1 is the bootable partition; just do:
$sudo cfdisk
look at the bootable column; set the boot flag if it isn't already; reboot

If neither of these work, then get back into grub as root and (exactly!) do:
>root (hd0,0)
>install --stage2=/boot/grub/stage2 /grub/stage1 (hd0,0) /grub/stage2 0x8000 (hd0,0)/grub/menu.lst
>quit
this installs grub into the boot sector in the partition; reboot

---

### Post by ano1 on 2005-07-05
[QUOTE=mingus]
When you boot you don't even see "GRUB . . . "?  Something is missing in the boot sequence.

Hmm . . . so let's try this:

Boot with your floppy, get into a terminal as root, and do (make sure this is entered *exactly* as below!):
#grub
>root (hd0,0)
>install --stage2=/boot/grub/stage2 /grub/stage1 (hd0) /grub/stage2 0x8000 (hd0,0)/grub/menu.lst
>quit
and reboot.  This is the syntax that SuSE would use to install grub to the MBR.  
[/QUOTE]
I did this and it constantly repeated "Loading (or starting, forget which) Stage 2" . I then tried booting using the bood floppy and was unable to get back into the system. Instead I got a grub command prompt. My guess is a grub editing screen?


[QUOTE=mingus]
If this doesn't work, check that hde1 is the bootable partition; just do:
$sudo cfdisk
look at the bootable column; set the boot flag if it isn't already; reboot

If neither of these work, then get back into grub as root and (exactly!) do:
>root (hd0,0)
>install --stage2=/boot/grub/stage2 /grub/stage1 (hd0,0) /grub/stage2 0x8000 (hd0,0)/grub/menu.lst
>quit
this installs grub into the boot sector in the partition; reboot[/QUOTE]

I used cfdisk on the drive and the boot column was properly flagged. 

I was able to get back into the system using the floppy and I tried you second GRUB commands and got the following (the install line got cut off in my paste do to scrolling):

grub> root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
<stage2 0x8000 (hd0,0)/grub/menu.lst 
Error 15: File not found
grub>Quit

Am I correct in thinking that something from stage2 might be missing? What would you suggest I try next? Thanks for the help

---

### Post by mingus on 2005-07-06
Grrr!  Initially you were not getting any grub message, now you do but it is not finding stage2.  That indicates you are got grub stage1 into the MBR but that its pointer to stage2 file is not right.  (You are not yet getting to menu.lst, so that's not the problem).  Sometimes its just a matter of tweaking the syntax.  Here are a few others to try.  Again, be very sure the syntax is entered exactly as shown, including the spacing (use copy/paste).  And ofcourse, reboot after each attempt.

>root (hd0,0)
>install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd0) /boot/grub/stage2 0x8000 (hd0,0)/boot/grub/menu.lst
>quit


#grub
>root (hd0,0)
>install /grub/stage1 d (hd0) /grub/stage2 0x8000 (hd0,0)/grub/menu.lst
>quit


(note that with this one the root line is left out - the volume is not mounted first)
#grub
>install (hd0,0)/boot/grub/stage1 d (hd0)  (hd0,0)/boot/grub/stage2 p  (hd0,0)/boot/grub/menu.lst
>quit

If none of these work . . . I suggest you give LILO a try.  Boot loaders and partitioners are a bit of black art.  Sometimes grub just refuses to install right, but LILO works straightaway.  To do this you'll either need to go back thru the installation, or you'll have to download LILO with apt-get.  As I recall, LILO uses the file /etc/lilo.conf.  You'll need to edit that and then at the prompt as root do:
#lilo /dev/hde.

---

