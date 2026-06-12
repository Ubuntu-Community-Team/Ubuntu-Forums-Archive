---
title: "So I installed Ubuntu/Linux for the first time....help!"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by zXen on 2006-03-02
Ok,

Firstly I partitioned my 120gb sata HD to a 20GB partition for my Ubuntu installation.
 I then restarted Ubuntu booting off the DVD for the instllation. Once I got to the partitioning screen i made a swap partition of 512mb, the remaing space i used for my Ubuntu installation, making sure that the Bootflag was On and the Mount Point was set to (/) root directory. #
 I then installed and set all the normal stuff, installed GRUB, then when I restart it says "Error Loading Operating System"
 So at the moment I am typing this through booting off my live Ubuntu DVD, because if i dont boot off a CD/DVD then i cant get passed the "Errior Loading Operating System" message.
Any ideas whats happened? How to fix it? and if there is any way of saving my Windows Installation.

Thanks

---

### Post by splint on 2006-03-02
when you restart does the grub boot loader show? Also did you make the linux partition before or after the windows? Your windows install is still there so you can defo get it back, unless you wiped it when partitioning :p

---

### Post by Herman on 2006-03-03
First, if you just recently made any changes to the boot sequence in your [BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm") (to get your CD/DVD to boot), check that you still have your hard disk as one of the devices in the list.

Second, make sure there is no floppy disk in the floppy disk drive, especially if your floppy drive is second in the list and hard drive third.

Third, if you still can't get it to boot, try re-installing Grub by whichever one of [these methods]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") seems the easiest for you. Maybe the Super Grub Disk would be the easiest if you are new to Linux. [Here's]("http://www.ubuntuforums.org/showthread.php?t=114332") another way, and [here's]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=re-install+grub") yet another way. Just pick one or two of all these methods, that you like. (You don't have to try every one). If Grub refuses to go in after one or two attempts there may be some other problem. Post back here again if so.

Don't worry, your Windows installation will be fine. You could even boot it in the meantime if you get too impatient and fixing grub looks like it will be more complicated than anticipated, with [GAG]("http://gag.sourceforge.net/") on a [System Rescue CD]("http://www.sysresccd.org/Main_Page"), or by [making your own GAG boot floppy or CD.]("http://www.users.bigpond.net.au/hermanzone/p12.htm") You can also use GAG bootloader to install to MBR if GRUB won't work for you. 

However, I'll bet your problem is something pretty simple and easy to fix.
I hope something here will have solved it for you already.:-D (Herman)

---

### Post by zXen on 2006-03-03
[QUOTE=splint]when you restart does the grub boot loader show? Also did you make the linux partition before or after the windows? Your windows install is still there so you can defo get it back, unless you wiped it when partitioning :p[/QUOTE]

Yes, I made the partition in Windows before hand and then when installing Ubuntu I used the unallocated space installed Ubuntu and the Swap.

[QUOTE=Herman]First, if you just recently made any changes to the boot sequence in your BIOS (to get your CD/DVD to boot), check that you still have your hard disk as one of the devices in the list.[/QUOTE]

Didnt make any changes and the Hardisk is the second bootdisk after the CD/DVD ROM.

[QUOTE=Herman]
Third, if you still can't get it to boot, try re-installing Grub by whichever one of these methods seems the easiest for you. Maybe the Super Grub Disk would be the easiest if you are new to Linux. Here's another way, and here's yet another way. Just pick one or two of all these methods, that you like. (You don't have to try every one). If Grub refuses to go in after one or two attempts there may be some other problem. Post back here again if so.[/QUOTE]
Ok, I tried typing in rescue and got to the point where it wanted me to select "Device to mount as Root File System" and gave a list of:

"/dev/discs/disco/part1"
"/dev/discs/disco/part2"
"/dev/discs/disco/part3"
....etc

Here I don't know what to select, any ideas?

---

