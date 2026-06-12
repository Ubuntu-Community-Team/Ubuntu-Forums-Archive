---
title: "my sad story.....and a newb looking for help with grub issues re: mounting"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by radpup on 2008-04-28
First post ever....sorry it's LONG.

Ok, here's my story. I'm a pseudo-newb to linux. The only reason that I'm not a total newb is that I learned a bunch of unix stuff 20 years ago in grad school while trying maintain a mass spectrometer that used HP-UX as the base operating system for the data acquistion and control computer. Wasn't an expert, but just a hack who learned what was needed to keep things going. Like many people, I spent the last 15 years chained to windows. I used to play extensively with CP/M and then DOS before that, writing batch files to do things and editing config.sys files to no end. Thus, I should have jumped to linux quite awhile ago, since I was predisposed to tinkering. But, I stuck with windows. But in the past couple years, I've gotten totally disillusioned with windows, and the lack of control one has over what it does (as well as it's cryptic nature). So, after hearing that ubuntu was desktop friendly, rather than server driven like unix like systems have historically been, I downloaded Gutsy a couple months ago and toyed with the live version. I liked it so much in the first week, that I dug out an old 20 GB IDE drive and hooked it up via a USB based enclosure, and installed Gutsy there. Grub worked great, and within 20 minutes I was running a full blown dual boot system. I started tinkering with apps downloaded from the net. I was hooked. I envisioned giving up windows forever (and that "genuine advantage"). I even started telling co-workers that they should take a look and give up the windows ball and chain. I work in a technical field, so most of my co-workers are savvy and confident enough to deal with file editing and command line things that must be done. No problem. I was becoming an evangelist already. So, I decided that since Hardy was coming out soon, that I would buy a nice new big SATA drive for my system (the 500 GB WD on sale!), add it to my windows system, install Hardy there, and start my tapered transition away from windows by staying dual boot for a bit. 

Hardy came out....I bought the drive and installed it. Now I had 2 NTFS windows disks and the new disk dedicated to linux. But....it didn't boot as cleanly as Gutsy did from my USB connected external drive. I got an "error 17" from grub on boot up everytime. And it just all stopped dead there. No windows boot, no Hardy boot. Nothing. I did some google searching and found multiple answers. Tried them all. Nothing changed. Now, I'm not like a lot of newbs that start freaking out and trashing linux because things didn't go perfect the first time. I'm willing to work through this (and learn something in the process). So...one forum suggestion was to download the "super grub disk". So, I did that. And still got error 17. But at least I was able to boot farther to a menu to choose operating systems. From there, I could boot windows, or attempt to boot to Hardy (or a recover version, both gave error 17) or memtest. The nice thing about the super grub boot menu is that I could edit the boot script and test immediately without resorting to booting to the live CD, making changes, and then trying to boot the hard drive again (that was slow going and getting old). Error 17 appears to be a mounting issue. When I started editing the super grub startup script, I cycled through the hard drive choices (hd0, hd1, hd2) since I wasn't sure which one it was looking for. Finally, I hit that right, and it booted past the error 17 issue. Yay! However, instead of booting into the nice desktop, it went into something called "busy box" and stopped there with a command line prompt. 

I'm at a loss now. It's been days of effort, and although I'm not getting totally frustrated, I'm at a loss on how to move forward. I can still get to windows, so I can get work done when need be. I can get to Hardy via live CD, but that's not getting me to a point where I can install new apps and really start playing with new OS. My main attempts into Hardy on the hard disk end up with either an "error 17" (when I don't have the right drive specified) or a busy box command prompt. 

Any suggestions here? I'm patient, and will keep scouring google and these forums for answers, but I figure with Hardy being new, SOMEONE must have the same issue and have found an answer. Any help is appreciated and will get me on my way with learning this OS in detail and then contributing to the community. Thanks in advance.

      D

---

### Post by confused57 on 2008-04-28
I highly recommend this website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Open a terminal, using the live cd, post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Once you determine which is your Ubuntu root partition, you need to mount it from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
replace /dev/xxx with your root partition, e.g. /dev/sdb1
With the root partition mounted from the live cd, you can explore your grub configuration file:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
and how grub recognizes your HD order:
```
gedit /media/ubuntu/boot/grub/device.map
```

