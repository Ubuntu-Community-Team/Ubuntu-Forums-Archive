---
title: "Grub doesn't recognize Vista installation"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Waelwulf on 2007-07-30
Well I tried to get a dual boot set up working and I paid the price. The steps I took, based on a guide, are outlined below:

First of all, I have 2 hard drives, Vista was installed on one of them, I did a fresh install of Ubuntu Feisty Fawn on the other one.

1. Booted into GParted environment and partitioned the second hard drive with no information on it into the swap file and half the drive's free space for Ubuntu.

2. Saved changes, took out GParted disc and rebooted, "No operating system detected" showed up on a black screen. I thought this might be trouble by this point but I had read that Grub remasters your boot record anyway so I forged on.

3. Booted into Ubuntu Live CD and installed.

4. Ubuntu succesfully installs, I reboot. Grub detects no other operating system and doesn't even greet me with that multiboot screen, instead just jumping into Ubuntu.

Let me know any information I can provide and I would be happy to. It's very important I retain the information on my Vista disc as I, stupidly, didn't make a backup.

I'm running an Intel Core 2 CPU in the range of 1.5 Ghz or so with 2 gigs of RAM and Geforce Go 7600 on an HP dv9048ea notebook.

---

### Post by Waelwulf on 2007-07-30
The guide I used is here: [http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html]("http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html")

---

### Post by MQMike on 2007-07-30
Hi Waelwulf,

Just simply reading the account you gave us, I’d bet the house that you inadvertently killed the Windows partition/OS somehow, maybe reformatted it by accident in GParted.  I’d say the problem happened in GParted.  I do presume btw that you know how to use GParted, but accidents happen; in GParted, you gotta make sure that the correct hard drive is selected from that drop-down list and all that stuff I'm sure you know very well.

While Vista may require a little extra attention here and there, the dual-boot setup for your configuration is straightforward and follows standard GRUB methods and etc.



***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by meierfra on 2007-07-30
MQMike is probably right, but  before losing all  hope we should check on what is really going on. Could you post the output of:

```
sudo fdisk -l
```
and 
```
 sudo gedit /boot/grub/menu.lst
```

---

### Post by Waelwulf on 2007-07-30
Thank you for your speedy replies! Well, I can access all my old files on my other hard disk and everything from the Ubuntu desktop. I even set my wallpaper to an image on that drive I had. I was very careful with GParted as I have some experience in breaking computers in my younger days. 

tao@Argent:~ $ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7041    56556801   83  Linux
/dev/sda2            7042       14337    58605120    b  W95 FAT32
/dev/sda3           14338       14593     2056320   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117218304    7  HPFS/NTFS

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
# kopt=root=UUID=20363df2-1809-448e-8e1c-78776fcbfe08 ro

And here's the other one you wanted:
 
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=20363df2-1809-448e-8e1c-78776fcbfe08 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=20363df2-1809-448e-8e1c-78776fcbfe08 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by MQMike on 2007-07-30
Sorry, looks like he just needs a boot entry for Vista;

title   Vista
rootnoverify  (hd1, 0)
makeactive
chainloader +1

Edit the menu.lst using sudo, adding this boot entry just before the *** Begin Automagic Kernels List
File-Save, File-Exit

If that doesn’t work, then you can try the map command:

title   Vista
map (hd0)  (hd1)
map  (hd1)  (hd0)
rootnoverify  (hd1, 0)
makeactive
chainloader +1




How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by Waelwulf on 2007-07-30
Error 11: Unrecognized device string pops up after Grub loads and if I press enter on Vista. No luck. I tried both entries you suggested.

---

### Post by MQMike on 2007-07-30
OK, then . . .

I’m a little bit fox-ed here because although Vista was there first, it’s showing up as sdb1, on the “second” drive, and Linux on sda, the “first” drive.  However, that’s just how Linux sees it (using sudo fdisk –l).  
GRUB may see it differently.
We do have to know how GRUB sees these drives.
In Ubuntu (or in Live CD Ubuntu), you can get a terminal and type
sudo grub
and you’ll then get a GRUB prompt, grub>,
and at that grub prompt, type
geometry (hd0)   #then press Enter
and see what you get – what drive is the first GRUB drive hd0?

Also for 
geometry (hd1)

---

### Post by Waelwulf on 2007-07-30
grub> geometry (hd0)
drive 0x80: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is fat, partition type 0xb
   Partition num: 2,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

