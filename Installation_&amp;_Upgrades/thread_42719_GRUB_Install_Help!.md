---
title: "GRUB Install Help!"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-06-19
I've been trying for hours to install Ubuntu. It's because of the way I setup my computer, that maybe the installer is confused? It always happens after the first reboot where it hangs at "GRUB."

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=1414&stc=1[/IMG]
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=1415&stc=1[/IMG]

Check those images for a better detail to what is happening. Those screens appear right after my bios memory checks and ide drive detection. (Anyone know what this boot selector thingy is called?)

At the boot sequence screen,
Primary Master holds Windows 98 and Windows 2000 in a dual boot config.
Primary Slave holds WindowsXP only.
Secondary Master is where I want to put ubuntu.

As you can see, you can select which drive gets to boot and each harddrive is booted independantly of any other OSes.


Installing GRUB on the MBR wipes out my 98/2000 boot options and won't load ubuntu. (I'll set my booting drive to Primary Master, and it will stop at "GRUB")

During the install, I manually selected which partitions to setup.
IDE6 master, or hdg, is what I'm trying to set it up on.

I've tried a variety of commands to issue GRUB to install to a specific location, but none of them really work. /boot gives a fatal error (I have setup a /boot partition), /hdg1, /hdg, /dev/hdg1.. all fail.

The partitions are setup as follows on that HD:
#1 /boot ext2
#2 / reiserFS
#3 /home ext3
#4 swap


The only time I was able to load past this, was unplugging the power to the other two drives holding Windows, installing Ubuntu. Upon plugging power back in, Ubuntu would fail to load.


