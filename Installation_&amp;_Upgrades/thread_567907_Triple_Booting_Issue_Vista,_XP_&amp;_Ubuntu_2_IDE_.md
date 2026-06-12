---
title: "Triple Booting Issue: Vista, XP &amp; Ubuntu: 2 IDE 1 SATA"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by m03 on 2007-10-05
Well first off I would like to say these forums are great and I really admire all the helpful individuals in the community.  I have been scouring the forums and google for what feels like ages for answers to my issue, but no avail.  I would also like to state that this is my first experience with Linux Ubuntu and Linux in general truthfully, but I figured if I'm going to give it a whirl it better be a doosey. :) lol Anyway here it goes.

Currently I am Dual booting Vista Ultimate and XP Pro.  I have 5 HDDs installed with a lot of space used.  Anyways... I am currently using the Vista Bootloader with EasyBCD to manipulate the boot files when needed. From viewing Disk Management in Vista I will describe my current drive/partition setup:

Disk 0 (500GB WD) IDE (Detects 465.76GB)
             
             C: 60.00GB NTFS 
             Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition)      

             E: 405.76GB NTFS
             Healthy (Primary Partition)

Disk 1 (20GB WD) IDE (Detects 18.64GB)

            D: 18.64GB NTFS
            Healthy (Primary Partition)

Disk 2 (120GB Seagate) SATA (Detects 111.76GB)

            I: 111.75GB NTFS
            Healthy (Logical Drive)

Disk 3 (320GB WD) SATA (Detects 298.09GB)

            J: 268.08GB NTFS
            Healthy (Logical Drive)

            Linux Partition: 28.99GB EXT3
            Healthy (Primary Partition)

            Linux Partition: 1.00GB SWAP
            Healthy (Primary Partition)

Disk 4 (160GB WD) IDE NTFS (Detects 149.05GB)

            K: 149.04GB NTFS
            Healthy (Logical Drive)

Currently I have Vista Ultimate on Drive C and XP Pro on Drive D.  My original procedure consisted of booting the latest GParted Live CD to manage the partitions... On my disk 3 I resized the partition to get 30 GB of unallocated space.  I then proceeded to create an EXT3 partition and the SWAP partition for the Ubuntu install as I read in some of the guides that the shrinking of the drives and partition creation from the live CD didn't always work the best.  Everything went fine with the partition creation so I then booted with the Ubuntu 7.04 live CD and proceeded with the Ubuntu install.  When it got to the partition assignment section I picked manual and then pointed to the EXT3 partition I created with GParted LiveCD and received an error stating that I needed to reformat the partition I was installing to as I was using the "/" for my root install (hope that makes sense)  So after I closed the error I highlighted the partition and chose to edit the existing partition. I changed the "/sdc6" to simply "/" and proceeded with the install.  Upon completion and reboot i receive the Grub Error 22: No Such Partition and then nothing will boot.  I delved a bit further and burnt a Super Gnome Disk and attempted to launch through that and still could not get into Ubuntu.  I tried to repair GNOME's mbr and launch still no dice.

Also, through the Ubuntu LiveCD I mounted the partition I installed Ubuntu to and have verified the files did install and are present.  Since all of this I have ran the XP recovery and used the "fixmbr" command to restore the original vista bootloader and can now jump from Vista to XP with no issues as before, but I still cannot get Ubuntu to boot from my drive... only from the LiveCD

I figure it is something not configured properly in the GNOME mbr but I dont know where... Another point I would like to mention is that when installing Ubuntu it did not detect my Vista or XP install and I figured that was because they are not on the same physical drive.

All of the HDDs are set to Cable Select with their jumpers and the BIOS Boot Order is: CD-ROM, HDD0, HDD1, HDD2. (CD-ROM has been set first for the booting of the Live CDs and Recovery Disks

Tools I have acquired and have been playing with consist of:

Vista Ultimate DVD
XP Pro CD
Ubuntu 7.04 LiveCD
Latest GParted Live CD
Latest Super GNOME Disk (CD)
EasyBCD 1.7
Partition Magic 8.2

I have no problem reading over other links or booting to the Ubuntu livecd to copy and paste info or post screen shots.

2 of the Guides I was reading over heavily were:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

and 

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/]("http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/")


