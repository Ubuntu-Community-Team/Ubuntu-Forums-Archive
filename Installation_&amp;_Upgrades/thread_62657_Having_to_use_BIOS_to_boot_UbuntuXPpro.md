---
title: "Having to use BIOS to boot Ubuntu/XPpro"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by chippy57 on 2005-09-05
I have 2 x WD120gig SATA in RAID 0 using Fastrak 378 with XPpro loaded on, 

I decided to use a spare WD 10 gig and connected it to the empty Pri IDE and installed Ubuntu Hoary 5.04.

It installed faultlessly except for the fact that grub did'nt recognise XPpro and I wanted a dual boot configuration, however  it did see the the 2 SATA drives, anyway it must have written the bootloader to the MBR of the Pri IDE and did not allow me to select the drive to write, so when I booted up it went straight into XP so I went into BIOS and selected the hd that Ubuntu was on and sure enough Ubuntu booted up no probs and works great. apart from a few tweaks I will need to do.

Can I write something  to menu.lst to give me dual boot functionality? like:-

title         Windows 95/98/NT/2000/XP
root          (hd0,0)
makeactive
chainloader   +1

How can I find out the root of XP eg.(hd1.0) or whatever?

Sorry  for the longwinded explanation I am a newbie to linux but not totally dumb.

below is my menu.lst using  $cat /boot/grub/menu.lst

Any advice is greatly appreciated

regards 

chips

