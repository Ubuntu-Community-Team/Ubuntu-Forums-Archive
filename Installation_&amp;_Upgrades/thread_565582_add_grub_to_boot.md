---
title: "add grub to boot"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by klaasth on 2007-10-02
[http://users.skynet.be/fa206098/schijfindeling.JPG]("http://users.skynet.be/fa206098/schijfindeling.JPG")

Hi,
I recently installed ubuntu on my desktop. But I could'nt start xp anymore unless i fix it wit fixmbr on windows recovery CD, but now I don't see the dual boot screen of grub anymore. How can I add it mannualy? On the picture in the link you can see my harddisk configuration, because I don't understand the hd0,0 commands etc. Can anyone please help me?

Thank you!

---

### Post by Herman on 2007-10-02
Hello klaasth,
The easiest way to fix that would be to download for yourself a copy of [Super Grub Disk]("http://geocities.com/supergrubdisk/").
Super Grub Disk is free and it's only a small download.
That comes in CD, floppy disk or USB form, so choose whichever file type is right for you and download it and make some kind of disc out of it. 
This web page might help you, [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

You will be able to boot either Windows or Ubuntu with Super Grub disk regardless of the state of your MBR.
You will be able to re-install GRUB to MBR, easily too, and do quite a lot of other jobs with boot loaders if you ever need anything else.

When you have used Super Grub Disk to restore your Ubuntu's GRUB to MBR, you will probably still be unable to boot Windows from GRUB yet until you fix your /boot/grub/menu.lst file in Ubuntu, there will probably be something wrong with that that will be easy to fix. 
For now at least you can boot Windows with Super Grub Disk until I or someone here can help you fix your GRUB.

To fix your GRUB, we will need a copy of your /boot/grub/menu.lst file, or at least the bottom half of it. You can get that like this:
```
sudo gedit /boot/grub/menu.lst
```And we will alsos need to see what your partition numbers are from this command: ```
sudo fdisk -lu
``` If you can post the output from both of those commands here after you get Ubuntu booted then I or someone here can help you fix your GRUB to boot both Ubuntu and Windows.

Regards, Herman :)

---

### Post by klaasth on 2007-10-02
I did what you said, i booted the grub bootloader en I fixed the Ubuntu MBR, now I can't boot from xp but from Ubuntu. The content of the files are:
the content off sudo gedit /boot/grub/menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		4

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
# kopt=root=UUID=42403ee7-9163-47d5-a026-051c1f4271c3 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42403ee7-9163-47d5-a026-051c1f4271c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42403ee7-9163-47d5-a026-051c1f4271c3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42403ee7-9163-47d5-a026-051c1f4271c3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=42403ee7-9163-47d5-a026-051c1f4271c3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


the content of sudo fdisk -lu
> Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS
/dev/sda2        62926605   466254494   201663945    5  Uitgebreid
/dev/sda3       466254495   488392064    11068785   83  Linux
/dev/sda5        62926668   297395279   117234306    7  HPFS/NTFS
/dev/sda6       297395343   465178139    83891398+   7  HPFS/NTFS
/dev/sda7       465178203   466254494      538146   82  Linux wisselgeheugen

Schijf /dev/sdb: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders, totaal 234441648 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS


Please help me so i can boot Ubuntu and Xp without problems and thank you for your good help and support

---

### Post by Herman on 2007-10-02
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``````
                              Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes

  Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS
/dev/sda2        62926605   466254494   201663945    5  Uitgebreid
/dev/sda3       466254495   488392064    11068785   83  Linux
/dev/sda5        62926668   297395279   117234306    7  HPFS/NTFS
/dev/sda6       297395343   465178139    83891398+   7  HPFS/NTFS
/dev/sda7       465178203   466254494      538146   82  Linux wisselgeheugen

Schijf /dev/sdb: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders, totaal 234441648 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS
```Hello klaasth,
Is your Windows operating system in partition 1 of your first hard disk? Because if it is, that should boot it okay.

Since you already told me that doesn't work, I can only guess that your Windows might be in one of the logical partitions in your first hard disk, or that might be your Windows in your second hard disk.

If Windows is in your second hard disk, try this, 
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```Try adding that to the bottom of your menu.lst file (just paste it on the bottom and save the file before closing). Then reboot and see if it works. I'm only guessing what the problem might be. 
Otherwise, can you tell me which partition is your Windows partition, please?

And also, can you please tell me what kind of error messages you are getting, (if any), or what it looks like when Windows tries to boot up? (If it still won't work).

Regards, Herman :)

---

### Post by 3579545 on 2007-10-03
today i started playing aroud with some installation do's and don'ts. I had win2000 on and wanted to do it like this.

dos 6.22
win 2000
xubuntu

so I really screwed it up like many times in the past. So I did some reading about hiding the windows partions and the guy who insatlled 8 win and 127 distros blah blah blah.

I just sighned on and started to browse the forums and this one poppped out at me. Now I know I may be interupting but hey, sorry. Does anyone have a good procedure on how to install dos-win2000-xubuntu in that order? 

Will that download you mentioned help. I have done a LLF on the drive so the disk partions should be clean. Any help would be sweet?


3579545......not quite the speed of light

---

### Post by Herman on 2007-10-03
Hello 3579545,
>  Will that download you mentioned help Yes, I would recommend anyone who is interested in dual or multiple booting should have a [Super Grub Disk]("http://geocities.com/supergrubdisk/"), they are free and only a small download, (the latest CDROM version, 0.9598 is only 394 KB), and can really give you peace in your mind that if something does go wrong with the boot loader, almost no matter what, you'll still be able to boot somehow until you get your system set up properly.  :)

(Except for partition table problems, which are not the same as boot loader problems, although they can also mean you can't boot, so you should still make a backup of your data before doing any hard disk partitioning work).

I haven't tried installing DOS as a separate operating system, but I have set up Ubuntu with Windows 2000 a few times for various friends, 

I usually start with Windows installed first and then install Ubuntu after that. I'm not sure about Windows 2000 but I do know that the Windows 98Se that I have will refuse to install if it detects an 'extended' or a 'logical' partition in the partition table, I guess just to be difficult and try to make it incompatible with Linux. That's one reason why Windows sometimes needs to be installed first. (Well if it's only the swap area that could be temporarily deleted). The other reason is just that some people have computers that came with Windows XP 'Recovery CDs instead of 'Installation' CDs, so they can't install XP to a partition, they can only wipe the whole hard disk and re-install 'to the state it was when it left the factory'.

You could install DOS, then use Super Grub Disk's GRUB to 'hide' your DOS partition while you install Windows 2000. Just boot Super Grub Disk, select your language, (perhaps English), and go 'English Super Grub Disk'--'Boot and Tools'-->'Hide Partition', and then choose your hard disk, then select your partition to hide, (whichever is your DOS partition), and go back and exit Super Grub Disk while you install Windows 2000.

If you already have Windows 2000 it doesn't matter, just do it the other way around, hide Win 2000 and install DOS.

Then if you install Xubuntu last, the GRUB installer for Xubuntu will most likely detect your DOS and Windows 2000 installations and add them automatically to your new GRUB menu.
You still might need to edit the commands a little by hand, I'm not sure, maybe you'll need to add GRUB's 'hide' and 'unhide' commands to the boot entries yourself, or something like that, but that will be easy. Here's a link about that, [More than one Windows on the same disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk")

Regards, Herman :)

---

### Post by klaasth on 2007-10-03
My windows is on the first hard disk (the second is only an external backup drive) and on the first partition and i am certain that it is an active primary partition. But when I am dual booting. Xp gives the following error. Couldn't find or missing ntoskrnl.exe in main windows folder. I only can switch form operating system when I overwrite the MBR everytime when I want to change.
Thanx for your help

---

### Post by kubu_for on 2007-10-03
I have another problem. I do not want to place GRUB in HD. I would like to boot from CD and to load ubuntu from extern USB. Is it possible?

I've installed ubuntu (7.04) on my extern HD. I also managed somehow to create boot CD. I copied vmlinuz, and initrd.img together with grub and created boot CD. Menu.lst is also ok. Boot works fine and ubuntu as well, but there are two problems:
- after any kernel update I need to recreate boot CD with new kernel files
- CD drive is locked and cannot be used from ubuntu.

Could anyone help me to solve these problems? Is it possible to place boot once on CD and then to load ubuntu from extern HD? This would be the ideal problem solution... Or, is it possible to unlock CD after booting so that I can use CD drive for normal work?

This is my drive list:

Disk /dev/sda:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4865 39078081 7 HPFS/NTFS
/dev/sda2 4866 9729 39070080 f W95 Ext'd (LBA)
/dev/sda5 4866 9729 39070048+ 7 HPFS/NTFS

Disk /dev/sdb:


Device Boot Start End Blocks Id System
/dev/sdb1 * 1 474 3807373+ 83 Linux
/dev/sdb2 475 60047 478520122+ 83 Linux
/dev/sdb3 60048 60801 6056505 f W95 Ext'd (LBA)
/dev/sdb5 60048 60801 6056473+ 82 Linux swap / Solaris

this is how I boot it from grub (in menu.lst)

title Ubuntu, kernel 2.6.20-16-generic (from CD sdb1)
root (cd)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/sdb1 quiet splash
initrd /boot/initrd.img-2.6.20-16-generic

I tried to change this sequence to 
root (hd1,0)
kernel /vmlinuz root=/dev/sdb1 quiet splash
initrd /initrd.img

but I get an error "Cannot mount drive..."

I made all possible combinations but I canot load it..

I am not sure how device.map works and if that can help somehow.. 

I would appreciate any help. I do not want to install grub in first HD.

---

### Post by Herman on 2007-10-03
Hello klaasth,
When Ubuntu's GRUB is installed in MBR you can't boot Windows, but when Windows bootloader (NTLDR) is installed Windows boots okay?

With Ubuntu's GRUB still installed in MBR, can you boot Windows with Super Grub Disk and tell me if the same thing happens ?
(The same error message)?

---

### Post by Herman on 2007-10-03
>  I do not want to place GRUB in HD. I would like to boot from CD and to load ubuntu from extern USB. Is it possible?Hello kubu_for, 

I have a good how-to about making a 'dedicated /home for Knoppix in a USB disk,[Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html"). Knoppix does that very well, and you can also do that for a Ubuntu LiveCD too, There is a nice how-to in the Ubuntu Wiki about that, [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").
 Would those be the type of thing you had in mind? With that type of USB install you can boot it from any computer, that's why I prefer to do it that way. You can go travelling and take a Ubuntu or Knoppix LiveCD and your USB drive with your /home in it. :)

The other kind of USB install, where you actually install Ubuntu operating system inside the USB drive has the disadvantage that not all computers BIOSes will support booting one of those, so it's not useful to take travelling, you can only use it at home, in which case you might as well install Ubuntu in an internal hard disk and install GRUB to MBR. 

Regards, Herman :)

---

### Post by klaasth on 2007-10-03
> Hello klaasth,
When Ubuntu's GRUB is installed in MBR you can't boot Windows, but when Windows bootloader (NTLDR) is installed Windows boots okay?

With Ubuntu's GRUB still installed in MBR, can you boot Windows with Super Grub Disk and tell me if the same thing happens ?
(The same error message)?

I don't know what ntldr bootloader of windows is never heard before. Where can I found a tutorial to install it?

When ubuntu Grub is installed. I can boot from super grub disk just by taking the second option in the windows menu of ubuntu groob (boot windows -> works in 90%) then I get no errors. Windows xp boot then well.

Thank you for your advice

---

### Post by kubu_for on 2007-10-03
Halo Herman,

I actually do not have problems installing Kubuntu on USB drive. I've alredy done it. The problem is: my BIOS doesn't support boot from USB. My idea is to prepare Grub CD and load ubuntu from USB. CD will be used just to boot grub. Once I get grub I will load ubuntu (already installed on USB HD). I did this too, but I had to place kernel files on CD. This has some drawbacks:
1) After updating kernel I have to update my CD (let say not so critical)
2) When I boot on this way, CD drive is locked. I canot use it in ubuntu (this is critical)

