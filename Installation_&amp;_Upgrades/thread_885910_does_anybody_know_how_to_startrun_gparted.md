---
title: "does anybody know how to start/run gparted"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by getagrip on 2008-08-10
[B]I have a problem trying to install hardy heron. 
I can't get beyond the ... "grud file loading 1.5" ...screen

I tried using a recovery disk to reformat the HD but it will not overwrite/erase/delete the corrupted portion of my HD holding the initial messed up install.

I have no OS, XP has been wiped from my Disk, and will not re-install with this corrupt partition.
I can only boot my system from the Ubuntu CD. 

How do I start gparted to somehow remove this partition from my drive?

sine I have an extra drive on my machine I download the file on another computer and created a bootable CD with the ISO file ...but I'm stuck at what to do next.

Also booting on the corrupt machine with the bootable linux CD I can get online  and download the zip file for gparted. But what/how ...do you open this file? 

I keep trying to read the instruction at the gparted site but it reads as if you have workable operating system ..and you know how to open this file. 

What do you open it with ...I see where they have some command typed ...where, how ...what ...do I type these commands? [/B]

---

### Post by Pumalite on 2008-08-10
Get Gparted Live CD and let's see if you can boot it:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
If not;
try TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Shazaam on 2008-08-10
Windows might still be there. Boot the Ubuntu livecd, go to Applications>Accessories>Terminal. Type this in the window that opens and post the results here.....
```
sudo fdisk -lu
```
(small L)
If fdisk still shows Windows is there reboot your pc. At the boot screen hit your "Esc" keyboard key to get to the grub boot menu. Using the up/down arrow keyboard keys highlight Windows, press ENTER and see if Windows will boot.

"I download the file on another computer and created a bootable CD with the ISO file" Is that the stand-alone gparted livecd?

---

### Post by Pumalite on 2008-08-10
Faster way to see if Windows is still there is to get Super Grub and try to boot it:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
(Besides, Super Grub is great to have around anyway)

---

### Post by getagrip on 2008-08-10
[COLOR="DarkOliveGreen"]*Windows might still be there. Boot the Ubuntu livecd, go to Applications>Accessories>Terminal. Type this in the window that opens and post the results here.....*[/COLOR]


Ok so thats where you type the commands. 
This is what I get when I type .."sudo fdisk -lu" and hit enter.