### Post by Herman on 2006-03-03
Normally whichever partition you installed Ubuntu on would be the one to choose.
If you don't know choose <Go Back> and scroll down to 'abort the installation' and exit the installer. 
To find out which partitions are which you can look at them by running the install CD again, the normal way this time, making a note of the list of partitions in [!!] partition disks, then using the <Go Back> option (with your tab key) and scrolling down and exiting again.
Or you can run some other live CD or partitioner on a CD to have look and make a note of which partition is your new 'Breezy' install.

How many partitions do you have anyway, and which are primary, extended and logical?

---

### Post by zXen on 2006-03-03
So the I have to choose one of these? are they partitions? because it looked like stuff that i select to boot off the dvd.

"/dev/discs/disco/part1"
"/dev/discs/disco/part2"
"/dev/discs/disco/part3"
....etc

I have two HD's, first one is my data drive, the second one has Windows in one partition, the second partition is a 512mb Swap partition and the third is the rest of the space lett on the disk with Ubuntu installed.
 I was advised to set all of these to Primary. I made sure that the Bootflag was On and the Mount Point was set to (/) root directory for the Ubuntu installation.

---

### Post by soonindallas on 2006-03-03
[QUOTE=zXen]I made sure that the Bootflag was On[/QUOTE]

This is your problem.  Attached is gparted's view of my hd.  note that the boot flag is set for hda2 which is my XP partition.

Reset your boot flag to your win partition using the ubuntu installer partitioner.  skip to grub setup.  Put grub in your mbr as it will likely suggest if it detects windows.

post back with your results.

---

### Post by Herman on 2006-03-03
Those are your partitions, select /dev/discs/disco/part3 then, if that is your Ubuntu partition. Your computer will boot from your MBR on the first sector of the first track of the first hard disk. That's where you want GRUB's IPL written to. (Herman).

---

### Post by soonindallas on 2006-03-03
[QUOTE=Herman]Your computer will boot from your MBR on the first sector of the first track of the first hard disk.[/QUOTE]

not if the boot flag is not set.  see my previous post.

---

### Post by zXen on 2006-03-03
[QUOTE=Herman]Those are your partitions, select /dev/discs/disco/part3 then, if that is your Ubuntu partition. Your computer will boot from your MBR on the first sector of the first track of the first hard disk. That's where you want GRUB's IPL written to. (Herman).[/QUOTE]

When it listed the /dev/discs/disco/part(x) there was more than 3 (hence why i put the "etc" earlier), this would be confusing though as i have only 3 partitions on my second HD.

---

### Post by soonindallas on 2006-03-03
dude, it's your wrongly-set boot flag.

---

### Post by zXen on 2006-03-03
Yeah, I'm gonna change that mate, just wanna get all possible information before i get home and can start changing a few things

Thanks for the help btw guys ;)

---

### Post by Herman on 2006-03-03
> When it listed the /dev/discs/disco/part(x) there was more than 3 (hence why i put the "etc" earlier), this would be confusing though as i have only 3 partitions on my second HDWell I have twelve partitions here right now in this test computer, and there are twelve /dev/discs/disco/part(x)'s in the list I'm getting, so I think that's okay. It would be strange to have extra partitions you don't know about...hmmm.:-k

It might pay to investigate things a little more before doing too much,then, maybe. It would be best to check with a partitioner or live cd and find out what is going on with your partitions.

Try soonindallas's idea, I never pay too much attention to the boot flag, I usually set it on whatever partition I am working on at the time, or just ignore it. Might be something I don't know yet, (I know there's lots I don't know yet).

---

### Post by zXen on 2006-03-03
[QUOTE=soonindallas]This is your problem.  Attached is gparted's view of my hd.  note that the boot flag is set for hda2 which is my XP partition.

Reset your boot flag to your win partition using the ubuntu installer partitioner.  skip to grub setup.  Put grub in your mbr as it will likely suggest if it detects windows.

post back with your results.[/QUOTE]

Ok, I swapped around the boot flag and now its booting into Windows, just wondering how you "Skip" to Grub setup? and what is an mbr?

---

### Post by soonindallas on 2006-03-03
if it boots into windows then you didin't install grub properly.

"skip to grub setup" means go to this step in the install process.

mbr is the master boot record on the disk.  grub will sit there, run when you start your box and give you the choice of OS to boot.