So, the question is: how to load ubuntu from extern USB if I am already inside of GRUB? Simply I cannot map correctly my USB drives and grub has problems mounting it.

Any idea?

---

### Post by Herman on 2007-10-03
> I don't know what ntldr bootloader of windows is never heard before. Where can I found a tutorial to install it? Windows NTLDR bootloader is already inside your Windows operating system, you can look and see those file if your Windows XP file system is mounted in Ubuntu, here is a link with illustrations, [            A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP").

When you use your Windows Install CD and run the command FIXMBR, it makes a little code get copied into part of your MBR to make your MBR point to the Windows boot sector and to these files, and NTLDR boots Windows.
Boot,ini is the configuration file for NTLDR.

When you install GRUB to MBR, it copies a little code to your MBR and makes your MBR point to GRUB files in Ubuntu instead. Then GRUB lets you choose whether to boot Ubuntu or maybe another Linux, or if you wantr to boot Windows it points back to Window' boot sector and chainloads it. That  wakes up Windows NTLDR bootloader and it does the work to boot Windows. (GRUB doesn't actually boot Windows, it just relays the message).

Super Grub Disk also works by chainloading your Windows by the boot sector.

Now, the interesting question is, if Windows can boot from the MBR okay by itself, and Super Grub Disk can also boot Windows okay by its boot sector, why doesn;t it boot when we try to boot it witrh Ubuntu's GRUB?

