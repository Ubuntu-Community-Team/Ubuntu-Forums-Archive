---
title: "Consistent problem dual booting 6.06.1 LTS with Win2k"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by DavidRB on 2006-12-22
My problem is a variation on a theme discussed on the forums, but I'm not sure how to adapt what I've read for my precise situation - any help for this newb is gratefully received! :D 

**Summary:**
I'm trying to set up a dual-boot with my existing Win2k sp4 system. I installed Ubuntu 6.06.1 LTS onto the E-drive, giving it the whole drive. The install goes fine, Ubuntu works fine, but after a single re-boot into Win2k, Ubuntu won't boot. I have re-installed from various media (DVD, CD, alternate, desktop) and this is a consistent problem.

**My system:**
 Windows 2000 Pro SP4, AMD Athlon 1.4Gig processor, 512 Meg RAM, a CDRW and DVD, two 60Gig hard-drives:
 C: hard-drive master, FAT32, Windows installed
 D: DVD player
 E: second hard-drive, was FAT32, and empty - given over completely to Ubuntu 6.06.1 LTS Desktop install
 F: CDRW

**Efforts so far:**
 I've done the following:

 [LIST]
[*]studied the install procedure in the LinuxFormat Ubuntu special, 'Beginning Ubuntu Linux', 'Ubuntu Unleashed' and the official Ubuntu book;

[*] 	downloaded the desktop, alternative and dvd iso's, burned the images to disk;

[*] 	the alternative install stalled about 1% from the end, and when I restarted it wouldn't give me the dual boot menu, just the Grub prompt;

[*] 	the official Ubuntu book dvd installer wouldn't work at all;

[*] 	the downloaded desktop and LinuxFormat CD's all installed ok;

[*]            I've had a good look around the forum, and not seen quite what I'm looking for.

[*]](*,) 
[/LIST]
 