It bothers me Grub doesn't know the other hard drive is NTFS. GParted sees that it is when I boot it.

---

### Post by MQMike on 2007-07-30
I re-read all this again, and what might be missing here is that GRUB should be installed to the MBR of the hard drive that is the first BIOS-bootable hard drive (which usually is the Windows drive, but we are not sure about that here yet).  Usually, this is done during the installation of Ubuntu, where you are asked where do you want to install GRUB?  Do you recall doing that?

That tip, what I just said,
combined with knowing where everything is here.
Is hd0 Windows or Linux?
And what's on hd1?

---

### Post by MQMike on 2007-07-30
We posted in passing.

So it looks like hd0 is where Linux is, and then hd1 must be where Vista is.  So what we did above with the menu.lst was correct, in terms of naming the drives properly.  Windows is on (hd1, 0).

You can try to re-install grub to (hd0):

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hd0, 0)          # (hd0, 0) is the partition of your "main" Linux OS
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

This combined with that map-dance boot entry above.

Make sense?

---

### Post by Waelwulf on 2007-07-30
Your assumptions were all right Mike but it didn't work. Same error 11 reared its ugly head.

---

### Post by MQMike on 2007-07-30
Hmmm…

Unless we missed some detail or have a typo, we’ve done the standard stuff, GRUB-wise:

--  Windows is on a non-first HD, so we fixed that using the map-dance in the Vista boot entry.
--  There was evidence that the GRUB boot (Stage_1) in the MBR of the first BIOS-bootable HD was not setup, so we re-installed GRUB to hd0, which we believe is the first hard drive in BIOS boot order.
That usually fixes it.

I’ll have to think about it, and recheck the details.  Maybe someone else will see something we are missing.  Unless it’s something quirky about Vista?
(That *definitive Vista dual booting guide * no doubt works, but you’d have to look at it carefully to see if it would require starting from scratch.)
 . . . . .

---

### Post by MQMike on 2007-07-30
Both your HDs are SATA drives?

---

### Post by Waelwulf on 2007-07-30
I was worried we might hit this wall. I've done a check over the other guide and as far as I can see the only worrying difference is they broke down their partition to non-allocated in Vista, whereas I did it in GParted, perhaps crippling the boot record for Vista in the process and causing it to "ghost" under the radar of Grub. 

Of course I could be wrong and I hope I am because I really don't want to go through another drawn out install process with Vista.

---

### Post by Waelwulf on 2007-07-30
I'll check, be right back.

---

### Post by MQMike on 2007-07-30
"Error 11: Unrecognized *** device string *** pops up after Grub loads and if I press enter on Vista. No luck. I tried both entries you suggested."

I'm just throwing out some ideas to work on, as I may run out of time on my end for awhile.

I wonder, too, if the UUIDs are correct?  See it in the kernel line?
These are contained in your filesystem table, /etc/fstab in Ubuntu.

To see your UUIDs, use the command:   
$ ls /dev/disk/by-uuid/ -alh   
(Note: “ls” is “l” as in “list”; and “-alh” is also with an “l” as in”list”)

The UUIDs in fstab must be correct for each device  (hard drive, partition), and what appears in that kernel line must match up as well (the kernel line passes the root device to the kernel of Ubuntu).

---

### Post by MQMike on 2007-07-30
In BIOS,

is BIOS set to boot from the drive that contains Linux?  (It should, the way we have it.  But I am a bit uncomfortable that Vista somehow ended up on what looks like the "second" HD . . .)

---

### Post by meierfra on 2007-07-30
Try 

title Vista
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0, 0)
makeactive
chainloader +1

---

### Post by Waelwulf on 2007-07-30
Whoops, just went on a hunt for those drives, according to GParted they are both ATA model ST9120821AS.

And here's your UUIDs, be right back with the BIOS stuff.

tao@Argent:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 120 2007-07-30 18:42 .
drwxr-xr-x 5 root root 100 2007-07-30 18:42 ..
lrwxrwxrwx 1 root root  10 2007-07-30 18:42 20363df2-1809-448e-8e1c-78776fcbfe08 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-07-30 18:42 422bc5d6-6b88-45d8-bdac-c958bcaf9530 -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-07-30 18:42 46AE-07C9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-07-30 18:42 9A8CCDF18CCDC7C9 -> ../../sdb1
tao@Argent:~$

---