I looked up your error message in Google and I found a nice website with some useful information in it, here, [http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/l0508/65l08/65l08.asp&guid=](http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/l0508/65l08/65l08.asp&guid=)
 
According to the suggestion on that page, if you had that error message normally, it would likely be caused by an error in your boot.ini file, which is causing your Windows to not be able to find \<winnt root> \system32\ntoskrnl.exe file.
However, we know the file is there and it is okay and your boot.ini file is okay too, because your Windows boots up okay by itself or by Super Grub Disk, but just not with Ubuntu's GRUB.

That seems like an important clue that Super Grub Disk can chainload Windows okay but Ubuntu's GRUB causes Windows to get mixed up somehow and display the error message.

Ubuntu's GRUB contains some extra files that Super Grub Disk doesn't need that can temporarily change the way your BIOS sees your computer, such as GRUB's device.map file. Normally that's a good thing and especially useful when we have more than one hard disk and GRUB needs to be told which one to count as the first one, and which hard disk should be second, and so on. I am wondering if something happened  to get GRUB a little bit mixed up when it was first installed and made some of GRUB's files get configured wrong.

Another thing you said was the Super Grub Disk can boot Windows 90% of the time. That seems like an interesting clue too. Super Grub Disk should be able to boot Windows 100% of the time, not just 90%.

