---
title: "&quot;Error 21&quot; on grub boot after new install"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by schwim on 2008-07-16
Hi there everyone,

I've got a small dilemma.  I installed Kubuntu 8.04 (KDE 4) from the livecd and during that install, chose to resize the drive, leaving a portion for my existing XP install and acquiring a portion for the new linux install.

On reboot, I got the dreaded "Error 21", which searching reveals that GRUB can't find the drive.  This is of course in spite of the fact that GRUB is sitting on the same drive that it can't find, but I digress ;)

Solutions I found via the Goog mostly pertained to swapping the bios settings from auto to manually setting the drive.  The problem is none of that seems to be working for me.

I can say this about the computer:  When it was built, the guy told me that I only had one cd-rom because the mobo was set up for sata drives, and since I had an IDE drive, one of two available IDE slots were taken by it and I had no room for another cd drive.

When the error 21 popped up, I figured that this had come back to bite me in the keester.

On bootup, it shows my drive's serial # connected as HDD0.  When I go into the bios, I see slots for IDE primary, secondary and third masters and slaves.  All of them have "none" beside them.  I went into each one and selected "auto detect drive" and all six of them stayed blank after the auto detection was done.  I tried changing all from auto to manual, but during reboot, the GRUB error persisted.

I'm stumped.  I don't want to damage the install, and I sure as heck don't want to lose my Windows install, so I thought I'd ask for some assistance before I did something that I couldn't reverse.

Could someone help me figure out what I need to do to get GRUB to recognize the drive that it's sitting on?

thanks,
json

---

### Post by logos34 on 2008-07-16
> **schwim said:**
> When it was built, the guy told me that I only had one cd-rom because the mobo was set up for sata drives, and since I had an IDE drive, one of two available IDE slots were taken by it and I had no room for another cd drive.

You mean only one IDE channel (two devices/per channel).  Your cdrom and ide hard disk on the same cable as master and slave? 

>  On bootup, it shows my drive's serial # connected as HDD0.  When I go into the bios, I see slots for IDE primary, secondary and third masters and slaves.  **All of them have "none" beside them.  I went into each one and selected "auto detect drive" and all six of them stayed blank after the auto detection was done**.  I tried changing all from auto to manual, but during reboot, the GRUB error persisted.

what? the Bios must be detecting the drives, otherwise you wouldn't even get as far as grub on the MBR (where it gives error because it can't find root partition with stage2 and menu.lst.

Boot from the live cd and run this in a terminal:

sudo fdisk -l

post output.

Might want to also mount root and check your /boot/grub/menu.lst (post that too if want)

---

### Post by schwim on 2008-07-17
Hi there logos, and thanks very much for your response.

[EDIT]Got it to boot via liveCD and will post necessary data.[/EDIT]

---

### Post by schwim on 2008-07-17
> > sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde14de14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12844   103169398+   7  HPFS/NTFS
/dev/sda2           12845       19457    53118922+   5  Extended
/dev/sda5           12845       19181    50901921   83  Linux
/dev/sda6           19182       19457     2216938+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

How would I go about mounting the root?

thanks,
json

---

### Post by logos34 on 2008-07-17
> **schwim said:**
> How would I go about mounting the root?

just double click on it in side pane of [edit] file browser

---

### Post by logos34 on 2008-07-17
run this to reinstall grub:

> [B]sudo grub

find /boot/grub/menu.lst[/B]
(should output 'hd0,4' = root /dev/sda5)
[B]root (hd0,4)
setup (hd0)
quit[/B]

---

### Post by schwim on 2008-07-17
I could not find /boot/grub under root on the left.  I found this under volume (ext3).

/boot/grub/menu.lst

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
# kopt=root=UUID=8363ca61-4f3b-420a-ad49-ab212127276c ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8363ca61-4f3b-420a-ad49-ab212127276c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8363ca61-4f3b-420a-ad49-ab212127276c ro single
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
chainloader	+1

Please let me know if there's anything else I need to post.

thanks,
json

---

### Post by logos34 on 2008-07-17
yeah, that's it.  Looks correct.

So try what I suggested.  But it probably won't solve the problem because the Bios doesn't detect the drives, and yet fdisk sees the hard disk fine.  Hmm...

---

### Post by schwim on 2008-07-17
Hi there logos,

I followed your last post and succeeded with no errors.  I shutdown, pulling the cd, but on restart, I continue to get error 21.

I don't know if printing the menu.lst might change anything.

thanks,
json

---

### Post by schwim on 2008-07-17
> **logos34 said:**
> So try what I suggested.  But it probably won't solve the problem because the Bios doesn't detect the drives,