I'm guessing you followed the first part of my post but not the second...  that's ok because you are now reassured at least about your win install working! 

reboot with your installation cd.  go through the partition bit without changing anything and go to the grub install stage.

when grub install says it has detected Windows as another OS residing on your disk accept installation of grub in your mbr.

then you should be set!

---

### Post by zXen on 2006-03-03
Ok, I got to the partition bit and selected "Manual Partitiom" as all the other ones were to do with erasing. So it went to the screen that lists the partitions and I clicked the "Finish Partitioning and save to disk" as i didnt want to change anything. Then when it went to the next stage it wanted to format my swap partition, so i clicked "Yes" then it said "No root file system is defined". Then i went back to the partition which Ubuntu was installed on to check if the mount point was selected as a "Root", instead for some reason it was "media/sda3", so i changed it back to "Root".
 Once everything was changed I went back and selected "Finish Partitioning and save to disk". Then lots of red boxes appeared saying that i cant proceed because there is already data on there (Ubuntu). So I aborted installation.

I then tried booting into the installation and once i got to the partition section i hit esc and went to the installation menu and selected "Install Grub Boot Loader on Hard Disk", I selected this and it took me to the partition screen, of course i cant really do anything once i get to the partition screen due to the problem listed above.

---

### Post by soonindallas on 2006-03-04
ok.  you don't mention whether you changed the boot flag to set it for your win partition and reset it for your ubuntu root partition.

if you achieved this, I suggest you use Herman's idea of the super grub disk to make sure you reinstall grub to your MBR.

[http://adrian15.raulete.net/grub/tiki-index.php?page=En](http://adrian15.raulete.net/grub/tiki-index.php?page=En)

of course if you don't have any precious data in your ubuntu install you can safely reformat those partitions and proceed with the installation using the breezy installer: set the flags (boot flag set for win partition), and for your linux partition change the format option from "no, keep existing data" to "format...".  this is your simplest option.

---

### Post by zXen on 2006-03-04
I just tried the Grub Super Disk and when i got to the part of the installation where you select "AUTO" it didnt complete and kept saying "Selected Disk doesn't exist" and "Partition does not exist". *Sigh*.

I decided to re-install Ubuntu from scratch again, when i got to the Grub installstion section it says the following OS's are installed, it listed "Windows XP Proffesional *twice*. Could this be part of the problem im having? maybe because beforehand i made a partition in WinXP for Ubuntu to use?

---

### Post by soonindallas on 2006-03-05
curious.
I suggest you use the windows utility to fix your mbr  using the windows rescue cd.  search the forums for something like "fix mbr" and you'll find detailed instructions.

then reinstall breezy from scratch.

gl.

---

### Post by zXen on 2006-03-05
Just used the repair facility in the WinXP disc, then ran the "fixmbr" command and said that my mbr was non standard or invalid, so i chose to fix it and it said it was successfully completed. Rebooted and still would not load Grub, changed the bootflags on each drive to test and it still didnt appear and didnt run Ubuntu, XP still worked fine.

So i tried a fresh install, same old problem, still says there is two WinXP installations when there isn't. Super Grub disk still doesnt work.
 I was thinking that it could be detecting two WinXP installations because I installed Windows on top of itself a while back due to corruption and didnt want to format and lose data. In the process the drive letters C: and D: switched so this is the only explanation i can think of.

---

### Post by zXen on 2006-03-06
I formatted my C: (data drive), now it only thinks i have 1 XP (Like it should). I also converted it to FAT32.
I made 20GB of unallocated space through Partition Manager and used that to make the Swap(512mb) and root(remaining GB's) partitions.
Now when I try booting from Ubuntu it just says "j" and doesn't do anything. When I boot from my WinXP partition it just goes into XP. Either was doesn't show a GRUB menu

---

### Post by zXen on 2006-03-09
Just for the record I got it working, formatted my main master SATA drive and tried to install, still didnt work. Unplugged the other drive and it installed fine.
 For some reason when I plug in this other drive and try to install Ubuntu it wont work, although i've found a work around, its still something i'd like to get to the bottom of.

---