### Post by MQMike on 2007-07-30
lrwxrwxrwx 1 root root 10 2007-07-30 18:42 20363df2-1809-448e-8e1c-78776fcbfe08 -> ../../sda1

That UUID looks correct in the kernel line for Ubuntu.

---

### Post by Waelwulf on 2007-07-30
Looking at what I know of the BIOS, which is little, it looks like there's only the option to set the boot order with "notebook hard drive" right after my cd-rom drive, no option between two of them or anything of the like. So no luck there I think. And trying the new Vista command only made Grub show up with another two options for a Ubuntu boot with the same Error 11 popping up trying to select Vista.

---

### Post by MQMike on 2007-07-30
I'm not sure what's going on.
You did say:

“Whoops, just went on a hunt for those drives, according to GParted they are both ATA model ST9120821AS.”
and
you’ve got “Geforce Go 7600 on an HP dv9048ea notebook.”

So those are PATA (or IDE) drives, not SATA, right?
I hope your motherboard isn't having trouble with the ATA.

For example,
If your motherboard uses the Intel P965 Express chipset with the ICH8 Southbridge,
PATA drives are controlled by an outboard jMicron 363 controller, and Linux has had issues with this jMicron chip.  Dual-booting issues have surfaced.

I hope your system doesn't have some glitch with these ATA drives.  I don't know.

---

### Post by MQMike on 2007-07-30
No -- scratch that post about ATA -- I looked up your drives and they are both serial ATA = SATA.
So there should be no issue of hardware problems vs Ubuntu there (that I know of).

---

### Post by Waelwulf on 2007-07-30
I'll keep a close eye on this post Mike, if you have any other thoughts, don't hesitate to let me know. Thank you for all your help so far, I really do appreciate it.

---

### Post by MQMike on 2007-07-30
Yeah, I'm stumped.  I've been a this for some 18 hours today, so maybe I'm pooped and misising something obvious.

Sorry to repeat this, but it's a puzzle how Vista ended up on the "second" hard drive even though it was installed first, usually to your computer's first-bootable drive . . .?

---

### Post by meierfra on 2007-07-30
I have no idea what is going on. But could you post your current menu.lst? Maybe  there are some misprints you have been missing.

---

### Post by Waelwulf on 2007-07-30
Funny thing, I brought it in for repairs just a week or so ago, they may have swapped the drives. Or rather, what ended up having me install a fresh copy of Vista on either of the then-empty drives (they were holding my data for me on their servers) may have been the cause of installing it on the second drive instead of the first.

---

### Post by Waelwulf on 2007-07-30
Of course now I find the exact same solution presented to me, really very frustrating. I don't know why I do this to myself.

---

### Post by meierfra on 2007-07-30
Did you try to mount your windows partition in Ubuntu? If that works you can at least rescue your data.

(Let me know if you need help with mounting)

---

### Post by MQMike on 2007-07-30
"Of course now I find the exact same solution presented to me, really very frustrating. I don't know why I do this to myself."

We all do it to ourselves!  :)
It's kind of funny, but it sometimes isn't.