The desktop install goes fine (though I haven't got internet access or package installation sorted); I have a consistent problem after rebooting into Windows. My only solution so far has been to re-install Ubuntu and try to repeat the problem: it would appear to be a consistent problem.

**Symptoms:**
 
This appears during a normal boot and during the aborted one:

```

Booting 'Ubuntu, kernel 2.6.15-26-386'

root (hd1,0)
	Filesystem type is ext2fs, partition type 0x83


```

That's interesting - I was sure Ubuntu said it would create an ext3 partition...  /dev/hdc as ext3, /dev/hdc as swap; pressing on,

```

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quite splash
	[Linux-bzImage, setup=0x1c00, size=0x15787d]
initrd /boot/initrd.img-2.6.15-26-386
	[Linux-initrd@0x1f931000, 0x6ae389 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.

```

It's at this point that the Ubuntu splash screen appears on the first reboot after install. A normal Ubuntu boot-up sequence then follows. BUT if I'm booting Ubuntu AFTER rebooting into Windows 2000, it is at this point that the Ubuntu splash screen does this:

```

Loading Essential Drivers...Ok
Mounting root File System

```

then BANG!! Straight out of the Ubuntu splash screen, and the text described above reappears, and is followed by this message:

```

mount: Mounting /dev/hdc1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: Can't access tty; job control turned off
#

```

Then all I can do that is in any way helpful is to press control-alt-delete to soft-boot. The F* keys do nothing for me, neither does 'exit' or any of the other tricks noted on the Forum that I've found (and understood / tried ...) so far. Windows can then reboot but verrrrrrrrry slowly. Rebooting into Ubuntu recovery mode didn't help - it seemed to want to find the ext3 partition also.

I don't want to run Ubuntu via a floppy disk bootloader, nor do I want to be plugging and unplugging hard-drives every time I want to use Linux. I just want a dual boot scenario that's easy to set-up and reliable. Or else remove Ubuntu and the boot loader to get back my Windows 2000 system, and reformat my E drive to FAT32.

Can anyone help please? Many thanks!

---

### Post by ajgreeny on 2006-12-22
What is the output of *sudo fdisk -l* in terminal (using liveCD if you can't boot ubuntu), or conversely if you use the gparted in the install CD you will get a proper indication of where your partitions are.

Also if you can get at a copy of your ubuntu /boot/grub/menu.lst file it would be helpful to see that as well.  There are various utilities to view files on a linux partition from windows, available as freeware for you to use to do this latter action, such as explore2fs from:-
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
It's worth having that in any case, so you should get a copy to use if you are going to boot into windows often.

---

### Post by DavidRB on 2006-12-22
Many thanks for the response!  :)  I'll try this out when I get home - Merry Christmas if I can't get back to you with the requested data beforehand.

cheers.

---

### Post by ajgreeny on 2006-12-22
Just a quick thought - you didn't remove the windows hard disk or disconnect it when you installed ubuntu, did you?  If so that will be the problem.  Now that you 've put it back, all your partition numbering etc. will be wrong.

---

### Post by DavidRB on 2006-12-22
I'm back!

First things first, no, I didn't unplug the Windows drive when installing Ubuntu. (My IDE cables are a severe pain to remove and plug in, so I tend to leave them alone! ;) )

Thanks for the tip about the download tool - got that and ran it. The results are:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device	          Boot	Start	End	Blocks		Id	System
/dev/hda1	*	1	7476	60050938+	c	W95 FAT32 (LBA)


Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device	Boot	Start	End	Blocks		Id	System
/dev/hdc1	*	1	7288	58540828+	83	Linux
/dev/hdc2		7289	7476	1510110		5	Extended
/dev/hdc5		7289	7476	1510078+	                82	Linux swap / Solaris

ubuntu@ubuntu:~$ 
```

Now, using the live install disk, I've got hold of the menu.lst file also:

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
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I hope that helps identify the problem; I really appreciate your input.

Cheers.

---

### Post by ajgreeny on 2006-12-22
Try changing the menu.lst entry for the linux ubuntu to:-
title        Ubuntu, kernel 2.6.15-26-386
root        *(hd2,0)*
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

Note the change in italics.  You will need to do this using the live cd, I think, but your system seems to have been confused by the cdrom being hdb, in grub nomenclature that is hd2, the 0 at the end being the 1 in linux nomenclature.  If that works and you can boot, do it for all the other linux entries once you get ubuntu up and running.

---

### Post by DavidRB on 2006-12-23
Thanks! Just got your message, will try that now.
cheers! :)

---

### Post by DavidRB on 2006-12-23
Sorry, no joy.

The live cd couldn't see the grub folder; so I reinstalled and started again.

Once I'd rebooted, I opened a terminal and used sudo vi to make the suggested change.

Upon rebooting, I got this:
```

Booting 'Ubuntu, kernel 2.6.15-26-386'

root (hd2,0)

Error 21: Selected disk does not exist

Press any key to continue...'
```

I was able to reboot into Ubuntu safe mode, and at the prompt, use vi to revert, and successfully rebooted; but after rebooting into Windows, I'm back to the original problem.

Ho hum!

---

### Post by ajgreeny on 2006-12-25
Sorry now I'm totally bemused.  All I can suggest is that you try again and after installing, boot ubuntu and before you do anything else you do sudo grub-install /dev/hda in a terminal.  This may sort out any problems of how grub sees your disks.

---

### Post by ajgreeny on 2006-12-27
Another thought!
If you have a floppy (which you don't mention in your first post), get a copy of smartbootmanager and copy the image to a floppy with rawrite (windows) or dd (linux), then boot the comp using the floppy, which may find your linux install and allow you to boot it, I think.

Also if you have no floppy, start up your machine and when the grub menu appears, highlight your ubuntu if it's not the default, and before it tries to boot, hit e, which will bring up the menu.lst entry for ubuntu.  Now scroll to the lines with the partition info in it, and using the cursor keys move to the data and edit it, trying one at a time, hd1,0 - hd2,0 - and see if it works.  I also see that the third line in your menu.lst at present refers to a different partition to the second, root line, ie you have hd1,0 in line 2 but hdc1 in line 3.  These must point to the same place, even though using different nomenclature.

So - If you change line 2 to hd1,0 line 3 should read hdb1, and if line 2 is hd2,0, then line 3 should be hdc1.  All these changes will only last for the one boot up attempt, so don't worry about messing things up completely.

OK, having edited each line, hit enter to save the change for this time only, and when you've made all the changes to lines 2 & 3 as needed, hit b to boot.  Hopefully one of these edits will be the one needed, so remember what you used that time and when ubuntu is running, edit the menu.lst file to take account of the partitions you've just found to be correct.  Don't forget the recovery mode entry as well.

Sorry if this is a long winded answer, but I hope you will get it all sorted soon.  I don't think you really need to reinstall again as it shouldn't be necessary to sort out this problem once we get you partition maning right in the menu.lst file.

Good luck!

---

### Post by DavidRB on 2006-12-27
Thanks ajgreeny!
Just got back from family Christmas, and need some time to experiment ... will revert with the results tomorrow night. Many thanks for your perseverance, especially so over the Festive Season!:) 
cheers
Dave

---

### Post by louieb on 2006-12-28
One more thing to try. I don't know why but you system seems have Linux confused by the  way the drives are hooked up. 
From the fstab output and comments you made it look like your[LIST]
[*]Windows drive is hooked up to the end (master) connector of  ide1 (hda)
[*]a DVD drive is hooked to the middle (slave) connector of ide1 (hdb)
[*]Ubuntu drive is hooked up to the end (master) connector of  ide2 (hdc)
[*] a CD drive is hooked to the middle (slave) connector of ide2 (hdd)[/LIST]That is not the normal way drives are usually plugged in but it should be ok but I think you should check the jumper setting for the proper master slave settings on all 4 drives. The jumpers should be set to master or slave depending on where the drive is is plugged in to the ribbon cable. It is also ok if the jumpers are set to cable select.   (There should be a sticker on the drive showing what the jumper positions are, but sometime I have had to go to the manufactures web site for that information).

If your jumper settings are ok and you are still having boot problems then I would try this:  Swap connectors between the second hard drive and the DVD drive. Where both hard drives are on one ribbon connector and both optical drives are on the other connector. That is what I would normally expect to see. Again making sure the jumpers on the drive are set to the correct master slave position depending on which connector  the drive is plugged into.[LIST]
[*]Windows drive is hooked up to the end (master) connector of  ide1 (hda)
[*]Ubuntu drive is hooked up to the middle (slave) connector of  ide1 (hdb)
[*]a DVD drive is hooked to the end (master) connector of ide2 (hdc)
[*] a CD drive is hooked to the middle (slave) connector of ide2 (hdd)[/LIST]After swapping the drive connections I don't think the GRUB menu will display. I am guessing you will have to reinstall GRUB.  See my signature for a thread on how to do just that.
BTW: Happy New Year!

---

### Post by DavidRB on 2007-01-02
I'm back! Happy New Year to both!

I've had a go with 'sudo grub-install /dev/hda'; after the disclaimer about a bug in xfs_freeze, it displayed the contents of the /boot/grub/device.map file:

```

(hd0) /dev/hda
(hd1) /dev/hdc

```

Changing hd1 to hd2 here didn't seem to affect rebooting into Ubuntu with hd2 in menu.lst; changing hd2 to hd1 consistently in menu.lst caused all sorts of problems!

Inside meu.lst I've tried changing hd1, and hdc, systematically;

[LIST]
[*]using hd0 and hda, hdb, hdc, hdd gives 'Error 15: File not found'
[*]using hd1 and hda or hdc ives me my existing problem - see above;
[*]using hd1 and hdb or hdd starts to boot Ubuntu, gets to the splash screen, tries to mount the file system, then says it's waiting (presumably for a CD to be inserted);
[*]using hd2 with hda, hdb, hdc, hdd gives 'Error 21: Selected disk does not exist'
[*]using hd3 and hda, hdb, hdc, hdd gives 'Error 21: Selected disk does not exist'
[/LIST]

I haven't had the nerve to start changing jumper settings on the hard-drives, since I'm not sure what impact that might have on my Win2k system...

Nothing I've tried seems to help the re-booting after Windows. Perhaps I should consider using a boot floppy to get to my Ubuntu install, or bin W2k altogether (after checking my shiny new serial external modem works ok first ;) )

cheers
Dave

---

### Post by ajgreeny on 2007-01-02
Remember that hd0,0 is grub nomenclature and hda,1 is linux.  In grub you need the full grub name, ie, hd0,0 (windows), hd2,0 (ubuntu).  In my menu.lst file I have the following:-

title        Ubuntu, kernel 2.6.15-27-k7
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda2 ro quiet splash vga=788
initrd        /boot/initrd.img-2.6.15-27-k7
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-27-k7
boot

title        Ubuntu, kernel 2.6.15-26-k7
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda2 ro quiet splash vga=788
initrd        /boot/initrd.img-2.6.15-26-k7
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-26-k7
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


You will see that in each case the root partition is in grub name (hd0,1) and the kernel partition is in linux name (hda,2).  Ok it's a bit confusing, but you must have the full partition name and it must be for the same partition in all cases.  Don't give up on this yet, there must be a way round it, even if you have to reinstall your hard drives the normal wat, ie as hda and hdb.

Good luck, again.

---

### Post by DavidRB on 2007-01-02
Thanks again!
I'll try that later on and let you know how I got on... ;)

---

### Post by crispingatiesa on 2007-01-02
I'm having semi-similar problems with XP and Ubuntu 6.10 (Boot in Xp and then problems booting back into Edgy)

In my case the problem seems to be a Mainboard + Video Card issue. If you just reboot from XP into Ubuntu the memory registers of the VC and some BIOS info dont' get flushed. Solution to my problem was to turn the computer off and back on after using XP instead of just rebooting.

---

### Post by DavidRB on 2007-01-03
Things just get curioser. 

I don't understand why (hd1,0) and hdc1 seem fine if I just keep re-booting into Ubuntu, but doesn't seem the right combination after just one re-boot into Windows.

As for shutting down completely, I've had no luck there either - the damage seems to be done permanently to the Ubuntu installation (or its bootloader).

Other threads are talking about the master boot record, and changes made to it by the Ubuntu installation process being reversed / 'repaired' by Windows when it boots. It occurred to me last night that perhaps another consideration might be the possibility that my Norton AntiVirus / Internet Security / SystemWorks might be recognising the MBR change as alien and 'repairing' it during boot-up of Windows.

:-|

---

### Post by Bartender on 2007-01-03
I agree with louieb -
Your drives are set up in a non-standard fashion and Ubuntu seems to be having trouble with that optical drive setting there as your second device.  Another thing to think about - when a HDD and an optical share the IDE bus, your HDD's transfer rates are often crippled because of the optical's DMA settings.  I don't understand all the in's and out's of this, but have read it often enuf that there must be something to it.

First off, resetting jumpers on your drives is cake after you've done it once or twice.
Second, it's highly unlikely that your Windows drive could be affected.  It's already configured as master on IDE #1 and that's where it'll stay.  I'll refer to your ribbon cables as IDE #1 and IDE #2 because that's what you have - 2 IDE buses, each of which can support 2 devices.  Rule of thumb is to have bootable devices on your IDE#1 bus.  That's the bus and the ribbon cable where your Windows drive is connected.

What you want to try is this - and take notes as you're doing it so you can put it all back the way it was if you paint yourself into a corner.

Remove the second HDD (your Linux-to-be drive, let's just call it HDD #2) from the end clip on IDE #2.  Remove the optical drive (the DVD drive, right?) from the middle clip on IDE #1 ribbon.  Set it aside for now.  

Take a look at the back of HDD #2.  You'll find the power receptacle, the data receptacle, and a little bank of eight or ten pins with a dinky plastic jumper pushed onto 2 of those pins.  Now look at the sticker on the top of the drive.  You should find a map that describes how to set the jumper for master, slave, cable select - there may even be a setting for "Single", which describes where to set the jumper if you only have one device on the ribbon cable.  What you want is the "slave" setting.  HDD #2 will be set to "master" right now.

Grab a pair of tweezers, grasp the jumper, and gently rock it off the "master" pins.  Use your fingers or the tweezer to push it onto the "slave" pins.  Now jack it into the middle clip on your IDE #1 ribbon cable, plug in a power lead, and set the drive on a stack of books or whatever's handy (as long as it's non-conductive) so that the drive is setting aside your PC and there's no tension on the cables.  We're just testing at this point, and you don't need to have it screwed into the chassis.

What we want to see at this point is HDD #1 (Windows) right where it was on the end clip of IDE #1 and HDD #2 (Linux) on the IDE #1 middle clip.  Back on IDE #2 you've got nothing on the end clip and a CD drive on the middle clip, right?

Do you really use both optical drives?  If not, take the newer drive (I assume the DVD) and look at its jumper setup.  It was (or shoulda been anyway!) jumpered as "slave".  Find its map and figure out how to move the jumper to "master".  Remove the CD drive entirely and put the DVD drive on the IDE #2 end clip.

Or leave the CD drive where it is and install the DVD drive to the end of IDE #2 after changing its jumper to "master".  

Either way, you'll want to make sure that you have an optical drive on the IDE #2 end clip, and that drive must be jumpered as "master".  If you're going to have only three devices (2 HDD's and one optical drive), make the empty space the middle clip on IDE#2.  If you choose to leave the CD drive in the system, you won't have to change its jumpers or its position on the IDE #2 ribbon.

Start it up, go into BIOS, check to see that BIOS correctly identified the drives and their positions in the "Main" section of your BIOS.  If everything looks OK (it should) exit from BIOS and let Windows boot.

Here's a link for changing drive letters.
[http://www.dougknox.com/tips/xp_drive_letters.htm](http://www.dougknox.com/tips/xp_drive_letters.htm)

I'm not sure what you'll see when you get back into Windows, but it'll probably look like this:  "C" drive will be your Windows drive (HDD #1), D drive your Linux drive (HDD #2), E drive your DVD drive (if it ended up as the master on IDE#2 ribbon cable) and F drive will be the CD drive.

You know what I'd do?  It probly won't make any difference to you in the long run, but your Linux drive will have at least 2 partitions, maybe more if you start getting adventurous :twisted: 

Designate your DVD drive as "J" and your CD drive as "K".  I honestly don't know if there's a potential for problems but hear me out...

If you set the 2 optical drives as 'E' and 'F', then Windows thinks the next 2 drives (or "partitions") in your system are the opticals. 

What if you create a Linux primary partition, then create a second Linux partition, then decide to create a shared FAT32 partition that both OS'es can use?  Counting swap, that would be four partitions on the Linux drive.  Those partitions would probably be
 
/dev/hda1, /dev/hda2, /dev/hda3 & /dev/hda5     
or 
/dev/hda1, /dev/hda2, /dev/hda5 and /dev/hda6

depending on how you set that up.

Let's say you do that.  Four partitions on the Linux HDD.  Now you go back to Windows, and you want to access that FAT32 partition.  That's where I'm wondering if there'll be a problem, because I think Windows would want to see the Linux partitions as E, F, G, and H.  But you've already designated E and F as your opticals!

So, since there's no downside to calling the opticals J and K, but I believe there's a *potential* for trouble the other way, why not just give the opticals letters that will stay out of the way of how Windows would perceive the Linux partitions?

Maybe I'm all screwed up and that's not a problem at all!  :rolleyes:

---

### Post by DavidRB on 2007-01-04
Thanks guys!

I guess tonight I'll be playing with those jumpers!

Many thanks again everyone! :)

---