---

### Post by Peter09 on 2008-04-28
Don't know if I can be of much help here, however I have read that Hardy has problems with SATA drives. If I recall its to do with the BIOS settings of the drive. It can be set to Legacy or ... something else. One of these settings is problematic.

Sorry That I can't help you anymore but it might be worth a trawl through the forums for a better description of this problem.

PC

---

### Post by radpup on 2008-04-28
Thanks! I have been through much of this territory already (after reading through the forums), just not sure I was using all the information  properly. I will go through it again and post some of the data I dig up from these suggestions and perhaps someone will notice what mistake I am making. I know I am reasonably close to getting this to work. 

   D 

> **confused57 said:**
> I highly recommend this website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Open a terminal, using the live cd, post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Once you determine which is your Ubuntu root partition, you need to mount it from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
replace /dev/xxx with your root partition, e.g. /dev/sdb1
With the root partition mounted from the live cd, you can explore your grub configuration file:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
and how grub recognizes your HD order:
```
gedit /media/ubuntu/boot/grub/device.map
```

---

### Post by radpup on 2008-04-28
Thanks! Yes, I have read this also, although details are still sketchy from most of what I read. One very good post suggested that a problem was fixed by checking BIOS and making sure that the drives were set to AUTO, not large, or user, or other setting there. Mine were already AUTO, so that didn't solve my problem. Enough people are going SATA that this should be fixed soon, I would hope. And the problem is related to boot up, because I can mount and use the drive with no problem when I start the OS from the live CD. Thanks for the suggestion, I will watch forum posts for SATA issues/fixes in case this is the problem.

    D

> **Peter09 said:**
> Don't know if I can be of much help here, however I have read that Hardy has problems with SATA drives. If I recall its to do with the BIOS settings of the drive. It can be set to Legacy or ... something else. One of these settings is problematic.

Sorry That I can't help you anymore but it might be worth a trawl through the forums for a better description of this problem.

PC

---

### Post by zman0900 on 2008-04-28
I am currently running ubuntu and win xp in dual boot in a very similar way to what u want to do.  I have had this working successfully for about 6 months, but I too had some difficulties in the begining.  My laptop has two internal SATA drives.  I had windows installed on the first drive, and I wanted to put ubuntu on the second.  What ended up solving my issues was gparted.  I shrunk the windows partition a bit so that I could put a very small ext3 partition in front of it for /boot on the first drive.  I have the root / partition on the second drive.  When I tried to have grub on the second drive, it would never boot (I believe I was getting error 17).  I've included my partition layout, hopefully this helps.

```
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags   mounted on:
 1      32.3kB  65.8MB  65.8MB  primary   ext3         boot    /boot
 2      65.8MB  10.7GB  10.7GB  primary   ntfs                 /windows
 3      10.7GB  120GB   109GB   extended                    
 5      10.7GB  119GB   108GB   logical   fat32                /data
 6      119GB   120GB   1074MB  logical   linux-swap           swap

Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags   mounted on:
 3      32.3kB  55.6GB  55.6GB  primary  ext3                 /
 1      55.6GB  120GB   64.4GB  primary  ntfs                 /data_old

```

