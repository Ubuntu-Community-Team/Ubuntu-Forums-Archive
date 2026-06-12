---
title: "Reboot Loop With Gutsy Gibbon Intel DG965RY"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by chaos51 on 2008-03-04
I am having some trouble installing Gutsy Gibbon.  I don't have any problem with getting the installation CD to run (like some other threads).  The installation process actually goes fairly smooth.  The problem is that on reboot, I never get to the grub boot loader (I just see a _ in the top left corner of the screen and E7 at the bottom right).  This stays there for a few seconds and then reboots....repeat.

What I've tried.
Installation with 7.10 desktop i386, 7.10 desktop  amd64, and their server variants.

I tried booting from the live Install CD and trying the Boot from first hard disk option, that just flashes Grub stage 1.5 really quick and reboots.

I tried modifying some BIOS settings (changing SATA to legacy mode, disabling USB devices, Serial ports, disabling all on-board devices (except Ethernet).

Tried installation and then a rescue to try and re-install grub.  Checked the device.map for correctness. reads (hd0)  /dev/sda

Fedora 8 installs without any problem. (This was done to test the hardware)
I was trying to set this up as a dual boot but put in a new 80Gb Hard drive to just test to get some version of ubuntu installed

What I'm trying next:
various option changes to grub, setting groot and maybe using the device names for root instead of UUID.

I'm currently downloading 8.04 Alpha 5 to try that but I'd prefer to have a stable release as I'm setting up a lab environment.

(I've attached lshw and lspci output for more detailed hardware list)
Intel DG965RY Motherboard
Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
2GB ram
GeForce 8400 GS

Does anyone have any ideas what else I can try?  Anyone else run into this problem?

This is my first post so if I've done something improper please let me know.

thanks,

---

### Post by vyvee on 2008-03-04
Oops! I encounter exactly the same problem as yours! I spent last 3 nights debugging it and finally found a workaround.

[SIZE="4"]**Problem**[/SIZE]

My system:
[LIST]
[*]Intel DG965RY Motherboard
[*]Intel(R) Core(TM)2 CPU 6400 @ 2.13GHz
[*]1GB ram
[/LIST]

Symptoms:
[LIST]
[*]Ubuntu was installed smoothly. Reboot, then Grub shows up to stage 1.5 for less than 1 second and reboot again.
[*]Windows XP was installed smoothly (just for testing). Reboot, everything just works fine!
[*]Tested on another harddisk with the above. Same symptoms.
[/LIST]

Further 'shocking' discoveries!
[LIST]
[*]After installing Ubuntu, reboot to a rescue CD and found that, except the first 0x1C00 bytes, the first 256MB+ bytes (and about the first 224MB for another harddisk) were wiped out to zeroes! So the filesystem of the first partition will be corrupted after Ubuntu installation!
[*]Even if we avoid the first 256MB of the harddisk, Grub still does not able to show the menu & boot the computer.
[/LIST]

[SIZE="4"]**Workaround**[/SIZE]
Two things need to be done:
[LIST]
[*]Sacrifice / Waste the first 256MB (or to be safe, use 1GB) of the harddisk. I created a dummy first partition to defend against the 'zero-ing' process. Install Ubuntu from 2nd partition onwards.
[*]Use Extlinux instead of Grub as the bootloader. Since Extlinux is not included in the Ubuntu Live CD, you have to find other way. Please refer to [this guide]("http://www.vyvy.org/main/node/167") I wrote (motivated by solving this problem) on using Extlinux instead of Grub for Ubuntu. I haven't tried other bootloaders like LILO yet.
[/LIST]

Hope it helps! The workaround works on avoiding the problem instead of solving it, as I don't know the real cause yet. If you know the cause & a better solution, please enlighten us!

---

### Post by zvacet on 2008-03-05
Maybe [this](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5) can put some light on your problem.

---

### Post by vyvee on 2008-03-05
Hi Zvacet, thanks for your suggestion. However, the problem we encounter looks much nastier than simply the problem of Grub configuration. Ubuntu installation is supposed to set up Grub properly.
In fact, the Grub configuration works & the computer boots with no problem with another motherboard. But once I change it to use this board, it enters the reboot loop. Furthermore, I have encountered this for two different harddisks which work for two other different motherboard.
As I checked further, it seems that the problem is probably (just a wild guess) related to the Marvell PATA chipset which was not supported by Linux earlier. What I find out is:
[LIST]
[*]Ubuntu 6.10: PATA did NOT work.
[*]Ubuntu 7.04: It works!
[*]Ubuntu 7.10: The nasty problem I encounter here... the harddisk is connected to PATA, that's why I have such a wild guess. How about the experience of others who use this Intel DG965RY board + Ubuntu 7.10 + PATA harddisk to boot?
[/LIST]

---

### Post by chaos51 on 2008-03-05
In my situation I am using SATA Hard drives, the only PATA device is the DVD RW drive.

8.04 Alpha 5 did install and boot properly.

Other information:
   After the installation of 7.10 and trying to use a rescue disk or just boot into the ubuntu live CD again, I tried mounting the file system to see if I could make some changes to the menu.lst file.  When I tried to do the mount: mount /dev/sda1 /mnt/foo  it said I must specify the filesystem (I thought this strange since it should have recognized it as ext3)  so I went on to try: mount -t ext3 /dev/sda1 /mnt/foo and I got invalid block device.  fdisk did show that it was partitioned ext3.

Going to try a few more tricks.

---

### Post by vyvee on 2008-03-05
> 
After the installation of 7.10 and trying to use a rescue disk or just boot into the ubuntu live CD again, I tried mounting the file system to see if I could make some changes to the menu.lst file. When I tried to do the mount: mount /dev/sda1 /mnt/foo it said I must specify the filesystem (I thought this strange since it should have recognized it as ext3) so I went on to try: mount -t ext3 /dev/sda1 /mnt/foo and I got invalid block device. fdisk did show that it was partitioned ext3.


That's exactly what I have encountered too! Refer to my Post #2... and that motivated me to do further diagnosis & I found that it's due to that the first 200MB+ of /dev/sda1 was zero-ed. The type of the filesystem is still ext3, yes, as it is recorded in the first 512 bytes that are not zero-ed. But the filesystem structure in /dev/sda1 has been destroyed by the 200MB+ zero-ing.

By the way, I used dd and hexdump to read the content of /dev/sda in byte format.

---

### Post by chaos51 on 2008-03-05
vyvee,
   Thanks for the input,  I initially did not notice the zeroing of the first portion of the disk because my first attempt was on a system whose first partition was a windows NTFS partition and I had ubuntu resize and install after it.  At that first time I was able to mount the Ubuntu install but it still was in that reboot loop.  When I ran into the reboot loop I then decided to try fedora and then  tried on another disk.
   I'm still looking into it, I tried 7.04 but when I boot from the CD m the PC speaker just keeps beeping while the Live CD is booting.  I couldn't let it go on like that  (it annoys our helpdesk personnel).  
   I think I might try installing fedora and use that installed grub and see if I can then install Ubuntu without installing ubuntu's grub.  Maybe if I can get the system up that way.  
   Is there a was to update the packages for the installed system during the install process?  I thought I saw this at one point but it failed because I am behind a proxy.
  thanks

---

### Post by chaos51 on 2008-04-16
Just an update,
  I did eventually get my systems installed.  I installed 7.10 ( with the server install I think ) and basically made it not install the boot loader at all.
   I then used my Hardy disk as a rescue and installed grub from hardy. This worked fine.  Once I got one machine setup I just used ghost to to a drive to drive copy to my other workstations and some I had still fix with the hardy disk and re-install grub but for now I've got 12 workstations up and going.
thanks for all the input.

---

### Post by Rohan Kapoor on 2008-04-19
Chaos51 please explain in detail how to fix it. I have a full 7.10 Server installed but not booting. Thanks

---

### Post by Rohan Kapoor on 2008-04-19
> **darth-vader said:**
> Chaos51 please explain in detail how to fix it. I have a full 7.10 Server installed but not booting. Thanks

Still can't fix it. Please give me more info chaos51

---

### Post by chaos51 on 2008-04-19
After installing 7.10, boot into the hardy live cd.
Open a root terminal window ( start a terminal and sudo su - )
mount your existing 7.10 partitions if they don't get automatically mounted.  I do it manually so I know exactly what I'm mounting and where.
If you don't know if you have a sda or hda or don't know which partition has what you might find disk info by doing:
fdisk -l
from that you can mount one partition at a time and find the one that contains the root partition.


So assuming that you have 7.10 installed on sda.
I usually do something like the following assuming /dev/sda1 = /boot and /dev/sda2 = /
#create a mount point for the root partition
1. mkdir /mnt/target
2. mount /dev/sda2 /mnt/target
#now if you have separate partitions for boot or usr or which ever you may have to mount those as well but I'm not for sure.  I think all you really need is the boot partition
# I'm assuming that the boot partition is a separate partition so I would mount it like this:
3. mount /dev/sda1 /mnt/target/boot
#now what we need to do is install grub into the master boot record using the grub-install from hardy but using the grub configuration and destination boot partition of the 7.10 install, which would be something like:
4. grub-install --root-directory=/mnt/target/ /dev/sda
5. reboot and hopefully 7.10 will boot

If you have the default install method which I believe puts boot and / on the same partition you'll only have to mount the root partition so assuming:
/dev/sda1 = /
(assumes you are booted into hardy live cd and in a root terminal window )
you'd just have to 
1. mkdir /mnt/target
2. mount /dev/sda1 /mnt/target
3. grub-install --root-directory=/mnt/target/ /dev/sda
4. reboot and hopefully 7.10 will boot

I'm typing this from memory so you might have to man grub-install if the above doesn't go smooth.

Let me know if you have any trouble with this and I will try to be more verbose as to what I did.

---

### Post by chaos51 on 2008-04-19
I should have mentioned that my previous post assumes that your first 200+MB of your 7.10 install didn't get wiped out buy the 7.10 boot loader install as vyvee pointed out.

I can't remember exactly how I got around that during the install but one of the last step in the 7.10 install asked if I wanted to install the boot loader and I said no or somehow canceled out before the boot loader zero'd out the first bit of the disk.  Alternatively I suppose you could create a dummy first partition that is maybe 300MB and install the boot loader (which would presumably zero out the first partition or some portion of it).     I think you will still have to use the hardy method in my previous to install a working grub .  You could then reformat that initial partition once you have a working install and use it as additional swap or something.
   I'm kind of speculating here about the zeroing out but I'm pretty sure that the 7.10 boot loader install will zero out the beginning of the disk as vyvee pointed out.  So the dummy partition method may or may not work.  The reason that I think that it would work is that in my initial install I had a Windows XP install on the first parition, when I booted into hardy my 7.10 install was fine but when I tried to boot into Windows I found that the file system was corrupt because the beginning of the disk with my Windows NTFS partition on it was zero'd out.

That's my $0.02

---

### Post by Rohan Kapoor on 2008-04-19
Ok, I'll try and let you know.

---

### Post by Rohan Kapoor on 2008-04-20
> **chaos51 said:**
> I should have mentioned that my previous post assumes that your first 200+MB of your 7.10 install didn't get wiped out buy the 7.10 boot loader install as vyvee pointed out.

I can't remember exactly how I got around that during the install but one of the last step in the 7.10 install asked if I wanted to install the boot loader and I said no or somehow canceled out before the boot loader zero'd out the first bit of the disk. 

Could you please explain exactly how you did that?

---

### Post by vyvee on 2008-04-28
Hi all,
I just installed Xubuntu 8.04 on my troublesome Intel DG965RY, sticking everything to default (i.e., using Grub, etc...). I'm happy to report that it works perfectly without reboot loop or disk wipe out problem. :)
:popcorn:

---