I know Obi Wan is out there somewhere... Help Me You Are My Only Hope.

m03

---

### Post by m03 on 2007-10-05
I've gone back in with the GParted LiveCD and deleted the EXT3 and Swap partitions and have booted back up with the Ubuntu LiveCD.  I've started the installation:

Step 4 of 7 "Prepare Disk Space" -  

I've selected "Manual" so I can choose my drive I wish to install on.

On the next section I can see my drive "/dev/sdc". "/dev/sdc5" is listed under this drive for the existing NTFS partition and also "free space".

I've highlighted "free space" and then clicked "New Partiton"

On the "Create a partition" dialog box I've selected: the "Logical" partition type, Size to "29694 MB", Location set to "Beginning", as an "Ext3" partition, and named the mount point "/"

For the Swap I set to: "Logical", size "1024 MB", Location "Beginning".

on step 5 of 7 the program "ma-search-users" closes unexpected and errors, No other OS's are detected at this point for user/document migration.

On step 7 I receive the normal summary:
```

 Language: English
 Keyboard layout: U.S. English
 Name: M03
 Login name: m03
 Location: America/New_York
 Migration Assistant:



If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI5 (0,0,0) (sdc)

The following partitions are going to be formatted:
 partition #6 of SCSI5 (0,0,0) (sdc) as ext3
 partition #7 of SCSI5 (0,0,0) (sdc) as swap
```

As stated in previous post I believe.  in my previous attempts Vista and XP have never been detected during the install.

I checked the advanced button as well and it seems the boot files will be installed to hd0 which makes sense since thats where the windows boots files are as well.

Will post results when I am finished... hopefully someone can lend some of their expertise. 


Thanks in advance 

m03

---

### Post by m03 on 2007-10-05
I've finished the installed and rebooted and attempted to boot with GRUB as the vista bootloader is now scrapped from install... I receive an error when booting straight to Ubuntu:

GRUB Loading, Please wait
Error 22

I also tried the super gnome disk without running the fix gnome mbr and get into the GRUB bootloader only to get the same error but with something along the line of Error 22: No Partition File.