Here's my grub menu.lst file as well:
```
default		saved
timeout		10

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
# kopt=root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro

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
# defoptions=quiet splash resume=/dev/sda6 vga=795

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
# savedefault=true

## ## End Default Options ##

splashimage=(hd0,0)/grub/splash.xpm.gz

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

Note that where it says root=UUID... for the ubuntu kernels, that is referring to the root ubuntu partition on drive 2, but root (hd0,0) is referring to /boot on drive 1.

---

### Post by radpup on 2008-04-28
I have thought about this approach....I figured it would work. The key is: can I repartition the main windows drive and add a small ext3 partition without losing everything and needing to reinstall windows? I have the space....it's a 250 gig drive and I'm using about 30 gig. And how large would that partition need to be? Looks like you're using 65 MB, which isn't much. Is that overkill size-wise, or does one need to leave space for "growth"? I've been trying to find another solution, but will resort to this if I can't find another way AND if I can repartition that drive without excessive risk. Thanks!!!

    D 


> **zman0900 said:**
> I am currently running ubuntu and win xp in dual boot in a very similar way to what u want to do.  I have had this working successfully for about 6 months, but I too had some difficulties in the begining.  My laptop has two internal SATA drives.  I had windows installed on the first drive, and I wanted to put ubuntu on the second.  What ended up solving my issues was gparted.  I shrunk the windows partition a bit so that I could put a very small ext3 partition in front of it for /boot on the first drive.  I have the root / partition on the second drive.  When I tried to have grub on the second drive, it would never boot (I believe I was getting error 17).  I've included my partition layout, hopefully this helps.

```
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags   mounted on:
 1      32.3kB  65.8MB  65.8MB  primary   ext3         boot    /boot
 2      65.8MB  10.7GB  10.7GB  primary   ntfs                 /windows
 3      10.7GB  120GB   109GB   extended                    
 5      10.7GB  119GB   108GB   logical   fat32                /data
 6      119GB   120GB   1074MB  logical   linux-swap           swap

Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags   mounted on:
 3      32.3kB  55.6GB  55.6GB  primary  ext3                 /
 1      55.6GB  120GB   64.4GB  primary  ntfs                 /data_old

```

Here's my grub menu.lst file as well:
```
default		saved
timeout		10

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
# kopt=root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro

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
# defoptions=quiet splash resume=/dev/sda6 vga=795

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
# savedefault=true

## ## End Default Options ##

splashimage=(hd0,0)/grub/splash.xpm.gz

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

Note that where it says root=UUID... for the ubuntu kernels, that is referring to the root ubuntu partition on drive 2, but root (hd0,0) is referring to /boot on drive 1.

---

### Post by radpup on 2008-04-28
One other thing....where does one get that UUID number? I think I biffed mine during some edits. That could also be causing some of the issues I'm having.

     D