```

# menu.lst - See: grub{8), info grub, update-grub{8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by essexman on 2005-09-05
Windows must be in the first partition of the primary drive.

Linux can install on any partition and have as many Distributions that you can fit.  Windows is not so accomodating.

You will need to make your spare drive a secondary drive or slave, but not the prime master.

If you have a live CD you may be able to reinstall grub after switching the drive around, there are many HOWTOs on the forum for this. However, it may be best to start again if you can.

---

### Post by Sale on 2005-09-05
Here's what helped me with a similar hardware configuration>

title		Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

---

### Post by Steve1961 on 2005-09-05
You need to write grub to the mbr of the primary hard drive - which should be the sata drive XP is on.  To do this use your cd to gain root access to your ubuntu installation:

[http://amd64.ubuntuguide.org/#gainrootinstallcd](http://amd64.ubuntuguide.org/#gainrootinstallcd)

You then need to find out what ubuntu calls your xp partition.  To do this just type sudo fdisk -l.  Your NTFS partition will probably be called something like sda if its a sata disk.

From here you need to install grub into the root partition of the sda drive by typing grub-install /dev/sda.  You also need to add the extra entry into your grub configuration so that XP is an option when grub loads.

It looks as if the Ubuntu installation has not known whether your sata or ide drives should be treated as the first drive, and so it's ignored the sata drives and gone for the ide drive.  

You don't need to add the maping entries in grub as windows doesn't need to be tricked into thinking it's on the first hard drive - it is.

Finally set your xp sata drive as the first boot drive in your bios.  That's it.  Hopefully everything should now work.

---

### Post by chippy57 on 2005-09-05
Thanks for all your input guys, I will check it out when I get home from work and will post a reply on how I get on.

regards

chips

---

### Post by chippy57 on 2005-09-07
OK I had a bash at a couple of things, firstly:-

> **essexman **

Windows must be in the first partition of the primary drive.

Linux can install on any partition and have as many Distributions that you can fit. Windows is not so accomodating.

You will need to make your spare drive a secondary drive or slave, but not the prime master.

If you have a live CD you may be able to reinstall grub after switching the drive around, there are many HOWTOs on the forum for this. However, it may be best to start again if you can.
 
I did start again, I moved the WD 10gig drive from Primary IDE to the Secondary IDE and reinstalled Hoary 5.04, it still didn't see the winXP installation and so grub again wrote to the MBR of the WD10gig, so I'm back to square one having to use bios to boot to either XP or Hoary.  the dvd is now on Primary IDE and the WD10 gig is on Secondary IDE.

I did wonder but haven't tried it yet,  actually slaving the WD10gig to the DVD drive to see what happens. I have also downloaded the Live CD, but haven't yet tried to use it to install Grub, I have yet to find the HOW TO's and of course work gets in the way.


> **Steve1961**

You need to write grub to the mbr of the primary hard drive - which should be the sata drive XP is on. To do this use your cd to gain root access to your ubuntu installation:

[http://amd64.ubuntuguide.org/#gainrootinstallcd](http://amd64.ubuntuguide.org/#gainrootinstallcd)

You then need to find out what ubuntu calls your xp partition. To do this just type sudo fdisk -l. Your NTFS partition will probably be called something like sda if its a sata disk.

From here you need to install grub into the root partition of the sda drive by typing grub-install /dev/sda. You also need to add the extra entry into your grub configuration so that XP is an option when grub loads.

It looks as if the Ubuntu installation has not known whether your sata or ide drives should be treated as the first drive, and so it's ignored the sata drives and gone for the ide drive.

You don't need to add the maping entries in grub as windows doesn't need to be tricked into thinking it's on the first hard drive - it is.

Finally set your xp sata drive as the first boot drive in your bios. That's it. Hopefully everything should now work.
I did gain root access to my ubuntu installation and typed in:

sudo fdisk -l 

to which it replied:

Unable to seek on  /dev/sda

So no luck there.

> **Sale**  	

Here's what helped me with a similar hardware configuration>

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

I haven't tried your method yet, I thought I would leave as a last resort.

In conclusion I cant slave the WD10gig off anything but the DVD Drive and it seems to me the if only the installation could detect the RAID O partitions it would make life a whole lot easier and we wouldn't see so many threads that have the same problem but in so many different ways.

Maybe someone will come up with something like dmraid incorporated into  the installation to recognise the RAID partitions so one may select the appropiate partition to install hoary onto.

Anyway enough whinging.... thanks very much for taking the time to answer my questions and please if you can think of anything else that I might try I'd be greatful.

kind regards

chip

PS this could be a very useful HOW TO if it can be sorted, and I'm positive there is an answer.

---

### Post by Steve1961 on 2005-09-07
Right let's have another think.  There's always a way with Ubuntu, we just need to find it.  The fact that fdisk couldn't even read your sda drive could be because you need a sata driver.  I have two sata drives on an nforce4 controller, but these are native and don't need drivers.  Try googling for a linux driver for your sata controller. You don't give any details about your motherboard or sata controller.  If you know the details try searching this forum - someone may already have solved the problem.

---

### Post by chippy57 on 2005-09-07
[QUOTE=Steve1961]Right let's have another think.  There's always a way with Ubuntu, we just need to find it.  The fact that fdisk couldn't even read your sda drive could be because you need a sata driver.  I have two sata drives on an nforce4 controller, but these are native and don't need drivers.  Try googling for a linux driver for your sata controller. You don't give any details about your motherboard or sata controller.  If you know the details try searching this forum - someone may already have solved the problem.[/QUOTE]

Opps! yeah sorry, it would help wouldn't it:-

P4 3.2 prescott
MB= Asus P4C800E Deluxe - onboard Promise Fasttrak 378
2 x SATA WD120gig in RAID 0 with WinXP installed
1 x IDE WD10gig connected to Secondary IDE with hoary 5.04 installed
1 x DVD Drive connected to Primary IDE

I did see a mention of Promise Fasttrak 378  in on of the [http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557)  HOWTO - Discovering and using existing sata raid,  but this thread deals more with ubuntu recognising raid partitions after an installation has taken place using dmraid I really havn't come across anything else.

I would appreciate any more advice or ideas that you guys have.

regards

chip

---

### Post by Steve1961 on 2005-09-09
Sorry for the delay in replying. I've been away from my PC for a day or two.  I've done a few google searches and it seems that lots of people have had problems with this sata controller on linux kernels older than version 2.6 - so this shouldn't affect hoary in theory.  Unfortunately I haven't found a solution or a linux driver.  Have you tried the lsmod command to see if your system is loading a module for the controller?

---

### Post by chippy57 on 2005-09-09
[QUOTE=Steve1961]Sorry for the delay in replying. I've been away from my PC for a day or two.[/QUOTE]
Thats OK we all have lives to get on with, I'm very grateful for your help. 


[QUOTE=Steve1961]I've done a few google searches and it seems that lots of people have had problems with this sata controller on linux kernels older than version 2.6 - so this shouldn't affect hoary in theory.  Unfortunately I haven't found a solution or a linux driver.[/QUOTE]
Yeah I trawled around a bit but couldn't find a solution, but......
Check this out its not the perfect solution but it might work, wouldn't mind your thoughts on this before I attempt it.
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)


[QUOTE=Steve1961]Have you tried the lsmod command to see if your system is loading a module for the controller?[/QUOTE]
I have in the past dabbled with ibmdos & amigados, so I am comfortable with command line interfaces but totally a newbie with linux , so no I haven't tried the lsmod command , I really need to gen myself up on these commands. 

regards

chip

---

### Post by Steve1961 on 2005-09-09
Hi again.  The lsmod command just lists the modules loaded by linux at startup.  However, the link you supplied does offer an option.  Basically, rather than using grub as the main bootloader, it uses the windows NT bootloader with a linux option.  As windows does recognise your sata drivers this would work.  The downside is that you still won't be able to gain read only access to your sata drives, but that's a minor inconvenience compared to not be able to dual boot at all.

There are other alternatives open to you as well, but they're non-free.  When I set up my dual boot I didn't want to install grub in my mbr because I didn't trust it not to wreck my XP partition - although now I've got more confidence I wouldn't have the same worries.  However, I bought a third party programme called Acronis disk director.  This runs from XP and I use it to do all my partitioning.  It also has a boot manager which shows a splash screen as soon as I switch on, and which gives me the option of choosing whichever operating system I want to boot.  No configuration required, it's all automatic.  I install as many linux distros in as many partitions, and on whichever discs, I want, I ask the installers to install grub to the root partitions rather than to the mbr, and they just show up in the boot manager when I reboot.

---

### Post by chippy57 on 2005-09-09
[QUOTE=Steve1961]There are other alternatives open to you as well, but they're non-free.  When I set up my dual boot I didn't want to install grub in my mbr because I didn't trust it not to wreck my XP partition - although now I've got more confidence I wouldn't have the same worries.  However, I bought a third party programme called Acronis disk director.  This runs from XP and I use it to do all my partitioning.  It also has a boot manager which shows a splash screen as soon as I switch on, and which gives me the option of choosing whichever operating system I want to boot.  No configuration required, it's all automatic.  I install as many linux distros in as many partitions, and on whichever discs, I want, I ask the installers to install grub to the root partitions rather than to the mbr, and they just show up in the boot manager when I reboot.[/QUOTE]

Hi steve thanks for the quick reply, this sounds the way to go for me. I have Partition
Magic 8.01 which has BootMagic on it but I've read on this forum that it can cause a few problems. The Acronis disk director you have, is it a recent,  the latest version is 9.0 I think. I haven't used it before and wondered how it compares to partition magic.

regards

chip

---

### Post by Steve1961 on 2005-09-09
Hi Chip.  I'm using version 9, which I bought from amazon about 3 months ago when I started experimenting with linux.  I've never used partition magic so I can't really compare the two, but I've done lots of partitioning and repartitioning on my system and haven't had any problems with xp or linux.  It also allows you to format the partitions as ext3, linux swap, reiserfs, or whatever.....  At one point I was quad booting xp, fedora, xandros and ubuntu to see which I liked best.  I decided on Ubuntu after a few weeks so I repartitioned and put Ubuntu on my second sata, windows on a small partition on the first, and I created a fat32 partition with the rest of the first sata disk's space, which I share between XP and Ubuntu.  The downside is that it costs money, but it does make life simple.

---

### Post by chippy57 on 2005-09-09
[QUOTE=Steve1961]Hi Chip.  I'm using version 9, which I bought from amazon about 3 months ago when I started experimenting with linux.  I've never used partition magic so I can't really compare the two, but I've done lots of partitioning and repartitioning on my system and haven't had any problems with xp or linux.  It also allows you to format the partitions as ext3, linux swap, reiserfs, or whatever.....  At one point I was quad booting xp, fedora, xandros and ubuntu to see which I liked best.  I decided on Ubuntu after a few weeks so I repartitioned and put Ubuntu on my second sata, windows on a small partition on the first, and I created a fat32 partition with the rest of the first sata disk's space, which I share between XP and Ubuntu.  The downside is that it costs money, but it does make life simple.[/QUOTE]

Partition Magic does all of the above to....I've just been playing about with BootMagic at the moment but not having much success its a bit quirky with NTFS partitions and needs to be installed on a FAT partition, i will need to read up on the configuration I might have missed something.....but for now I must go to sleep its 01:50am here damnit....

I'll playabout with it tomorrow...err later today and let you know how I got on.

regards

chip

---

### Post by Steve1961 on 2005-09-09
Best of luck.

---

### Post by chippy57 on 2005-09-10
[QUOTE=Steve1961]Best of luck.[/QUOTE]

Well bootmagic overwrote grub, so I had to re-install grub and back to square one again lol!

[QUOTE=Steve1961]There are other alternatives open to you as well, but they're non-free. When I set up my dual boot I didn't want to install grub in my mbr because I didn't trust it not to wreck my XP partition - although now I've got more confidence I wouldn't have the same worries. However, I bought a third party programme called Acronis disk director. This runs from XP and I use it to do all my partitioning. It also has a boot manager which shows a splash screen as soon as I switch on, and which gives me the option of choosing whichever operating system I want to boot. No configuration required, it's all automatic. I install as many linux distros in as many partitions, and on whichever discs, I want, I ask the installers to install grub to the root partitions rather than to the mbr, and they just show up in the boot manager when I reboot.[/QUOTE]

This maybe where my problem is with Bootmagic, it overwrites Grub, so in theory... and I maybe getting mixed up here...if I get grub to install into the root partition then bootmagic wont overwrite it.

 

By using a terminal window is it possible to install grub to the root? or even a floppy?  because everytime I install ubuntu grub does not give me an option of where to install it, it just doesn't ask, so I cant even install it to a floppy which was one of the methods in that link I gave you. 

cheers

chip

---

### Post by Hairy_Palms on 2005-09-10
windows doesnt have to be on the first primary hard disk, heres a walkthrough on how to do it from the suse website, but it works like a dream on ubuntu aswell 
[http://portal.suse.com/sdb/en/2002/09/fhassel_grub_win1.html](http://portal.suse.com/sdb/en/2002/09/fhassel_grub_win1.html)

---

### Post by kelme on 2005-09-10
I'm going to jump in here b/c i have a very simliar situation. i actually created another thread before i saw this one.  we seem to be in almost the exact same situation.  here's my menu.lst



[i]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda1 ro

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
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST[/i]

also, here is my device.map:

[i](hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb[/i]

so if i'm reading that correctly, grub sees my ide hard drive as primary and therefore boots to it before my serial harddrive (sda).  

so i'm thinking i need to create a new entry in my menu.lst that give windows xp as an option, right?  i think sale mentioned this earlier.

[i]title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1[/i]

can someone explain what the "chainloader+1" does?  and why would i make hd0 active if i was trying to boot to hd1 & hd2? 

thanks in advance for the help.

---

### Post by chippy57 on 2005-09-11
[QUOTE=kelme]I'm going to jump in here b/c i have a very simliar situation. i actually created another thread before i saw this one.  we seem to be in almost the exact same situation. [/QUOTE]

Hi kelme when you say you have the same situation as me is it like this drive connection wise I mean:-

2 x WD120gig SATA in RAID 0 using onboard Promise FastTrak 378 with XPpro installed,

1 x dvd burner connected to Primary IDE

1 x WD 10 gig on Secondary IDE with Hoary 5.04 installed, Grub wrote itself to this drive and didn't give me a chance to write anywhere else so I can only use bios to select the boot drive. I have tried Bootmagic with no success as it overwrites grub.

There must be a way to solve this without having to use a 3rd party bootmanager. 

regards

chip

---

### Post by Steve1961 on 2005-09-11
> By using a terminal window is it possible to install grub to the root? or even a floppy? because everytime I install ubuntu grub does not give me an option of where to install it, it just doesn't ask, so I cant even install it to a floppy which was one of the methods in that link I gave you.

When you install ubuntu you get an option that asks if you want to install grub into the mbr - at least you should do.  If you select no it then takes you to another screen where you can manually select the partition where you want it installed - e.g. /dev/hda or /dev/fd0.  You should be able to install grub into your root partition with same command, even if you have to gain access to the root partition using your cd.  So, if your Ubuntu installation is on hda, you sudo grub-install /dev/hda.  I think this should also work with a floppy - sudo grub-install /dev/fd0.

> 
(hd0) /dev/hda
(hd1) /dev/sda
(hd2) /dev/sdb

so if i'm reading that correctly, grub sees my ide hard drive as primary and therefore boots to it before my serial harddrive (sda).

so i'm thinking i need to create a new entry in my menu.lst that give windows xp as an option, right? i think sale mentioned this earlier.

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

can someone explain what the "chainloader+1" does? and why would i make hd0 active if i was trying to boot to hd1 & hd2?

If all your discs are visible in fdisk -l it should just be a case of setting the priority correctly.  Windows won't boot unless it thinks it's on the first partition of the first hard drive and normally, if you have two ide drives or two sata drives and you want to put windows on the second or slave drive, then the 'map' option tricks windows into thinking it's on the first drive.  I think the main problem here is that with a mixture of ide and sata drives the question of which is the first drive is debateable, and possibly, for windows, it should just be a case of setting the boot priority in the bios.  As long as grub is installed in the mbr of this drive everything should then work OK.

The chainloader command simply passes control to the windows boot loader, it then makes the boot partition of your windows drive the active partition, and windows can then read the windows boot sector. 

> There must be a way to solve this without having to use a 3rd party bootmanager. 

Chip seems to have a different problem - ubuntu can't see his sata drives.  This means grub can't be installed in the mbr of his sata drive, and so in order to dual boot he needs to use the windows bootloader or a third-party bootloader.  When this works, the first bootable drive should be the windows drive, as set in the bios.  But you also set up the windows bootloader to include options for booting installations from other disks - e.g. ubuntu.

After reading about all these problems I have to say that I'm starting to feel very glad that I use a third party bootloader.

Anyway, best of luck guys.

---

### Post by chippy57 on 2005-09-11
[QUOTE=Steve1961]When you install ubuntu you get an option that asks if you want to install grub into the mbr - at least you should do.  If you select no it then takes you to another screen where you can manually select the partition where you want it installed - e.g. /dev/hda or /dev/fd0.  You should be able to install grub into your root partition with same command, even if you have to gain access to the root partition using your cd.  So, if your Ubuntu installation is on hda, you sudo grub-install /dev/hda.  I think this should also work with a floppy - sudo grub-install /dev/fd0.[/QUOTE]
Ubuntu has never given me an option as to where to install grub, this is what is confusing me as alot of answers in the other threads mention this.




[QUOTE=Steve1961]Chip seems to have a different problem - ubuntu can't see his sata drives.  This means grub can't be installed in the mbr of his sata drive, and so in order to dual boot he needs to use the windows bootloader or a third-party bootloader.  When this works, the first bootable drive should be the windows drive, as set in the bios.[/QUOTE]
Spot on, you've hit it right on the head, I really cant see a way around this.



[QUOTE=Steve1961]But you also set up the windows bootloader to include options for booting installations from other disks - e.g. ubuntu.[/QUOTE]
By this I guess you mean boot.ini 


[QUOTE=Steve1961]After reading about all these problems I have to say that I'm starting to feel very glad that I use a third party bootloader.

Anyway, best of luck guys.[/QUOTE]

I downloaded a trial version of Acronis Disk Director 15 days, great looking ap,  I think this is my only option,  did you mention I had to have grub installed in my root partition for it to recognise it?

At the moment Acr. Disk Director only gives me the option to boot WinXP or from a floppy. this could also be the fact it is a trial version although one would have thought they would have activated the OS Selector for 15 days too.

regards

chips

---

### Post by Steve1961 on 2005-09-12
Hi again Chip

> Ubuntu has never given me an option as to where to install grub, this is what is confusing me as alot of answers in the other threads mention this.


There's definately something wrong here.  At the end of the installation you shoud get a screen that asks if you want to install grub to the mbr.  If you answer no, you're then taken to another screen where you can choose where to install it.  If this isn't happening something - although I'm sorry to say I don't know what - is wrong with your disc, or perhaps ubuntu simply doesn't like your hardware and the installation routine doesn't work properly.

> 
By this I guess you mean boot.ini 

Yes, but you would still need grub in the root partition of your ubuntu disk.

> 
I downloaded a trial version of Acronis Disk Director 15 days, great looking ap, I think this is my only option, did you mention I had to have grub installed in my root partition for it to recognise it?

At the moment Acr. Disk Director only gives me the option to boot WinXP or from a floppy. this could also be the fact it is a trial version although one would have thought they would have activated the OS Selector for 15 days too.

This doesn't sound right either.  But you're right, the bootloader recognises all instances of grub, and if it isn't on the root partition it won't work.

My suggestion:  Try one more reinstallation and before you start delete all the partitions on the ide drive and make sure your raid array is set to boot first in the bios.  If it doesn't work, well linux is all about choices, and some distros work better with some hardware than others.  In fact, over the last few days I've had a few problems myself.  The latest batch of updates seems to have caused start-up problems that I haven't been able to fix.  So in the meantime, while I wait for the stable version of breezy, I'm giving the latest fedora core 4 a spin, and I'm very impressed.  This has the latest kernel and you might have more luck with it recognising your hardware.  

Best of luck!

---

### Post by Steve1961 on 2005-09-12
Just a thought.  If Ubuntu can't see your sata drives it probably acts as if your machine only has a single ide.  If so, the installation routine might be different - e.g. automatically installs grub in an mbr on the ide and so doesn't give you the option of installing to the root partition.

Not sure how to get round this.  Try switching the ide disc to the secondary ide port and putting your cd/dvd in the primary port - both set to master.  It might just work.  I seem to remember reading somewhere that when you use a mixture of ide and sata, with sata as your primary drives, you should avoid adding ide drives to the first ide port.  In fact, I have my dvd drive attached to the first port and ubuntu calls this /dev/hda but recognises it for what it is.

---

### Post by chippy57 on 2005-09-13
Firstly apologies for not replying sooner, I had a couple of horrendous oncalls and was catching up on some shuteye

[QUOTE=Steve1961]
My suggestion: Try one more reinstallation and before you start delete all the partitions on the ide drive and make sure your raid array is set to boot first in the bios. If it doesn't work, well linux is all about choices, and some distros work better with some hardware than others. In fact, over the last few days I've had a few problems myself. The latest batch of updates seems to have caused start-up problems that I haven't been able to fix. So in the meantime, while I wait for the stable version of breezy, I'm giving the latest fedora core 4 a spin, and I'm very impressed. This has the latest kernel and you might have more luck with it recognising your hardware.[/QUOTE]

I'm going to have another bash at this and wipe the IDE completely, it is already  on the Sec IDE and my DVD in on the Pri IDE although I haven't used the jumper to set them to Master which I will try, I think if I can get grub installed on the root it will solve my prob and  Acronis Disk Director will hopefully recognise it,  excellent prog very slick  and BTW the OS Selector is fully operational for the 15 day trial. In fact I think I will purchase it anyway so I can then play about with some of the other distros around.

What do you think of Linspire?Cant remember if it is a freebee.

Anyway thanks alot for your advice it is much appreciated and invaluable.

cheers

chip

ps congrats on the ashes.

---

### Post by leezer3 on 2005-09-13
Linspire- Not with a bargepole :P
Basically this asks three questions in the install- Keyboard type, mouse, JUNK EVERYTHING?

Maybe you should have a try with GRUB for DOS- This is basically grub loading out of  
a Windoze partition, and might get round your probs.

Cheers

-Leezer-

---

### Post by Steve1961 on 2005-09-13
> I'm going to have another bash at this and wipe the IDE completely, it is already on the Sec IDE and my DVD in on the Pri IDE although I haven't used the jumper to set them to Master which I will try, I think if I can get grub installed on the root it will solve my prob and Acronis Disk Director will hopefully recognise it, excellent prog very slick and BTW the OS Selector is fully operational for the 15 day trial. In fact I think I will purchase it anyway so I can then play about with some of the other distros around.

Best of luck chip and I agree about Acronis.  For about 20 quid over here it's pretty impressive and I haven't had the same problems that some people seem to have suffered with linux recognising partitions created in partition magic.

> What do you think of Linspire?Cant remember if it is a freebee.

Depends what you want.  Basically it's a windows clone so it's very easy to use.  You might be able to get hold of a free version, but you have to pay a fee to use their software warehouse.  Xandros is similar, but you can get this for free.  I tried xandros but found it very restricting - just like windows but without the flexibility of other linux distros.  That said, a good distro to cut my teeth on.

> Anyway thanks alot for your advice it is much appreciated and invaluable.

cheers

chip

ps congrats on the ashes.

No problem, if linux users, and potential users, don't help each other out none of us would learn how to use this system.  And the more I'm learning the more I'm coming to  prefer it to windows.  Thanks for the congrats.  Lots of very happy people over here.

---

### Post by chippy57 on 2005-09-13
[QUOTE=Steve1961]
Depends what you want.  Basically it's a windows clone so it's very easy to use.  You might be able to get hold of a free version, but you have to pay a fee to use their software warehouse.  Xandros is similar, but you can get this for free.  I tried xandros but found it very restricting - just like windows but without the flexibility of other linux distros.  That said, a good distro to cut my teeth on.[/QUOTE]
Nah! Like you I'll wait for a stable version of Breezy in the meantime I my try fedora core 4 but I'll def get Acronis.


[QUOTE=Steve1961]No problem, if linux users, and potential users, don't help each other out none of us would learn how to use this system.  And the more I'm learning the more I'm coming to  prefer it to windows.[/QUOTE]
This is exactly what I like about the linux community and I'm slowly heading towards being less reliant on windows.


[QUOTE=Steve1961]Thanks for the congrats. Lots of very happy people over here.[/QUOTE]
Your welcome, its about time and well deserved. Lots of very very long faces here :-#  lol.

---

### Post by chippy57 on 2005-09-13
Thanks leezer3 for your reply.

[QUOTE=leezer3]Linspire- Not with a bargepole :P
Basically this asks three questions in the install- Keyboard type, mouse, JUNK EVERYTHING?[/QUOTE]
Well thats knocked that one on the head lol.

[QUOTE=leezer3]Maybe you should have a try with GRUB for DOS- This is basically grub loading out of a Windoze partition, and might get round your probs.[/QUOTE]
Interesting concept, please would you care to enlighten me further...I'll try anything at this point in time

regards

chip

---

### Post by leezer3 on 2005-09-14
Have a google- It's the suggested method for a network install, as GRUB is installed & runs from the Windows partition, as opposed to the MBR/ Linux install of the standard GRUB. I've never tried it, and so can't be of much help here. However, as Windows actually recognises your drives, this should allow GRUB to load properly.

Hope this helps

-Leezer-

---

### Post by chippy57 on 2005-09-14
[QUOTE=leezer3]Have a google- It's the suggested method for a network install, as GRUB is installed & runs from the Windows partition, as opposed to the MBR/ Linux install of the standard GRUB. I've never tried it, and so can't be of much help here. However, as Windows actually recognises your drives, this should allow GRUB to load properly.[/QUOTE]

Thanks for your suggestion, makes sense. I will do a search and see what I come up with, all part of the learning process I guess. If the poo hits the fan, I can always do a fdisk /mbr

cheers

chip

---

### Post by leezer3 on 2005-09-14
[QUOTE=chippy57]Thanks for your suggestion, makes sense. I will do a search and see what I come up with, all part of the learning process I guess. If the poo hits the fan, I can always do a fdisk /mbr

cheers

chip[/QUOTE]

I believe (And don't quote me on this  :-# ) that GRUB for Dos doesn't actually do anything to the MBR, but instead overwrites the Windows bootloader, so a fdisk /mbr may not actually fix whatever it screws.

Cheers

-Leezer-

---

### Post by chippy57 on 2005-09-14
[QUOTE=leezer3]I believe (And don't quote me on this  :-# ) that GRUB for Dos doesn't actually do anything to the MBR, but instead overwrites the Windows bootloader, so a fdisk /mbr may not actually fix whatever it screws.[/QUOTE]

hmmmm...better tread carefully. There is a thread or HOWTO on writing something in boot.ini , I must check it out again.

thanks

chip

---