man, that's a bummer :)

Any other thoughts on the matter?

---

### Post by logos34 on 2008-07-17
DO you have a usb stick and does the Bios support USB booting?  If so you could download [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download") (USB tar.gz) from the the kubuntu live cd session you're in now, copy it on the stick and boot from usb drive, then try to boot ubuntu and windows.

Or if no USB stick but you have access to another machine, get the CD version and burn it to disc and boot from that

---

### Post by schwim on 2008-07-17
In the BIOS, under hard disk boot priority, I see:

1. SCSI-0 : ST3160212A
2. Bootable Add-in Cards

So in the section that it determines boot order, the drive shows up, but under the IDE selection, I can't seem to choose any setting that works.

---

### Post by logos34 on 2008-07-17
I'm still trying to figure out why the Bios doesn't detect the drives...If you select 'manual', you have to enter the various settings by hand, which means you need to know the make, model and specs of the ide hard disk (->manual or website).

---

### Post by schwim on 2008-07-17
Hi there logos,

No matter what options I choose in super grub, I get error 15(file or disk not found).  There are so many options in the system that I'm not sure that I tried them all, but I tried a buttload and so far, all ended up with the same error.  I tried choosing a harddisk & partition, but it gives me an error before I even get a chance to pick a drive.

Holy crap, I screwed myself up on this one.

thanks,
json

---

### Post by schwim on 2008-07-17
> **logos34 said:**
> If you select 'manual', you have to enter the various settings by hand, which means you need to know the make, model and specs of the ide hard disk (->manual or website).

That's the strange thing.  Even if I choose manual, the options below stay greyed out and I can not make any changes to capacity, cylinder, head, etc.  It's as if something is overriding the drive setup completely.

---

### Post by logos34 on 2008-07-17
>  1. SCSI-0 : ST3160212A

Why is your IDE hard disk showing up as SCSI/SATA?  It's an IDE drive for sure.  

Your cdrom and hard disk are either jumpered master and slave or both set for 'cable select'.  That's the only other thing that comes to mind that you could change that might make a difference.  For instance, you could change the jumper clips on the back of each drive to cable select or master and slave, depending on which cable connector they're on (black=master, gray=slave, blue=motherboard).

I'm really at a loss because the Bios at the very least should detect the drives.  Yet you were able to install--go figure.  Maybe flashing the bios with an update would help. (But you'd need to dl the file and copy it to a floppy, or else do it in windows if you can get into it).

not sure what else to suggest

---

### Post by schwim on 2008-07-17
I found the following settings in the bios under On-Chip ATA Devices.  Would any of these settings perhaps affect the detection of the drive?

thanks,
json

---

### Post by logos34 on 2008-07-17
> **schwim said:**
> Hi there logos,

No matter what options I choose in super grub, I get error 15(file or disk not found).  There are so many options in the system that I'm not sure that I tried them all, but I tried a buttload and so far, all ended up with the same error.  I tried choosing a harddisk & partition, but it gives me an error before I even get a chance to pick a drive.

...

That's the strange thing. Even if I choose manual, the options below stay greyed out and I can not make any changes to capacity, cylinder, head, etc. It's as if something is overriding the drive setup completely.

As far as choices in SGD, here are the ones you should try:

> **Gnu/Linux (Advanced)** contains the options to
restore GRUB's or LiLo's IPL to MBR for you,
[COLOR=Blue]boot a Linux OS by it's menu.lst file,
boot a Linux OS by it's kernel directly (via symlinks),[/COLOR]
or boot any OS by its boot sector if the boot sector contians an IPL for a boot loader.
You can also set the boot flag on a Linux partition, (sometimes needed for LiLo).
**Windows (Advanced)** leads to a menu where you can
restore Window's NTLDR bootloader's IPL to MBR (equivalent to FIXMBR),
[COLOR=Blue]boot Windows by its boot sector (bypassing the MBR),
[COLOR=Black] boot Windows on a non-first hard disk,[/COLOR][/COLOR]
set the boot flag on a Windows partition,
and
re-install Windows NTLDR's IPL to a boot sector (equivalent to FIXBOOT).manually specifying the partition like you did is also normally an option, but it's not letting you because it can't see the hard disk.  Again, this because there is a serious issue in the Bios.

About the Bios: Can you restore the Bios settings to factory defaults?  Maybe that will 'unlock' whatever seems to be overriding it

---

### Post by logos34 on 2008-07-17
> **schwim said:**
> I found the following settings in the bios under On-Chip ATA Devices.  Would any of these settings perhaps affect the detection of the drive?

