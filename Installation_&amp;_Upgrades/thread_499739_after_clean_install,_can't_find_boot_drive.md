---
title: "after clean install, can't find boot drive"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by metafizx on 2007-07-12
hi forgive me complete n00b...

want to get away from XP and Vista horrors..so I downloaded Ubuntu 7.04 and booted to Ubuntu on the live cd successfully on a Hp Pavillion Laptop.

then I did a clean install (nothing else on the drive), and it completed successfully...but after I rebooted as prompted, the boot drive is not found.

am I missing something here ? :confused:

the laptop is a Pavillion Zv5000 with 40GB of HDD, and 256MB of RAM. Celeron CPU.

sorry if this has been answered, pls direct to the post (i looked but couldn't find anything ....)

---

### Post by Herman on 2007-07-13
Hello metafizx,
I haven't heard of that before, what do you mean "the boot drive is not found."?

Please type the error message like: "Grub error 15", or whatever it is, or describe as best you can what you see on the screen.

Also if you can, boot the Live CD and post the results from the following command here, ```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by metafizx on 2007-07-13
hi herman, thanks for the reply.

what I meant is after the live cd finished installing Ubuntu and said to reboot, once the laptop restarted, the bootloader did not run.

it seems like grub is setup wrong for the bootloader.


here's the output from the fdisk command...

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    75874994    37937466   83  Linux
/dev/hda2        75874995    78140159     1132582+   5  Extended
/dev/hda5        75875058    78140159     1132551   82  Linux swap / Solaris

Disk /dev/sda: 130 MB, 130023424 bytes
1 heads, 32 sectors/track, 7936 cylinders, total 253952 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32      253951      126960    6  FAT16

---

### Post by bulldog on 2007-07-13
I think you have a removable item like a flashcard or something in your computer.
Can you remove that and try again?

---

### Post by Herman on 2007-07-13
```
 Disk /dev/sda: 130 MB, 130023424 bytes
1 heads, 32 sectors/track, 7936 cylinders, total 253952 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32      253951      126960    6  FAT16
``` I agree with bulldog, (hello bulldog :) ),  it looks like you may have left a USB memory stick plugged in and if that was plugged in the whole time it is likely that GRUB is installed to MBR in the memory stick instead of in your hard drive.  Most computers BIOSes won't look for it there unless you specifically tell them to. (By pressing your F8 or F12 key for a list of devices, like this, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") . That's how mine works anyway, yours will probably be a little different.

I think the best thing to do would be to boot up with the Ubuntu Live CD and re-install GRUB to MBR in your first hard disk, like this, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.

That's if we guessed right and that's your problem. It won't hurt to try that anyway.
Then we might still need to edit your /boot/grub/menu.lst to get it working properly.

..or if you think it'll be easier, just re-install without the memory stick this time, if that's the problem, or did we guess wrong?

Regards, Herman :)

---

### Post by metafizx on 2007-07-13
hi guys,

thanks for the replies, ok...well, you are right that it is a flash memory stick, but it was not present during the install process, and was not plugged in during the boot.

I had only put the memory stick in to copy the results file from the fdisk output, since I am writing to you from a windows PC. so false alarm on the /dev/sda

it's something else..

I am really foggy from my unix days, and have been a slave to windows for years, so please forgive my ignorance...

but when I look at grub, the boot device seems to be /dev/hd0, but the linux partition is /dev/hda1

I guess the MBR is called /dev/hda0 but for some reason it's not being accessed on boot up.
and why is /dev/hda0 not shown from the fdisk output ?

---

### Post by bulldog on 2007-07-13
> **metafizx said:**
> hi guys,

thanks for the replies, ok...well, you are right that it is a flash memory stick, but it was not present during the install process, and was not plugged in during the boot.

I had only put the memory stick in to copy the results file from the fdisk output, since I am writing to you from a windows PC. so false alarm on the /dev/sda

it's something else..

I am really foggy from my unix days, and have been a slave to windows for years, so please forgive my ignorance...

but when I look at grub, the boot device seems to be /dev/hda0, but the linux partition is /dev/hda1

I guess the MBR is called /dev/hda0 but for some reason it's not being accessed on boot up.
and why is /dev/hd0 not shown from the fdisk output ?

The boot device should be hd0 and the partition should be hd0,1 or something like that.
Maybe you can post your menu.lst so we can have a look?

---

### Post by metafizx on 2007-07-13
so I went and attempted to reinstall grub using the live cd.

what's weird is when I ran the following, there was no output.

grub> root (hd0,0)

I expected to see something like the example :

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

when I ran :
grub> find /boot/grub/stage1
   
it resulted in :
(hd0,0)

there was no indication of an error, everything looked successful when I ran :
setup (hd0)

so something is wrong...just to ignorant to know what it is.

---

### Post by metafizx on 2007-07-13
here's menu.lst....

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=8f5737a3-52a7-4669-bbfb-3d495c80cf7e ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8f5737a3-52a7-4669-bbfb-3d495c80cf7e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8f5737a3-52a7-4669-bbfb-3d495c80cf7e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Herman on 2007-07-13
Okay, maybe here are a few things to check in your BIOS then.

First, please check you hard disk is being detected properly and it is set to auto in CMOS [    Make sure your hard disk is properly detected in your BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Making_sure_your_hard_disk_is_properly").

Secondly, check to make sure your hard disk is still in the list of bootable devices in your           boot priority. It is always possible for us humans to make a mistake when setting the CD-ROM drive to boot the install CD, and not notice the hard drive is now not in the list. (I'm human too, that's how I know).[ Changing the boot sequence in CMOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS").

Also ikn your BIOS, check in the hard disk boot priority, just to make sure.[ Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").

Another thing it might be is if your BIOS has an MBR write-protection feature enabled, that can stop GRUB from being installed. Normally that's to prevent boot sector viruses from affecting your MBR, but this time we want to write to your MBR to install GRUB, or more correctly the 'IPL' to make your MBR point to GRUB. Check your BIOS and make sure the antivirus or MBR write-protect is turned off, [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect").

>  what's weird is when I ran the following, there was no output.
grub> root (hd0,0)
I expected to see something like the example :
grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83 That might still be okay, in some of my computers I do get feedback and in others I don't get any feedback, I guess it depends on what kind of  BIOS the computer has.

That's all for now, see how you go,
Regards, Herman :)

---

### Post by metafizx on 2007-07-13
hi herman,

thanks a bunch for your help...as I think I am barking up the wrong tree now.

after you pointed me to the BIOS, I see that the hard drive is not being recognized.

what is weird WEIRD is that everything did install as I can access the hard drive with the live CD, however the BIOS doesnt "see" it. 

so for some reason it is "there" but BIOS ignores it. hmmmm...

I'll come back after I've figured out that issue.

thanks again for your help....even if it is because of hardware, the n00b learns...

---

### Post by Herman on 2007-07-13
Okay, if you have made any changes in your hardware, or even had a service technician working in your PC, you may need to open your computer's case and shine a light in there and check how your discs are plugged in and jumpered.

Be careful of course not to touch anything inside the case unless you know what you're doing.

If your IDE hard disk has a cable with black plugs, make sure your hard drive is jumpered as master and any other drive that might be connected to the other plug (CD-ROM drive maybe), is jumpered as slave.

If your IDE cable has a blue plug, a grey plug and a black plug it's a 'cable select' IDE cable. The blue plug goes in the motherboard socket, the black plug is for the master or number 1 hard disk and the grey plug is for the slave or number 2 hard disk or CD-ROM drive. With that kind of IDE cable you need to make sure your jumpers are set to 'cable select'. 

There should be stickers on each hard disk that will tell you how to place the jumpers for the setting you need according to the particular disc manufacturer's design.

If you're not sure what you're doing it might be best to get a service technician to do it for you, but you might be able to see with a light if that's maybe what's wrong or not. 

If you do decide to reach in your case yourself (I do everything myself), you will need to be aware of 'ESD', (ElectroStatic Discharge), which is just static electricity. A small spark of static that you can't even feel can ruin your computer, so be sure to at least touch case first to equalize any difference in charge. 

When you have the hard disc plugged in and jumpered correctly it should be detected properly in most modern BIOSes automatically and instantly without the user having to do any more work. :)

Maybe you already know all that but I though I'd type it out in case it helps anyone, there are sometimes people reading these posts at a later date trying to fix their own problems who might benefit.

Regards, Herman :)

---

### Post by metafizx on 2007-07-13
thanks a bunch Herman...your info is great. I know now what I have to do before I get back to this thread.
there is something weird with the BIOS.  until this is solved, nothing will work right..



> **Herman said:**
> Okay, if you have made any changes in your hardware, or even had a service technician working in your PC, you may need to open your computer's case and shine a light in there and check how your discs are plugged in and jumpered.

Be careful of course not to touch anything inside the case unless you know what you're doing.

If your IDE hard disk has a cable with black plugs, make sure your hard drive is jumpered as master and any other drive that might be connected to the other plug (CD-ROM drive maybe), is jumpered as slave.

If your IDE cable has a blue plug, a grey plug and a black plug it's a 'cable select' IDE cable. The blue plug goes in the motherboard socket, the black plug is for the master or number 1 hard disk and the grey plug is for the slave or number 2 hard disk or CD-ROM drive. With that kind of IDE cable you need to make sure your jumpers are set to 'cable select'. 

There should be stickers on each hard disk that will tell you how to place the jumpers for the setting you need according to the particular disc manufacturer's design.

If you're not sure what you're doing it might be best to get a service technician to do it for you, but you might be able to see with a light if that's maybe what's wrong or not. 

If you do decide to reach in your case yourself (I do everything myself), you will need to be aware of 'ESD', (ElectroStatic Discharge), which is just static electricity. A small spark of static that you can't even feel can ruin your computer, so be sure to at least touch case first to equalize any difference in charge. 

When you have the hard disc plugged in and jumpered correctly it should be detected properly in most modern BIOSes automatically and instantly without the user having to do any more work. :)

Maybe you already know all that but I though I'd type it out in case it helps anyone, there are sometimes people reading these posts at a later date trying to fix their own problems who might benefit.

Regards, Herman :)

---

### Post by Herman on 2007-07-13
>  there is something weird with the BIOS.  until this is solved, nothing will work right.. If you checked and you don;t think it's the way your hard drives are jumpered and plugged in another thing I've run across is BIOS hard diskdrive size limitations.
I have an older computer that came with a 6.0 GB hard drive that died of old age. I tried to replace it with a 40.0 GB hard drive and it gave the exact same symptoms as you are describing. I could install okay, but it wouldn't boot.
It turned out I was up against the 33 GB hard disk drive BIOS barrier. I tried everything but in the end I gave up and bought a 30.0 GB hard disk instead. That solved my problem.
The 40.0 is now in an external USB enclosure, and it's extremely useful there instead.

Could that be your problem maybe? 
                                     Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
                                      You can check the date of your computer's BIOS by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information").

Regards, Herman :)

---

### Post by metafizx on 2007-07-13
that's really interesting..

I knew there were some BIOS limitations in the past on HDD capacity, but I didn't know there were so many iterations. wonder what the current limitation is...drives are pretty huge.

I am working on getting a different drive to try...will post when I get the results... thanks again.

---

### Post by metafizx on 2007-07-14
hi,

Ok this problem is a non-problem..the hard drive was just not being recognized by the BIOS and a replacement drive is working fine. 

Installed Ubuntu successfully and no issues with Grub. 

thanks for all the help, sorry it turned out to be hardware.

what was strange is Ubuntu did install "successfully" on the first hard drive, but the BIOS ignored that particular drive, so it wouldn't boot. 
I would've thought that the drive would have been inaccessible, and the install would fail.. but somehow it went through the install process.
no other sort of error was evident, and all the Ubuntu files were there on the drive. weird !!

---

### Post by Herman on 2007-07-14
He-He, well that's computers for you! :)
I'm glad you have Ubuntu installed okay now. congratulations and welcome to Ubuntu! :guitar:
Regards, Herman :)

---