So I think we need to start from the simplest things and look for the real problem step by step until we find out what the real problem is and solve it.
One thing to make things simpler would be to make sure your external hard drive in not plugged in during booting, but plug it in after your computer is booted, just for a while, to make things simpler until we solve this problem. After we find out what's wrong and fix it, then you can boot with your USB hard drive plugged in if you want. :)

Okay, now, is this computer a laptop or a desktop, and do you know if it has an SCSI or SATA hard drive or IDE?
Did you ever have your hard drive or CD/DVD drive replaced, or is this computer still very new?
When we have IDE hard drives in a Desktop computer, they can have a standard or 'cable select' IDE cable, and the hard drive has a little plastic clip called a 'jumper', with metal inside it to make a bridge between two prongs on the back of your hard disk. That tells you computer if it is master, slave, or 'cable select'.
If you have a Cable select IDE type of ribbon cable for you hard drive. your hard drive should be set to 'master', and perhaps you might have a CD/DVD drive set as slave. If you have a special 'cable select' IDE cable, then your jumper setting should be set to 'cable select', on both drives.
A standard IDE ribbon cable had balck plugs, but a 'cable select' IDE cable has one blue plug for the motherboard, one grey plug for slave hard drive, and the black plug is for the master hard drive.
Do you think you could take a look with a flashlight (torch) and see inside your computer case?  (but make sure you don't touch anything in there unless you know what you are doing). ( I didn't ask any questions about your level of technical ability so far, so I don't know if you are a professional computer technician or someone who has never looked inside a computer before, so I am not sure how much to expect you to be able to do yourself).
If you have a SATA hard drive it will have a thin red cable and it doesn't need any jumpers, it will depend in which port it is plugged into on your motherboard.
If you are lucky you might be able to see stickers on top of the hard drive that tell you what the jumper positions should be, or maybe if your computer is very compact and crowded you might find it hard to see anything in there at all.

If you can easily check those jumper settings if you think that could have anything to do with your problem then it is worth looking at those first, the hardware needs to be right before the software will be able to work properly. 
If it's a laptop then that's not likely to be the problem, or if the computer is new (you didn't build it or modify it your self), then that's probably not the problem either, we'll take a look at your /boot/grub/device.map file next.

Regards, Herman :)

---

### Post by klaasth on 2007-10-03
I know very much about hardware and everything is plugged in OK. My harddisk is connected with a Sata cable and it is a desktop. I already tried to copy another ntkoskrnl.exe but it didn't work, I am out of idea's to fix this problem. Maybe you have some?

Thank you for so much effort!

---

### Post by 3579545 on 2007-10-03
> **Herman said:**
> Hello 3579545,
 

Then if you install Xubuntu last, the GRUB installer for Xubuntu will most likely detect your DOS and Windows 2000 installations and add them automatically to your new GRUB menu.
You still might need to edit the commands a little by hand, I'm not sure, maybe you'll need to add GRUB's 'hide' and 'unhide' commands to the boot entries yourself, or something like that, but that will be easy. Here's a link about that, [More than one Windows on the same disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk")

Regards, Herman :)
Thanks those are great ideas< i will try thr grub disk and let you know how it goes. 

As for hiding  and unhiding I will try hiding when I install Ubuntu. I insatlled dos-win2000 and when I went to install Ubuntu...the installation did not see the dos boot, made me raise some questions....



thanks again..

---

### Post by Herman on 2007-10-04
Hello kubu_for,
Would this link be the one ou are looking for then, [BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB") - Booting an Ubuntu system on a USB hard disk on computers which cannot boot from USB (using a boot CD).?

Regards, Herman :)

---

### Post by Herman on 2007-10-04
Hello 3579545,
No, you should have hidden your first Windows install from the second before you began the install of the second Windows operating system. The reason for doing that is to prevent Windows from setting up a default Windows style multi-boot.
Please read the following link thoroughly, [Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") Dan Goodell
It's up to you though, (of course), do whatever makes you happy! :)

Regards, Herman :)

---

### Post by Herman on 2007-10-04
Hello klaasth,
I have lots of ideas, but I can't promise which one will work.

One idea is to take a look through your BIOS and check that everything is set up right in there if you haven't already done that.

You can check your /boot/grub/device/map file, it should look like this, since you only have one hard disk,
```
(hd0)  /dev/sda
```

Another suggestion would be to save a copy of your /boot/grub/menu.lst and then delete the rest of your GRUB files in /boot/grub and then re-install GRUB and see if it will configure itself better this time.
That should fix any corruption or misconfiguration in your installed GRUB.
I can give you more details about how to do that if you need.

You could install GRUB to the first sector of your Ubuntu partition, (in addition to your MBR). After you do that you could try booting with GAG Boot Manager, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm"),  **GAG's HomePage: **[GAG Boot Manager]("http://gag.sourceforge.net/")
Maybe GAG will be able to chainload your Windows for you better than GRUB, GAG is a very good boot manager.

What do you think?
Regards, Herman :)