The factory default for block mode is sometimes 'disabled', but you can safely enable it because I know that drive supports it (although if you have a rather old mobo the ide controller might not).  Mine's enabled by default.  It allows for speedier data transfers.  But it shouldn't be affecting the main issue.

---

### Post by schwim on 2008-07-17
Hi there logos,

I'll pull the side on the computer tomorrow and see what I can see in regards to how the drive is connected.  If I can't resolve the issue that way, I'll reset the bios.  Either way, I'm sure I'll be posting again tomorrow as I continue my leisurely and relaxing foray into dualbooting :)

Either way, I can't thank you enough for your help.  I really appreciate all the time you dumped into this.

thanks,
json

---

### Post by logos34 on 2008-07-17
don't mention it--I like troubleshooting, it helps exercise what's left of my brain

talk to ya later

---

### Post by schwim on 2008-07-17
In continuation, looking into it, I see only one IDE slot on the mobo, and the cable's master is the drive and slave is the cd drive.  Both were set to master & slave, respectively.  There are five SATA ports on the mobo, and one PCI card has an IDE cable running from it, but it's just lying on the bottom of the computer.

I disconnected the cd drive and set the drive to cs and on startup got a chain of four error beeps.  I could not even get to the bios, so I set it back to master.

Leaving the cd drive disconnected, I tried detecting the drive in the bios again, but still no go.

That's where I'm at.  I've not tried repairing the boot sector with the Win install disk, as I wanted to save that for last.  It seems like giving up.  Plus, if it doesn't work, I'll be even more sad :)

thanks,
json

---

### Post by logos34 on 2008-07-17
> **schwim said:**
> ...and one PCI card has an IDE cable running from it, but it's just lying on the bottom of the computer.

That appears to be a leftover PCI IDE host controller card--maybe taking that out would help...or else connecting the drives to it instead.  Try removing it first, see if the drives are detected in the Bios. 

I'm fresh out of ideas...don't know what to suggest other than flashing the Bios with a newer version or resetting it to the factory default (look for a jumper on the motherboard, or else remove and replace the CMOS battery)

---

### Post by schwim on 2008-07-18
Hi there logos,

I think I [found the cause](http://ubuntuforums.org/archive/index.php/t-233540.html) of my problem.  The JTMicron controller on my [p965 Neo mobo](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=265) is more than likely the cause of all my troubles.  It seems that a lot of people have the very same problem.  I was able to get GRUB to work by connecting a SATA drive to the SATA4 port on the board, but I never figured out how to get my IDE drive to get detected properly.

I figured the least I could do after you helped me is let you know what was causing the problem :)

thanks,
json

---

### Post by logos34 on 2008-07-18
oh, so you have a board with one of those notorious jmicron chips!  Yeah, that caused a hug headache a while back--there were lots of threads on it.  I wish I'd have thought to ask your mobo model, I could have found it immediately in the ubuntu wiki (hardware lists).

---

### Post by schwim on 2008-07-19
Well, I got my win install back by repairing the MBR.

I've got two quick questions:

1) The linux install is still on the disk and Kubuntu installed an option at bootup that would allow me to boot the cd.  It's still there.  Can I point that to the actual linux install(instead of the cd that is no longer there)?  ie.  Is there alternate method to grub to get to the linux install?

2) If I can't use that boot option, how do I get rid of it?

thanks,
json

---

### Post by logos34 on 2008-07-19
> **schwim said:**
> Well, I got my win install back by repairing the MBR.

I've got two quick questions:

1) The linux install is still on the disk and Kubuntu installed an option at bootup that would allow me to boot the cd.  It's still there.  Can I point that to the actual linux install(instead of the cd that is no longer there)?  ie.  Is there alternate method to grub to get to the linux install?

2) If I can't use that boot option, how do I get rid of it?


You mean you restored the windows bootloader to the MBR?

You could try booting ubuntu from windows, by writing grub to the first sector of sda5, then copying it to widows C:\ drive and add entry to boot.ini

---

### Post by pdubs on 2008-07-19
Hi guys, I'm new to ubuntu and have received the same error message as schwim, so I'm going to add my problem to this thread.  One difference is that my installation was ubuntu, not kubuntu.  Please let me know if my question would be better on its own.  

I've installed 8.04 on an older desktop of mine - a dell 8200.  After doing some research I decided to install with a dual boot (I have XP previously).  I went through the installation off the Live CD without a hitch, but when I removed the CD and attempted to boot from the hard drive, my computer halted with "Error 21" at GRUB.  