There has got to be a way for me to have my cake, and eat it too. :(
Any help on this issue would be appreciated!

---

### Post by luca_linux on 2005-06-19
Could you post your /boot/grub/menu.lst?
Anyway what you need is mapping.

---

### Post by phend-one on 2005-06-19
I'm still a Linux newbie.

Is my /boot even setup?
How would I view that file? (where can I access a terminal or command prompt?)
If I have access to a prompt, can I type: cat /boot/grub/menu.lst ?

---

### Post by luca_linux on 2005-06-19
Grub has a command line: just press "c" or "e" when it shows the Operating Systems list.

---

### Post by phend-one on 2005-06-19
But it doesn't get that far.

It hangs at "GRUB _" and the underscore keeps flashing.

---

### Post by luca_linux on 2005-06-19
It sounds like a bad grub setup rather than a bad configuration.
Try to setup grub again in the MBR from a live-cd.

---

### Post by phend-one on 2005-06-19
Setting up grub on the mbr is so we can start mapping out which drives/partitions we are going to install later on in /boot ? Should I redownload the ubuntu image and burn it again to cd-rw?

Would LILO be easier for this task?

---

### Post by luca_linux on 2005-06-19
Grub is perfect for this, don't worry about.

---

### Post by phend-one on 2005-06-19
I guess I need to download the LiveCD... can I use the Install Disc I have already or I need the LiveCD?

Can I use the Knoppix LiveCD instead?

I just don't want to download another huge file again :(

---

### Post by luca_linux on 2005-06-19
Yeah, I think Knoppix is ok.

---

### Post by mingus on 2005-06-19
Looks like there is a good thread here . . . this may also be helpful . . .

There are 3 MBR's on your system, 1 on each drive.  If you are getting "GRUB . . ." when booting from the *primary master*, that means the grub stage1 was installed on *that* disk's MBR and it cannot find stage2 which is on the first partition of disk3, the secondary master. 

One approach is to try to get this configuration to work, in which case grub on the disk1 MBR must chain-load to W2K on the first partition, and it must also find its own stage2 on disk3 for Ubuntu.   It appears the problem is with the installation of the grub loader, not with the menu configuration.   One cause for this can be if /boot is on a separate partition.   You may not be able to use the "grub-install" script; you may have to run grub interactively and give it explicit paths to stage1 and stage2 for installation.  Additionally, you must therefore always boot from this disk.  If you change the order in the boot sequence, this MBR will not be found by the BIOS.  In this method, the syntax could be:
grub> root (hd2,0)
grub> install /grub/stage1 d (hd0)    /grub/stage2 p    /grub/menu.lst

A second approach is to use the BIOS boot sequencer and treat the disks as entirely separate.   In this method Windows is set up to boot from the disk1 MBR, as before.  And then grub gets installed on disk3, in either of 2 methods.  The first is to use the disk3 MBR; again, this may require installing from grub interactively as cited above, but changing hd0 to hd2 (install line only).  The second (and possibly easier) method is to install the boot loader in the /boot partition and bypass the MBR by flagging that partition as bootable (very simple with cfdisk or fdisk).   Syntax:
grub> root (hd2,0)
grub> install /grub/stage1 d (hd2,0)    /grub/stage2 p    /grub/menu.lst

A key point is to be consistent with how you are using the boot sequencer and how you are setting up the boot loaders.

Installing grub in any of the above config's is possible with the installation CD, but that is rather difficult.  A live-cd is probably better.  Looks like luca_linux will help you with that.    

If you choose the second approach, you will need to reinstall the Windows MBR.  This can be done either from an XP or W2K install CD (Recovery, "fixmbr" at the command prompt) or from a W98/ME/DOS bootable diskette ("fdisk /mbr" at the A:\> prompt).  If you don't have this media, you can download it from [www.bootdisk.com](www.bootdisk.com),

Questions, don't hesitate to ask.

---

### Post by luca_linux on 2005-06-20
Also the "mapping" feature could be useful in this case: [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10)

---

### Post by mingus on 2005-06-20
[QUOTE=luca_linux]Also the "mapping" feature could be useful in this case: [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10)[/QUOTE]

Yes!!! - another method!

---

### Post by phend-one on 2005-06-21
Sorry for no reply, my internet was cut by my provider... -__-


Mingus, some of that I already knew. But you lost me when you got so technical with some of this stuff. I'm already treating the first two HDs with Windows as separate disks. I want to make this easy and do the same with Linux. I want to get GRUB on that /boot partition I created, or at least on that drive where ubuntu is going to be installed.

I don't understand some of the "linux-jargon" that was mentioned. "chain loading?"  I'm pretty decent with my understanding of computers and the Windows world, but I am very much a linux newbie. 


luca_linux, the livecd finished downloading. But I don't understand what that "Q10" mapping thing does? An explanation with what we are trying to accomplish would help a lot. If I can see the goal, I can start understanding what's going on.

---

### Post by mingus on 2005-06-22
Chain-loading is a boot loader term . . . the primary loader hands off to another loader installed elsewhere.  Grub can hand off to Windows ntldr.  (And ntldr can be set up to hand off to grub, although its a bit of a kluge.)  More on this below. 

Using the BIOS boot sequencer dictates how you install the loader.  So assuming that you *will* use the sequencer, and you prefer a separate Ubuntu /boot partition, then your easiest approach is to:

1- reinstall the Windows boot loader in the first drive's MBR.
2- install grub to the Ubuntu /boot partition
3- mark the Ubuntu /boot partition as the "active" on that drive (also called setting the boot flag)

Reinstalling the Windows MBR loader you know how to do . . . this will overwrite the grub file on that drive and restore Windows to booting as before.

There are a number of methods to reinstall grub.  IMO, this is the most straightforward, easiest, most clean . . . reinstall Ubuntu.  When you get to the partitioning step, set the bootable flag on the /boot partition.

Then when you get to the step to install grub, do *not* install it to the MBR.  Install it to the /boot partititon.  As a precaution, repeat this step and also install it to a floppy.

Complete this first stage of the installation, and reboot.  Make sure the sequencer is booting from the Ubuntu disk.  The BIOS should call grub from the /boot partition.

If this does not work (it should), reboot from the floppy - you can fix the boot loader after finishing the installation.

Finally, when you boot from the Ubuntu drive you may see a grub menu entry for booting both of your Windows drives.  If so, this will be using chain-loading.  It may even work - giving you the choice of always booting from the Ubuntu drive and then chain-loading to Windows vs changing the BIOS boot sequence to the other drives when you want to boot those OS's.  But once again, if you boot from the Windows drives you will not see grub nor can you get to Ubuntu from there; you can boot Ubuntu only by choosing that drive in the sequencer.  If you would like to always boot from Ubuntu and chain-load to Windows, and it doesn't work right or wasn't set up by the installer, you can edit the file /boot/grub/menu.lst to add chain-loader sections for Windows.  It is easy and the file documents how to do this.

That's all there is to it!

---

### Post by mingus on 2005-06-22
I should have qualified the suggestion to install grub on the Ubuntu drive's /boot partition . . .

You should also be able to just install grub on *that* drive's MBR, since the sequencer is booting from that drive.

I've seen it work both ways.

---

### Post by phend-one on 2005-06-23
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdg2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdg2 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdg2 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd2,0)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdf1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdf1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
chainloader	+1