Here is some info from Ubuntu:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/hda2            7834       60801   425465460    7  HPFS/NTFS

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2433    19543041    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14589   117178110    f  W95 Ext'd (LBA)
/dev/sdb5               2       14589   117178078+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38731   311098725    f  W95 Ext'd (LBA)
/dev/sdc5               2       34997   281105338+   7  HPFS/NTFS
/dev/sdc6           34998       38607    28997293+  83  Linux
/dev/sdc7           38608       38731      995998+  82  Linux swap / Solaris
```

I will leave it at this point for a bit and see if anyone responds with any ideas.  Please help out if you can as I really want to get this bad boy running... possibly say bye bye to MS all together at some point would be great but not just yet.

m03

---

### Post by m03 on 2007-10-05
BUMP...figured I'd bump this up and see if anyone might be able to help.

---

### Post by ctothej on 2007-10-05
Seems like GRUB isnt installed correctly. You could either boot with the LIVECD and update/reinstall GRUB or add an entry into the Windows boot loader to boot to whatever partition sdc6 is.

---

### Post by Herman on 2007-10-05
Hello m03, :)

Here's how to [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") to rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] 
That link should ehlp to explain to you how to use the Ubuntu Live CD to get ahold of your /boot/grub/menu.lst file in Ubuntu to see what might be wrong in there and see if we can fix it.

Here's a link to my info about GRUB error 22, and how it can normally be fixed, [/COLOR][/COLOR][     Grub error 22]("http://users.bigpond.net.au/hermanzone/p15.htm#22").

If you still need help, please post a copy of your /boot/grub/menu.lst file here and I or someone can help you edit it if that's the problem.

After re-reading my own notes on GRUB Error 22 I see that it can also be cured with a file system check in the Ubuntu partition from a GParted LiveCD too, so that's something else that might be worht a try.

I hope something there will be helpful'Regards, Herman :)

---

### Post by Herman on 2007-10-05
> I am currently using the Vista Bootloader with EasyBCD to manipulate the boot files when needed ...or use  [EasyBCD]("http://neosmart.net/dl.php?id=1") to boot Ubuntu for you instead, but you'll still need Ubuntu's /boot/grub/menu.lst file to be correct for that.
Another file you might want to look at (and post here maybe if you still have trouble), is your Ubuntu's /boot/grub/device.map file. 
Regards, Herman :)

---

### Post by m03 on 2007-10-05
great thanks guys I'm going to read them now and will post back shortly :)

Thanks 

m03:guitar:

---

### Post by m03 on 2007-10-05
> **Herman said:**
> Hello m03, :)

Here's how to [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") to rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] 
That link should ehlp to explain to you how to use the Ubuntu Live CD to get ahold of your /boot/grub/menu.lst file in Ubuntu to see what might be wrong in there and see if we can fix it.

Here's a link to my info about GRUB error 22, and how it can normally be fixed, [/COLOR][/COLOR][     Grub error 22]("http://users.bigpond.net.au/hermanzone/p15.htm#22").

If you still need help, please post a copy of your /boot/grub/menu.lst file here and I or someone can help you edit it if that's the problem.

After re-reading my own notes on GRUB Error 22 I see that it can also be cured with a file system check in the Ubuntu partition from a GParted LiveCD too, so that's something else that might be worht a try.

I hope something there will be helpful'Regards, Herman :)

Ok I mounted the partition with the liveCD and am looking at the menu.lst now:

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
# kopt=root=UUID=67ea31d6-550c-4aad-9aba-f48c571df36f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,5)

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
root		(hd4,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=67ea31d6-550c-4aad-9aba-f48c571df36f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd4,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=67ea31d6-550c-4aad-9aba-f48c571df36f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd4,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Where would you like me to go from here?  Looks like it is saying my Ubuntu install is on HD4,5

---

### Post by m03 on 2007-10-05
> **Herman said:**
> ...or use  [EasyBCD]("http://neosmart.net/dl.php?id=1") to boot Ubuntu for you instead, but you'll still need Ubuntu's /boot/grub/menu.lst file to be correct for that.
Another file you might want to look at (and post here maybe if you still have trouble), is your Ubuntu's /boot/grub/device.map file. 
Regards, Herman :)

as requested here is my device.map file as well (viewed from gedit with command "ubuntu@ubuntu:~$ sudo gedit /media/ubuntu/boot/grub/device.map")

```
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda
(hd3)	/dev/sdb
(hd4)	/dev/sdc