---

### Post by klaasth on 2007-10-05
I asked my teacher for help. And he said to watch me in the /boot/grub/device.map
and the media/hda1/boot.ini.

The boot.ini file is empty!!! and in the device.map conains the following:
(hd0)   /dev/sda
(hd1)   /dev/sdb

So maybe the problem is in the previous files.

---

### Post by Herman on 2007-10-05
Hello klaasth, :)
What? Your boot.ini file is empty? Are you sure? Because I don't think Windows would boot at all with an empty boot.ini file. :)
Maybe it's because of security features that it looks like it's empty, but if you open it by a special way in Windows XP, you'll see that it does have something in it. Yours might be differrent from mine because your Windows has the NTFS file system but I only have FAT32, so you have more security features than I do. 
Just in case you are interested, this link shows you another way to open it from inside Windows, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html") , but you don't need to do that now, (unless you want to). 

Anyway, never mind, the main thing to do for now I think will be to try a trick with your /boot/grub/device.map file in Ubuntu and see if it helps.

Make sure your external drive is unplugged now, and then run this command,
```
sudo grub-install --recheck /dev/sda3
```That command should do three things at the same time, it will get GRUB to write you a new device.map file and it will install it in GRUB for you, and you'll have an IPL for GRUB installed in the first sector of your Ubuntu partition too, all from the one command.