``` 

Here is my /boot/grub/menu.lst . I'm in knoppix livecd right now posting this information.

It never gets to any choices. It just hangs at "GRUB _" Nothing can be typed, nothing else is to be seen except the blinking cursor.

What's wrong? I installed it to a floppy, but it was full and didn't get written in. How do i go straight to the install of grub from the install cd of ubuntu? I also installed grub to the /boot, but that didn't work. 

Need some tutoring!



**EDIT:** I usually get the first type of error from the hard drive, but I got the lovely block of GRUB from the floppy.

Anyone been able to just type '/boot' as the location to install GRUB? It gives me a fatal error.

---

### Post by phend-one on 2005-06-25
I tried disconnecting the HD, then installing ubuntu on the single hard drive, then plugging everything back in, but it only messes up the hard disk controller. 

Looks like I'll have to actually find someway to mess with that grub menu list.

Anyone have any other suggestions? It would be appreciated!

---

### Post by mingus on 2005-06-26
Looking back over this thread, there appears to be at least 2 problems.  The boot loader is not getting properly installed and the disk mapping in grub vis-a-vis the BIOS may be out of sync.

You indicated installing Ubuntu to the Secondary Master, "IDE6 Master", assigned hdg?  Umm, the Secondary is the second cable on the primary IDE controller, and its master would typically be IDE3 (i.e., hdc).  What is the 3rd drive physically connected to? PCI, SCSI, SATA, additional IDE controller?  What is the sequence assigned to these devices by the BIOS?  How did you arrive at "IDE6 Master"?

You tried to install grub to various devices, how were you doing this?  Are you sure the partitions were actually mounted first?

When debugging the grub install, my pref is always to create a grub boot floppy, to get into the system with and to do subsequent test & install.  The following thread, post #22, details a procedure to create the floppy.  It should work for you, just be sure that when you come to the mount menu you choose the partition which corresponds to where / resides on hdg2, and also in the commands I provide hdg1 (this time, your /boot partition) should be used in place of hdb1.

[http://ubuntuforums.org/showthread.php?p=229174](http://ubuntuforums.org/showthread.php?p=229174)

Post back the results.

---

### Post by phend-one on 2005-06-27
IDE6 and hdg were assigned in the ubuntu installer. It's what it defines that hard disk as.

My motherboard is based on the 440BX chipset. (Abit BE-6). Basically it has 4 IDE channels. Two are DMA33 (IDE1,2). Other two are UDMA66 (IDE3,4). Somehow ubuntu arrives at that as the IDE6. I have two cdroms plugged into IDE1 (or IDE2, forget). Two HD plugged in on IDE3, and the final one, the one I'm trying to install ubuntu at, IDE4.

Hope that answers the question. Will look over that link you sent me.
Thanks for the reply!

---

### Post by mingus on 2005-06-28
Still need clarification . . . with a config like this, we must be able to tell grub *explicitly* how to sync with the BIOS because grub does not read that directly (no boot loaders do).  You have a complication because you have *2* BIOS's, a Highpoint bolted on to an Award, kluged together.  Unfortunately, the manual is of little use.

[I]Primary Master holds Windows 98 and Windows 2000 in a dual boot config.
Primary Slave holds WindowsXP only.
Secondary Master is where I want to put ubuntu.[/I]

*Two are DMA33 (IDE1,2). Other two are UDMA66 (IDE3,4). Somehow ubuntu arrives at that as the IDE6. I have two cdroms plugged into IDE1 (or IDE2, forget). Two HD plugged in on IDE3, and the final one, the one I'm trying to install ubuntu at, IDE4.*

Highpoint shows the W98 drive to be IDE1/master and the XP drive as IDE1/slave; your post indicates IDE3 - I'm guessing that the Highpoint is blind to the main IDE controller, and so it sees *its own* IDE1 (really IDE3) as being the primary?  Note that the installation read the entire IDE chain, putting Ubuntu on IDE4/master, but grub thinks that the chain begins with the Highpoint IDE3.

Do you know why the Highpoint use the Windows-like driver letter assignments from the Award BIOS when referring to its own drives?  Or is this a second set of C-F?

How do you have the BIOS setup pgm's boot sequence field configured - I'm guesssing "EXT, A, C"?  And what is the meaning of the Windows-like drive letter assignments?  It appears as if C-F is possible on the main controller, and another C-F on the Highpoint?

You don't have anything on 1 of the main IDE channels; a HDD there is not an option?

When you boot Windows now, is it dual-boot from W2K to XP or the reverse?  Or are you using the Highpoint boot sequencer to point the boot?

Are you able to get into Ubuntu?  You indicated you tried to install grub in various locations; how were you doing that?

Finally, you might have a go at creating the floppy in the thread ref'd above.  Like with XP on a floppy, the loader is self-contained and so the need to reconcile the BIOS boot sequence to the loader and the IDE chain is avoided.

---

### Post by phend-one on 2005-06-30
Okay, I'm back with a solution that works well.

- Physically set the drive you want ubuntu / linux on, as the master drive (jumpers!)
- Boot up, making sure the drive in the driveloader is stating that drive as the master drive.
- Install. You can install to /boot or the MBR. It does not matter.
- Now swap the drives so that the Windows (or whatever) drive is master, and the linux (ubuntu) drive is slave. 
- Use the driveloader to choose between them. 

Should work. At least it did for me.

Thank you very much to those who have contributed to this thread. Muchly appreciated!

---

### Post by mingus on 2005-07-01
Congratulations.  Your solution is straightforward.

FWIW, just one point of clarification:  From grub's point of view, master or slave is immaterial.  Nor is their order in the boot sequence.  What grub does need to always know, is where the booting drive is *relative* to the boot sequence defined in the BIOS.  (This is why all the earlier questions.)  However, if the BIOS is going to be used to dynamically change the sequence - as you are doing - then in all cases grub should be simply told that where it is installed is hd0, no matter what the drive is along the IDE chain.  In other words, hda=hd0, hdb=hd0, hdg=hd0, etc.

Good job.

---