> **zman0900 said:**
> 
Here's my grub menu.lst file as well:
```
default		saved
timeout		10

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
# kopt=root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro

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
# defoptions=quiet splash resume=/dev/sda6 vga=795

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
# savedefault=true

## ## End Default Options ##

splashimage=(hd0,0)/grub/splash.xpm.gz

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro quiet splash resume=/dev/sda6 vga=795
initrd		/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=2bd0a446-630d-40d4-913f-ffd1a7f38238 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

Note that where it says root=UUID... for the ubuntu kernels, that is referring to the root ubuntu partition on drive 2, but root (hd0,0) is referring to /boot on drive 1.

---

### Post by confused57 on 2008-04-28
It may be that you need to add boot parameters to your kernel options...I don't have any personal experience with a busybox problem, but this thread may help:
[http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7)

---

### Post by zman0900 on 2008-04-28
As for resizing the windows partition, I have used GParted to resize various ntfs, fat32, and ext3 partitions several times and have never experienced any problems or data loss.  And I believe that program is installed on the ubuntu live cd.  If not, google it and it has its own live cd.  I've used this a few times as well with no problems, although it is fairly slow to boot.  I'm using 65 M, which is ok when you have only one version of the kernel, but now that I've upgraded to hardy, space is kind of tight with two versions of the kernel, so I would recommend something slightly larger like 128 or 256 M for the future.  

As for the UUID, that is like that because it was auto generated by the installer.  It would also be perfectly correct to use root=/dev/sdb3 (the location of my root partition).  

The easiest way to do this would probably be to create that small partition first with the live cd, then reinstall ubuntu and make sure you tell it to mount /boot to the new small partition you created, and root to the partition on your second drive.  That should cause your menu.lst to be auto generated (which is very handy during upgrades), and if your lucky, it will even automatically add the entry to boot windows.

---

### Post by radpup on 2008-04-28
Problem is now FIXED!!!! I guess I won't have to resort to repartitioning my main windows drive. BTW, I did find that the UUID is in /etc/fstab...but you were correct, root=/dev/sdb1 works just as well. Here was the fix, for those using supergrub and still landing in busy box:

I looked hard at this startup script in super grub: 
 
root=(hd0,0)
/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro single
/initrd.img-2.6.22-14-generic
quiet

The part that didn't make sense to me was the first root assignment. It appears that "hd" is used for IDE drives and "sd" is used for SATA drives. Since root is set in the second line, I don't understand why it is also needed in the first line (unless the kernal is booted to a partition on an IDE drive and the rest of the OS is sitting on a second SATA drive). So, I just deleted the first line referencing (hd0,0) and rebooted. And it worked!!!!! No dump to busy box! Do remember that my setup is 3 SATA drives, with Hardy installed on sdb...the other 2 drives are windows XP drives. But now, it appears I don't have to make a small partition on the first windows drive to get Hardy to boot from the second drive.

Thanks to all for the help and suggestions. The answers helped me learn something and I'm excited now to start really investigating this OS.

      D


> **zman0900 said:**
> As for resizing the windows partition, I have used GParted to resize various ntfs, fat32, and ext3 partitions several times and have never experienced any problems or data loss.  And I believe that program is installed on the ubuntu live cd.  If not, google it and it has its own live cd.  I've used this a few times as well with no problems, although it is fairly slow to boot.  I'm using 65 M, which is ok when you have only one version of the kernel, but now that I've upgraded to hardy, space is kind of tight with two versions of the kernel, so I would recommend something slightly larger like 128 or 256 M for the future.  

As for the UUID, that is like that because it was auto generated by the installer.  It would also be perfectly correct to use root=/dev/sdb3 (the location of my root partition).  

The easiest way to do this would probably be to create that small partition first with the live cd, then reinstall ubuntu and make sure you tell it to mount /boot to the new small partition you created, and root to the partition on your second drive.  That should cause your menu.lst to be auto generated (which is very handy during upgrades), and if your lucky, it will even automatically add the entry to boot windows.

---

### Post by confused57 on 2008-04-28
Glad you got it working...great advice by zman0900.  Once you get a little more experience, you can always "revert" back to using UUID's for your /etc/fstab & kernel root option in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

There are advantages & disadvantages to using either method.

---

### Post by radpup on 2008-04-28
I wonder now how many people are having the same issue. I see a lot of "busy box" and "error 17" issues posted here. I wonder how many of them can be fixed as easy as mine (probably just the pure SATA people without mixed systems (SATA/IDE)). However, the technical discussion on what just happened to me needs to take place, since supergrub defaults to a 4 line variant of the following:

root (hd0,0)
/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro single
/initrd.img-2.6.22-14-generic
quiet

I'm not sure of the reason for the first line, as root is specified in the second line on the kernal load. Is root one variable, or does the second line just concatanate to the root statement? I can understand the "error 17" if supergrub was trying to mount my windows IDE drive as a SATA, but the dump to busy box when the drive spec is changed is beyond my comprehension.

I will likely start searching the forums to see if I can help others with my same issue and see if they can get up and going.

      D

> **confused57 said:**
> Glad you got it working...great advice by zman0900.  Once you get a little more experience, you can always "revert" back to using UUID's for your /etc/fstab & kernel root option in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

There are advantages & disadvantages to using either method.

---

### Post by confused57 on 2008-04-28
> I'm not sure of the reason for the first line, as root is specified in the second line on the kernal load. Is root one variable, or does the second line just concatanate to the root statement? I can understand the "error 17" if supergrub was trying to mount my windows IDE drive as a SATA, but the dump to busy box when the drive spec is changed is beyond my comprehension.
Grub recognizes partitions as (hdx,y) and the "root (hdx,y)" line is needed for grub to find the OS kernel image.  The Linux kernel recognizes partitions as /dev/xxx, therefore this is where the kernel looks for the root partition.  The root line may be different than your kernel root if you have a separate /boot partition...grub stage 1 would look for the kernel in (hd0,0), but the root partition may be in (hd0,2) or /dev/sdx3.

Older versions of Ubuntu recognizes IDE drives as hdx and SATA drives as sdx, however newer versions(on most computers) recognizes drives as sdx, regardless of whether they are IDE or SATA.
For example, I have 3 drives, an IDE and 2 SATA...in Dapper, they're recognized as hda, sda, & sdb...in Gutsy & Hardy, they're sda(hda in Dapper), sdb, & sdc.

I believe it depends on the chipset or hard drive controller, whether Gutsy or Hardy differentiates between hda or sda...

---