That command might take a few minutes to complete, but when it does it will give you some feedback (show you what it has written in your new device.map file). After you are finished that, you can reboot whenever you are ready and test GRUB out to see if that has fixed anything or not.
Maybe it will or maybe it won't
Your device.map file already looked okay to me, but it has the external USB disk in it, and if your BIOS has gotten your USB drive mixed up with the internal hard drive in the numbering, maybe that's what the problem could be. I'm not sure, it's something to try anyway,
Good luck, I hope it helps,
Regards, Herman :)

---

### Post by klaasth on 2007-10-05
> sudo grub-install --recheck /dev/sda3

Doesn't do anything, it just gives some options that you can choose and neither of one option is relevant.

Thankx

---

### Post by Herman on 2007-10-05
It didn't do anything?
When I do it it probes my hardware (disks) and re-writes my device.map file.
Here's what mine does with a couple of extra USB thumb drives plugged in, 
```
herman@amdxz:~$ sudo grub-install --recheck /dev/hda2
``````
 Probing devices to guess BIOS drives. This may take a long time.
``````
 Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb
(hd4)   /dev/sdc
```...and here's what it does when I unplug my extra USB thumb drives and run the same command again,
```
herman@amdxz:~$ sudo grub-install --recheck /dev/hda2
``````
Probing devices to guess BIOS drives. This may take a long time.
``````
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
``` If your USB drive had been plugged in during installation and your [ hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") was upside down in your BIOS for some reason, that might have cleared the problem. That theory is a bit far-fetched I suppose, because the USB drive would probably only appear in your BIOS when it's plugged in, in which case it should have affexcted the boot of Ubuntu too, if you tried booting with it unplugged. I don't know what kind of BIOS you have, so anything is possible.

Okay, never mind. 
Let's try a different tack then, how about trying out [GAG Boot Manager]("http://gag.sourceforge.net/")
 and see if that can chainload both of your operating systems better than GRUB, you will still be booting Ubuntu with GRUB, and Windows will still be booting with NTLDR, but GAG will be the boot manager, (manages the bootloaders for you). :)

[GAG Boot Manager]("http://gag.sourceforge.net/") is a free download of only 1.4 MB, so it will only take a second or so.
If you download that in Ubuntu you'll have a file called gag_4.9.zip. Then you can move it to your home directory and right-click on it and click 'Extract Here'.
That will give you a new directory called gag_4.9.
You open that and open the docs folder and look for the file called index.html,Right-click on it to open it in your firefox web browser. 
Then you should read what it says in there and follow whatever instructions you want. You can make a GAG CD, floppy disk, or do a 'direct installation' and copy GAG to /boot and from there install direct to MBR and the first track of your hard disk.
HINT: If your computer has a floppy disk drive, GAG works particularly well from a floppy disk. A GAG CD will work but it's not as convenient because you can't save your settings when it's in a CD.
Then you just need to configure GAG, which is easy because it's the Graphical.boot manager. :)
This page might help you too, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm") 
NOTE: You already ran grub-install and installed grub to /dev/sda3, simultaneously when we did the device.map command, so there is no need to do that again.

There are two reasons why it will be good if you can test booting with GAG For one thing it will help to determine if there's a problem with either your Windows itself or in your BIOS, because if GAG can't chainload your Windows either it will tend to indicate the problem is not with the boot managers. I already suspect that because Super Grub Disk doesn't even work 100% of the time for you.
Maybe we just need to run FIXBOOT or something like that, and fix your Windows, or look in your BIOS again for a wrong setting somewhere.

If GAG does boot Windows well then maybe there is a compatability problem with your BIOS and GRUB, so you might want to keep GAG Boot Manager instead.

Other options are to try out LiLo, [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html") or  WinGRUB, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").

Regards, Herman :)

---