```

---

### Post by Herman on 2007-10-05
Good, m03, :)
Well, I think your /boot/grub/menu.lst file looks okay.
You have Ubuntu in your fifth hard disk and in your number 6 partition, but GRUB always starts counting from the number 0 instead of 1, so (hd4,5) would be correct.

You could use your GParted LiveCD and run a file system check in your Ubuntu partition just to make sure, it won't hurt and it might help.

Your device.map file looks a little bit messy. Here's a link about how to edit that, [**Editing GRUB's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map") (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything)
That might do the trick for you, (I hope) :)

Regards, Herman :)

---

### Post by m03 on 2007-10-05
> **Herman said:**
> Good, m03, :)
Well, I think your /boot/grub/menu.lst file looks okay.
You have Ubuntu in your fifth hard disk and in your number 6 partition, but GRUB always starts counting from the number 0 instead of 1, so (hd4,5) would be correct.

You could use your GParted LiveCD and run a file system check in your Ubuntu partition just to make sure, it won't hurt and it might help.

Your device.map file looks a little bit messy. Here's a link about how to edit that, [**Editing GRUB's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map") (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything)
That might do the trick for you, (I hope) :)

Regards, Herman :)

Great Herman I'm going to boot to the GParted liveCD and run the check now and I'm still reading over the fix device.map ;)

---

### Post by Herman on 2007-10-05
Actually, m03, now that I have looked at your device.maop file again, that looks okay too, it's just that you don't have an hdb at all, I don't know why, it isn;t in your fdisk output either, so your device.map might be okay.

---

### Post by m03 on 2007-10-05
very odd indeed.  So my .lst and .map files look to be ok... I ran the system check in GParted and attempted boot again but same error 22 for GRUB.  Should I just try to kill the current Ubuntu Partition on the SATA and resize the Vista partition and just create an ext3 and swap partition on that same HDD... i could then take the 30 Gigs i am currently using and format it FAT32 so I have a drive that both windows and linux can write to.

What do ya think? :confused:

m03

---

### Post by Herman on 2007-10-05
> very odd indeed. So my .lst and .map files look to be ok... I ran the system check in GParted and attempted boot again but same error 22 for GRUB. Should I just try to kill the current Ubuntu Partition on the SATA and resize the Vista partition and just create an ext3 and swap partition on that same HDD... i could then take the 30 Gigs i am currently using and format it FAT32 so I have a drive that both windows and linux can write to.Yeah, well you could do that I suppose, that should work and might be quicker than fiddling around with the way it is now, who knows, it might be something simple we can fix in a few minutes or it could take forever to troubleshoot and correct whatever the problem might be. 
At least we know that re-installing in a different hard drive will only take about half an hour.

If you do want to keep on troubleshooting your set up the way it is now I would have tried booting with [**GRUB's Command Line Interface**]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") next and see if we can learn anything from that.

Whatever you decide to do I hope you'll enjoy Ubuntu, so just do whatever you think will be best for you.
Regards, Herman :)

---

### Post by Herman on 2007-10-05
I have Ubuntu in my first hard disk and I have no Windows at all in this computer I'm using right now, but I formatted my second hard disk with NTFS anyway, just to use it for experimental purposes.
I used a how-to from [Ubuntu Geek's site]("http://www.ubuntugeek.com/tag/ubuntu-hacks/") to get my Ubuntu to be capable of both reading and writing to and from my NTFS hard drive.
If I can find that how-to again you might not need any FAT32 partition. ...here it is, this is what I used, [Windows NTFS Partitions Read/write support made easy in Ubuntu Feisty]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")
That has been working well with no problems for me for some time now. I think Linux support for NTFS is getting pretty good now, but maybe it's still best to restrict it to a dedicated NTFS partition or disk maybe, just to err on the conservative side.

---

### Post by dabl on 2007-10-05
For complex disk/partition combinations, I recommend the Alternate Install CD, rather than the Live CD.

Reasons:

1. You can choose partitions that will NOT be mounted at all.
2. You can choose partitions to be formatted ("/") during installation, and partitions to be mounted as-is without formatting ("/home").
3. Different partitions can be formatted with different filesystems.
4. You can direct the installation of the Grub bootloader to the partition where you actually want it.

Taking this approach, I have one IDE drive that is NOT the boot drive, and 4 SATA drives, and have 3 Linux OSs to pick from when I boot.  :)

---

### Post by m03 on 2007-10-05
gentlemen thanks for you help.  I basically went and restored my Windows mbr with fixmbr through XP's recovery console.  Then with partition magic (although GParted would have worked just as well) I killed the Ext3 and Swap partitions on the SATA drive and turned it to a fat32 for the time being.  I also sectioned off some of the space on the vista/data drive (1st HDD) and then booted Ubuntu LiveCD and proceeded with the formating while installing... just selected the use largest space selection and let the install finish.  I have now booted to all 3 OS's.  GRUB loads first for me to select Ubuntu and also lets me start the Vista bootloader as well.  Vista didn't like my 2.5 GB ram config originally so I have been running @ 2GB for some time now (XP handles the config fine as well)... so I'm thinking I will stick my last 512MB stick in and really see what this baby can do ;)  I'm going to check out the NTFS read and write now too thanks for that link.

m03

---

### Post by Herman on 2007-10-05
Okay m03! 
Welcome to Ubuntu and congratulations on your successful installation! :)


Hello dabl :)
Yes, a few people still prefer the 'Alternate' CD for various reasons. I agree. It contains quite a few tricks and secrets in it that most people wouldn't be aware of.
I really like the Ubuntu Live CDs too. I am impressed with the new Windows migration tools in the Live CD's installer! Ubuntu just keeps getting better and better all the time! :)

Regards, Herman :)

---