[B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e64c0

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ [/B]


Windows is gone after the billion re-formatting I have been doing for the past 2 days now. 
When I look into this /dev/sda ...partition I don't see the grub sub-folder in the boot folder. Hence no ..."menu.lst"... file and I believe this file is necessary to boot.  I want to delete ..erase, this partition from my HD....but for 3 days now ..I have been unsuccessful.

---

### Post by lisati on 2008-08-10
> **Pumalite said:**
> Get Gparted Live CD and let's see if you can boot it:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
If not;
try TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

gparted should be on the LiveCD already

---

### Post by getagrip on 2008-08-10
I don't mean to be dense ..but I burned the iso to a blank CD as a bootable disk. But when I plug it in and restart all I see is ...[DR-DOS] A:\> .... 

for sure its trying boot since I set my BIOS to boot from the CD drive before the HD. 

Am I missing something ..because the website shows a screen for this boot which I'm not seeing.

---

### Post by grungedoobie on 2008-08-10
Why not just use cfdisk from linux command prompt?  I know it isn't pretty, but it does a good job.  Just follow the commands listed at the bottom of the screen.  The up and down arrow keys cycle the partitions and the right and left arrow keys cycle the command options.  To enter cfdisk, type: 

sudo cfdisk

Use the working linux disk to do this of course.

Also, linux ISO's are bootable by nature.  You do not need to "Make" them bootable.  Doing this will create a disk bootable to the operating system you created it on.  I'm thinking the cd was burned using microsoft.  When the "Make it Bootable" option was engaged, you made a dos boot disk with an unuseable copy of the linux ISO.

---

### Post by getagrip on 2008-08-10
OK great I'll try that!!

 I've used fdisk a million times over the past few days but it was always from a DOS window using my XP recovery disk.

Lets see what happens now ...thanks!!

---

### Post by getagrip on 2008-08-10
I'm sorta winging things with the syntax here ...but 

fdisk /dev/sdc  yields ....unable to open /dev/sdc.

I went back and look at how linux designates partion as sectors. If you look at my earlier post when I pasted what ...."sudo fdisk -lu" yields.

[B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e64c0

Device Boot Start End Blocks Id System
ubuntu@ubuntu:~$ [/B]

If I understand correctly ...63 sectors!!!??  My HD is messed up after all the re-installs and uninstall attempts ..I just need to delete the $#@&** crap and start over!!! 

I already made backups ..so starting over is no big deal ..I don't need to save anything ..I don't care if XP is gone ..I just want to wipe clean the HD and start over!  

I'm little steamed because after 2 days I don't know whether throwing away the HD isn't the best solution!!

---

### Post by grungedoobie on 2008-08-10
My first several attempts at playing with linux partition editors were somewhat not cool as well.  Do you know if there was anything wrong with the drive before hand?

It looks like your partition query from fdisk is only showing an 80Gig Drive.  You multiply the number of heads times the number of secters, then multiply that by the designated 512 bytes.  So, yes, your drive has 63 sectors.

Were you able to get anywhere with "cfdisk"?

When the changes are made in cfdisk, the computer must be rebooted immediately after saving and exiting cfdisk.  If you try to check the drive after saving the cfdisk changes but before rebooting, Linux will automatically salvage the drives boot sector.  In effect, checking the drive in the manner will undo the cfdisk changes.

---

### Post by Pumalite on 2008-08-10
> **lisati said:**
> gparted should be on the LiveCD already

I'm aware of it. The Gparted Live CD is superior. More flexible, newer version, more control. It's great to have around.

---

### Post by grungedoobie on 2008-08-10
There is definitely no comparison between cfdisk and gparted.  I LOVE gparted.  It is super easy to use and extremely powerful.

If I gave any other vibe, then I apologize.

I just wanted to give an option that I knew was available.

8-)

Extra tidbit:  After removing the boot sector from the drive, when you install the operating system on the drive, your operating system will automatically make the drive useable to the platform of your choice and wipe the rest of the drive for you.

Oops, silly me, crossed wires.  My bad Puma.

---

### Post by getagrip on 2008-08-10
Guys thanks ...I tried cfdisk ..which was very straight forward ..and reinstalled Ubuntu ..and it failed again with the same message.

**GRUB LOADING STAGE 1.5**

 I'll try to do it again and reboot first as you've instructed. One of the issue I had during the install was in using the manual partitioning...i did some research and was able to tell which sector of the drive was to boot ...usr etc. But everytime I hit forward ..i get a ..CANNOT FIND ROOT DIRECTORY error. 

After this failure I said ...since I got Ubuntu on my laptop running ok ..why not use cfdisk to check to see how that drive was partitioned. 

I spoke too soon!! I tried to start ubuntu on my laptop and got this message ....

[B]BUSYBOX V1.1.3 (DEBIAN 1:1.1.3-5 Ubuntu/2) BUILT -IN SHELL (ASH) ENTER HELP FOR A LIST OF BUILT IN COMMANDS

(INITRAMFS)[/B]

[COLOR="Red"]

[SIZE="4"]**YYYAAAHHGGG!!! Its coming after my only working machine now!!! **[/SIZE][/COLOR]:(

Why would this happen? It worked perfectly a day ago..since then I've only booted in XP

---

### Post by grungedoobie on 2008-08-11
Just out of curiosity, has linux been installed on the same drive as windows?

This is not advisable as microsoft has a long history of scrambling linux partitions.  Linux tried for years to make their system capable of living side by side with microsoft, but microsoft makes updates that scramble linux all over again.

The safest way to dual boot is to have two drives.  Install Windows on the first drive with the first drive installed by itself.  When the Windows installation is finished then shut down and put the second drive in the computer.  Then boot directly to the linux live cd.  Do not activate the second drive while in Windows as it will make a mess of any other operating system you wish to install.  When you go through the live cd installation tell it to use the entire secondary drive, this will leave no extras for Windows to try to take hold of.  This is the configuration that I have set up on my mothers computer for a month now, and there have been no problems.  One very big thing, do not access the Linux drive from the Windows or vice versa.  As Windows will trash the Linux drive.  If you want to share information between the two operating systems, here is what I have done.  I got a USB drive, it's a maxtor 250Gig.  I formatted the drive as a MSDOS FAT16 drive.  Doing this cost almost 70Gigs, but it was the most stable configuration I could find.  I have to turn the USB drive off between boots though as Windows leaves trash in the USB drive's onboard memory that makes it unstable when changing over to Linux.  Turning the drive off clears out the trash.

In a perfect world, manufacturers would create friendly operating systems that perform as advertised, stay within codes of decent conduct and adhere to globally recognized guidelines.  But, Microsoft just won't do it, so, we have what we have.

If you are wondering why I have made my mothers computer dual boot, I installed a new hard drive that her Windows could only see half of (BIOS could see all of the drive).  The answer that Microsoft had was to buy Windows operating system again, and that just seemed silly.

There is another way to do this, and that is with Linux installed on the drive first.  Then a program can be installed which is called VirtualBox.  My dad has his computer configured this was and it seems to run well.  Windows is a little bit slower this way, but Windows doesn't have the ability to scramble the linux installation.  Using virtual box uses lots of cpu power as you will in effect have two operating systems running at the same time, so if yours is less than a dual core with lots of ram, I wouldn't advise it.

---

### Post by getagrip on 2008-08-11
Thanks ... here is what I'm doing. I am in the process of building a new machine ..in fact I'm doing the work and dilligently selecting the parts to buy. What I want this system for is 3D graphics and animation ..and Blender is the tool I intend to work with among others. 

So I'm experimenting with Ubuntu ..when it works ..its great! Blender ...works better using Ubuntu (Idon't know why) it renders faster when running installed on the HD for example. Plus I've had it with microsoft and refuse to be dragged by the neck by them any further.... I don't want Vista!! But for this system I intend to use a RAID set up for my HD to gain speed ..I'll have at least 2 seperate internal HD. 

I intend to install Ubuntu solely on this machine ...but the way its corrupted my HD on my existing desktop machine is not making me feel good. When I get back from work today I'll try to use your method to fix the desktop. 

That aside ..on my laptop I run XP ...its a actually a tablet machine using a Pentium M CPU ... with only a 80G HD. On that HD I have some 20G free ...and thats where I put Ubuntu. I want to keep using XP as a back up for now ... whats your advice trying to put Ubuntu on this system? 

Should I run out and buy a USB drive and put Ubunto on this drive and live with the limitation? Would it run effectively?

I have no plans to upgrade the HD on this machine (using only a Pentium M) especially since I don't have the XP disckette to install it on an upgraded drive. 

Tonight I 'll try cfdisk and reboot before trying to re-install Ubuntu on the desktop ...because its really bothering me that I can't get over this hurdle. AFter all whats to stop Ubuntu from screwing up my new system when I do get it.

---

### Post by Pumalite on 2008-08-11
If you want to install in USB:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by grungedoobie on 2008-08-11
Wow, ok that clears up a lot of haze for me getagrip.  

Ok when making a desktop from scratch, I would suggest googling each individual part for linux issues.  No, not the capacitors and diodes, but the drive, the motherboard, the chipset, the video card, the memory, stuff like that.  Google is my friend, and has given me answers to most of my questions.  I've come across quite a few HDD issues between linux and raid drives, and usually there is a work around somewhere.  I've not dealt with raid drives personally, so I'm not much help there.

Bios accelerators like "Fast Boot" can make the boot sequence unstable.  I think I said that before, my bad.

Some motherboards these days have overclocking options right in bios.  I have found that overclocking can make a system become unstable if just one part has even a minor compatibility issue.

Another thing to watch for is peripheral placement.  I built my computer out of a box of old spare parts that my brother was about to toss, some stuff I had lying around and some stuff my dad had.  The onboard video and audio were crummy and the onboard networking was unuseable.  So, I put cards in.  Linux didn't like me just putting cards in, it wanted to have them in some sort of order.  I have an AGP slot but the card I found for it was too fast for the mobo, so I used a PCI graphics card that windows had deemed fried.  I don't know how, but linux made it work.  Linux wanted the ethernet card after that, and the sound card after that.  I could get into bios with no problem on any configuration, but Linux would only boot with the PCI bus cards in this order: Video on primary odd PCI, networking on primary even PCI and audio on secondary odd PCI.  I'm not going to say that this order will work for you, I'm just saying that this was what I had to do, I had to play with the parts to find the right combination.

Something to be careful of, Power Supply.  There are calculators out there that can help you to make sure the one you have is enough for your hardware.  Be very careful.  If you get a supply that just breaks even, you will run into a plethera of weird problems (including bootup problems) and things can get toasted.  If you are able to, find out what your parts need then go an extra 100Watts.  If you are planning to upgrade in the future, the go even higher.  I have a little old computer, but even it has a turn on spike of 2.5 amps which calculates to 300 watts.  I have a 350 supply in the box, it's not in my comfort zone, but it's what I have, and it works.

This is a minimum calculator that I use:

Motherboard - 75Watts single core, 150Watts dual core, 300Watts quad core
Each Drive - 50Watts EIDE, 75Watts SATA, 100Watts RAID
Peripheral cards - Find recommendation as there are a million of them.

Even after all that, it is always best to find the specs for your parts and go from there.

I have a live CD for most of the Linux platforms, and some of the Live cd's are for different installs of the same flavor.  I am running Kubuntu Hardy Heron on my computer.  It's a 550MHz pentium with 640Mb Ram with one 80Gig HDD, two Opticals and the peripherals I mentioned before.  The Hardy Heron install cd for Kubuntu doesn't work on my machine.  I have to use the Feisty Fawn installation, make the hardware and software environment what I want it to be, then upgrade to Gutsy and then to Hardy.  I'm not saying that what I did to mine will work for you, I'm just saying that you may need to play with different flavors to find one that works the way you want it to.  The reason for this is that each install package has a different driver package to interface with the most common machines within its release date and for which the package was designed.

Another thing to watch for, be absolutely certain that your hardware arrangement is compatible for 64 bit before using the 64 bit software.  Trying to run 64 bit software on 32 bit or less system will cause tears.  The 64 bit hardware starts at dual-core.  However, it is possible that some very early releases of dual-core may not work with the 64-bit software (I have not run across this myself, but have only heard of it).

I am sorry, I know that was a lot to chew on.  When you get into the nitty gritty of computers, things can get overwhelming at times.

Now, for the laptop.  Ouch.  Does windows still boot?  Laptops are more difficult to put linux on as they have greater limitations.  Windows does not like any other operating system installed on the same drive.  Even when it is one of its own.  I worked on a windows laptop that had two partitions on it.  The primary was FAT32 and the secondary was NTFS.  The FAT32 being the primary completely trashed the NTFS and the files in it.

This is what I had to do to fix it.  I used a linux boot disk (it was an old laptop so I used a SLAX live cd).  In linux I took the info from the drive and put in on the USB drive that I mentioned in a prior post.  I then cleaned the drive on the laptop and made it one contiguous partition of FAT32 using "cfdisk"(and made it bootable of course).  I rebooted onto a windows 98 recovery cd and formatted the hard drive.  I then rebooted to linux and returned the operating system from the USB drive back to the laptop.  I then rebooted to the hard drive force entering to safe mode and did the standard system checks.  When that was finished, everything worked properly, and there was more room for the os to breath.  This was an option of last resort.  If any one step in something like this goes wrong, everything will be lost.  Word of caution when transferring an entire drive, double check to make sure everything is in order, and make an extra copy of the drives root directory in a seperate folder in case something goes wrong with the roots boot files.

You can google around and find windows boot disk ISO's if you want.  I did and it turned out to be a great help as I made the CD open ended and could add utilities after the first burn (I made that CD using K3B burning tool from my Kubuntu machine).  One word of caution when adding software to an open ended cd, put the new software in its own directory.  If you try to put the new software in the root directory, it will trash the cd.

I hope this helps, even though it is severely long winded.

---

### Post by grungedoobie on 2008-08-11
I sure hope you havn't given up, because I have news.  My dads dual-core 64-bit system with Kubuntu on it did an upgrade.  The next time he tried to boot, it made it to the "Grub Loading 1.5" then dumped him to the login you would see if you were in the shell prompt.

Wow.  What to do.  So, I logged into the OS right there at the prompt.

I first did:

sudo apt-get check

This showed up nothing. So then I:

sudo apt-get autoclean

This took out six files.  So then I:

sudo apt-get autoremove

This took out three more files and unclogged the updater.
Lots of files immediately updated including major system files.
So after that I:

sudo apt-get upgrade

Several more files updated, so I:

sudo apt-get autoclean

Nothing more happened, so I:

sudo shutdown -r now

The system rebooted, and no more problems.

I'm praying that this is the problem with yours as it is an easy fix.

Best of luck,

The Grunge

---

### Post by getagrip on 2008-08-11
Guys ...thanks ...spent another 2 hours trying all the things suggested above ...no luck! 

I still get the ..**"GRUB LOADING STAGE 1.5"** message. 

I think I've been humbled ...what saddens me isn't losing the use of my machine ...not loosing my files ...its the fact that there is every reason to believe that this could happen again!!  

I was excited a few days ago ...I even went out and bought the linux program magazine which ran a Ubuntu special with the latest isos packaged in a DVD! I read it cover-to-cover now I feel like I've been kicked in the gut! 

I even did some Googling ...and found this site ..

[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)


followed the steps .. and use this command ..fdisk /dev/hdb ...it tells me there is no such disk. 

Luckily I have my lap-top working again with XP ...I immediately un-installed Ubuntu ...because I can't take a chance of loosing both machines!! 

For all the bad-mouthing windows gets ..it at least takes measures to fix itself.  

The **GRUB LOADING STAGE 1.5** message I googled for days ...even before I joined this forum. 

Its very very pervasive ...I looked at threads dating back to 2003 on the same issue ..and yes this is .."free" .. but my god ... this should have been an issue addressed long ago before toting this product as competitive!! 

[COLOR="Red"]
[SIZE="5"]
**What can I say about a product that wipes away my file, denies my HD from being re-formatted, and phrohibits re-installation of the original OS (XP)? I think I know the answer ..I'd call it a #$@%* ...virus!! **
[/SIZE][/COLOR]

:evil:

I think I'll stick with the devil I know ..lest I spend the rest of my life trying to boot with this #@$@**! OS. 

[I]**PUMALITE**

If you want to install in USB:
[http://www.ubuntuswitch.com/2006/08/...sb-hard-drive/](http://www.ubuntuswitch.com/2006/08/...sb-hard-drive/)[/I]

BTW this link takes me nowhere...but thanks for your effort anyway. At least you guys treat me better than this POS ..OS have!!

---

### Post by grungedoobie on 2008-08-12
I am so sad that Linux isn't working for you.  It has done wonders for me, however I am using it on older computers (although I have installed it on machines up to dual core, one a desktop and the other a laptop, with awesome results).  My personal main box is Pentium 550MHz, and my laptop is Pentium 366MHz.  And even the laptop is great for online gaming (when the details are toned down, lmao).  The thing is, they just plain work.  

We have a couple of kids in the house.  They use the 550 box and put it through the ringer on many occasions with their happy clicking keyboard pounding button pushing childlike ways, and they have yet to make the system crash (if you've seen monkeys bouncing around in a zoo, then you have an idea of how excited these kids can get when playing with the thing).  It has all sorts of games, graphics and paint programs on it (mostly geared towards children).  The oldest one uses it for web surfing for kids online games and gets into all kinds of web pages and I have yet to contract a virus (the 550 box has been up and running for nearly two years now).  For the most part, Linux on the 550MHz boots faster and runs cleaner than XP does on a 1.8GHz machine (I timed them).

Perhaps one day, Linux will step up to the plate and work for you.

You have been a help to me in a way.  My brother is building a super computer.  It's a quad-core / sli ready / dream machine.  I will advise him to use SATA until the Linux groups are able to fix the RAID bugs.  For that, I do thank you.

I believe Microsoft has ported XP to 64 bit systems.  You might want to check it out.  I hate the thought of anyone going back to windows.  I was a follower myself for a lot of years.  

Oh well, I'll stop now as this isn't helping anyone.

Good luck to you, whatever you chose.

A saddened Grunge

** Side Note **

I don't like saying this because I don't like looking stupid (ok, so the avatar is me, but that's my Goofy-Goober face I swear).  My first Linux install was more than two weeks of hair pulling mayhem.  I'm down to about four hours now, and most of that is waiting for installations and upgrades.  If you stick with it, you may be able to figure it out, the rewards are oh so sweet.

One other thing, typically the primary master hard drive is located at "/dev/hda".  However, different flavors of linux have different designations in their file structures.  I ran across one that called the primary master hard drive "/dev/scsa" (it was an ide drive). Another gave a windows formatted drive which was in the primary master position the designation of "/dev/hdc".  Just something to poke at, my bad.

---