In the best of all possible worlds, and as goofy as Vista *may* be (too soon to tell, it's so new), Vista should go on the first BIOS drive in boot order ((hd0, 0)--first partition, too), then Ubuntu can go anywhere and it'll probably work, esp following that Definitive Guide link above, and in any case, the chance that GRUB methods work will be pretty darned close to 100%.

---

### Post by MQMike on 2007-07-30
I think meierfra wants to be sure you have all the commas and details in place, and I agree that’s the thing to do right now – even one thing could throw it.
I’m letting it rest for now, unless I get a brainstorm.

---

### Post by Waelwulf on 2007-07-31
Okay, I'm reinstalling the OS again. Here's what I plan to do:

1. Reformat drives with GParted before Vista or Ubuntu install
2. Install Vista on sda2
3. Install Ubuntu on sdb1
4. (Hypothetical) Install Mac OS X on sdb1 (Fat32 partition)

Now, if hypothetically I were to install Mac OS X on the other partition it shares sdb1 with Ubuntu, I assume I would have to make a Grub bootloader entry. Are you able to advise me on how that entry would look? As well as perhaps the Vista entry?

---

### Post by Waelwulf on 2007-07-31
According to the Vista install, sdb1 is hard drive 0 and should be the first to boot, so I don't think that was the problem before. I just reformatted and repartitioned. Updates to come.

---

### Post by MQMike on 2007-07-31
- - -   Vista install:  

In would at least look at the Definitive Guide I posted the link to.
The Vista entry is the same as for XP, just be sure and use rootnoverify instead of root:

title  Vista
rootnoverify (hd0, 1)    # is that right?  second partition?
makeactive
chainloader +1

- - -   I’m all confused now about your drives, Vista is going on sda now, isn’t that hd1?  
Doesn’t matter -- All that matters is that *you* are clear on it.

- - -   I don’t know anything about Mac OS X.
I don’t understand installing it on the same partition as Ubuntu.

---

### Post by meierfra on 2007-07-31
> grub> setup (hd0) # This assumes (hd0) is your “main” booting hard drive MBR

I think that's where we went wrong yesterday.

Windows was installed on sdb=hd1. So I bet also MBR was on hd1.

---

### Post by jdimauro on 2007-08-25
Hi folks,

I'm having a similar problem.  I used gparted originally to try and make my Linux partition a bit bigger but after messing with it for a few hours and not being able to get two partitions to merge I said to heck with it and deleted my Linux partition, made a new larger one, and reinstalled.  During the reinstall process I noticed it was no longer recognizing my Vista partition.  When I booted into Grub the option was no longer there.  I've tried a few things but I keep getting Error 11 if I try and load Vista.  The output of  sudo fdisk -l is:

[I]Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6482    52063232    7  HPFS/NTFS
/dev/sda2            6483       11103    37118182+   b  W95 FAT32
/dev/sda3   *       11104       36108   200852662+  83  Linux
/dev/sda4           36109       36483     3012187+   5  Extended
/dev/sda5           36109       36483     3012156   82  Linux swap / Solaris[/I]

sda1 is the Vista partition and sda2 is for holding files I need to trade between the two os'.  The output of  sudo gedit /boot/grub/menu.lst is:
[I]
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
# kopt=root=UUID=d19db752-ac30-4c51-9dc6-96544dae1e3d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d19db752-ac30-4c51-9dc6-96544dae1e3d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d19db752-ac30-4c51-9dc6-96544dae1e3d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/I]

This is the default without any of the changes I made to try and add Vista.

Any ideas? 

Thanks!
John

---

### Post by merlinus on 2007-08-25
You might try adding this to the end of /boot/grub/menu.lst --

title  Vista
rootnoverify (hd0,0) 
makeactive
chainloader +1

Also, if you place a hashmark (#) before the line near the top of the file that says hiddenmenu, grub will appear.

-merlin

---

### Post by jdimauro on 2007-08-25
Thanks Merlin!  It's starting to load now but then says BOOTMGR is missing.  Do you know if  there's a way to restore the Vista boot manager (I think that's what it is) without having to reinstall it?

-John

---

### Post by merlinus on 2007-08-25
You do not want to do this, or ubuntu will not load.

Set the boot flag on the ubuntu partition, and remove it from the vista one.

gparted live cd works best:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can see the boot flags with:

```

sudo fdisk -l

```

-merlin

---

### Post by jdimauro on 2007-08-25
Ok.  I've tried switching the boot flag a few times, both with the gparted live cd and within Ubuntu.  For some reason the flag keeps getting switched back to the Vista partition when I reboot.

Thanks for the help Merlin!

-John

---

### Post by merlinus on 2007-08-25
Very strange.  Others have not had this problem.

You might take a look in your BIOS to see if there is some setting that is booting vista.

Also, you might try reinstalling grub to the mbr.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

It will probably be (hd0,2) for root and (hd0) for setup.

And I did see from your posting of sudo fdisk -l that the boot flag was set to the ubuntu partition.

-merlin

---

### Post by jdimauro on 2007-08-25
Thanks for all the help Merlin.  It's fixed now.  I used the Vista disk and it repaired it.  I would have responded sooner but we just had a big thunderstorm so I shut things down until it passed.  I wonder if using the x64 distro added to it by not recognizing the dual boot at first?  I originally installed the x86 version and everything was working fine.  After I messed with the partitions I switched to x64 (I have an AMD 64 cpu).  I'm going to reinstall with the x86 version and see what happens.

Thanks again!  The Ubuntu community is so friggin' helpful!

-John

---

### Post by merlinus on 2007-08-25
Glad it is working, and yes, we tend to be a zealous and helpful bunch.

Welcome!

-merlin

---