I have two hard drives in the computer.  From what I can remember when I added the second drive in 2002, the hard drives are IDE.  I believe that in XP, my C: drive was NTFS and my D: drive was FAT32.  I had much more free capacity on the D: drive, so my intention was to partition Ubuntu there.

When I installed Ubuntu, only the D: drive came up as an option during the partition process.

I am now running off the live CD, and based on logos34's earlier instructions to schwim, I have run:

sudo fdisk -l 

with the following result:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4865    39045982+   7  HPFS/NTFS

Disk /dev/sdb: 46.1 GB, 46103371776 bytes
255 heads, 63 sectors/track, 5605 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ec2acd
[FONT="Courier New"]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2339    18787986    c  W95 FAT32 (LBA)
/dev/sdb2            2340        5605    26234145    5  Extended
/dev/sdb5            2340        5512    25487091   83  Linux
/dev/sdb6            5513        5605      746991   82  Linux swap / Solaris
[/FONT]
If it's not already obvious, I'm fairly new at this, but from what I can tell, in Live CD fdisk is able to tell that I have two hard drives, and further that the second drive (sdb) contains a linux partition and a linux swap in the sdb2 range.  It looks to me (and I may be speculating beyond my abilities here) that the "*" for "Boot" should maybe be next to /dev/sdb2, and not next to the "sdb1" partition, which I believe is the partition representing the remaining files on the D: drive in XP.  

If I have this right, can someone please tell me if there is a command line or some other way to move the boot to point to sdb2?  Or, if I'm off, I would appreciate any guidance.

Thanks!

---

### Post by logos34 on 2008-07-19
pdubs,

The * boot flag is not causing a problem. Only windows cares about it (i.e. the windows system partition needs to be 'active')...linux doesn't need it to boot.  True it's a data dump partition, so it shouldn't be there.  You can remove it later.

Boot from the live cd, mount root, and check out your /boot/grub/menu.lst.  The 'root' lines for ubuntu should read '(hd**1**,4)' -- i.e. sd**b**5, since the boot drive is the XP drive sda.  (hd0). [edit]

[Reinstall grub to the mbr.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by pdubs on 2008-07-19
logos34, thanks for the quick reply.

I was able to mount root and edit /boot/grub/menu.lst.  The root was (hd1, 4).

I'll work on reinstalling grub to the MBR and post back on how that turns out.

Thanks again

---

### Post by logos34 on 2008-07-19
sorry, typo -- I put sda5 when it's sd**b**5 you want.  Try it again

Then

sudo gedit /media/sdb5/boot/grub/menu.lst

---

### Post by pdubs on 2008-07-19
Thanks.  I was able to edit grub's menu.lst, and I found that the root for ubuntu was set to hd(1,4).

I followed the instructions in [the thread logos34 provided]("http://ubuntuforums.org/showthread.php?t=224351") on how to install grub from the live CD.  I first followed Tosk's post on mounting proc and udev, and then ran catlett's commands:

sudo grub
find /boot/grub/stage1  <= this command returned hd(1,4)
root hd(1,4)
setup (hd0)
quit

Everything seemed fine, but when I went to reboot, I still received "Error 21" at the grub menu.

Now, to make matters worse, when I try to boot from the Live CD, after the initial language selection and choosing to run ubuntu from CD, I receive the following text and a prompt:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ 

With a cursor at the end.  I'm totally puzzled by this.  How do I restore the Live CD to run the ubuntu GUI?  Any other suggestions on getting past the grub error?

Thanks again for your help!

---

### Post by logos34 on 2008-07-19
pdubs,

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

check the Bios hard disk settings for sdb.  

Or try Super Grub Disk to reinstall bootloader.

Or...you could write Grub to the MBR of the ubuntu disk, i.e.:

> root (hd[COLOR=Red]1[/COLOR],4)
setup (hd[COLOR=Red]1[/COLOR])then switch the Bios boot disk priority so sdb is first on the list.  

Reboot and if you get the grub menu screen, press 'e' on the highlighted selection, 'e' again on 'root' line and change to (hd**[COLOR=Red]0[/COLOR]**,4)--counterintuitive, I know, but you're now booting from that disk so it becomes (hd0).  'b' to boot.  If it works make the change permanent once inside ubuntu by editing menu.lst

---

### Post by pdubs on 2008-07-20
OK, problem solved for me.  I went into BIOS and it turned out that the second hard drive was "off" instead of "auto".  I don't know why I didn't see this when I reconfigured my boot settings, but thank you for directing me back to the manual and to check my BIOS settings.

---

### Post by logos34 on 2008-07-20
Glad to help.  Mark as 'Solved' (>thread tools)

---

