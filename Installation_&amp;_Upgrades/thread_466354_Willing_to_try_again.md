---
title: "Willing to try again"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Mechaphoenix25 on 2007-06-06
I have a story and a couple of questions about the new Ubuntu release.

I tried to install the new Ubuntu (7.04 feisty fawn) on my external HD.  While the installation appeared to go fine, it also (unbeknownst to me) put a bootloader on my main HD.  It was the Grub one, and it errored out whenever I tried to boot from my main HD (windows vista).  I had to reformat the entire drive and restore all my stuff from a backup.  It took me 3 days  because I like my system to be well configured and most of the backups are on CD's.  Not only that, but Ubuntu STILL didn't work when I tried to boot off my external.  

My whole objective here is rather different than a normal install.  I do a lot of consulting and computer upgrading/fixing/troubleshooting around my college.  I want to be able to have an external HD that I can just plug into any computer and have boot straight into Ubuntu, because it's free and a great OS.  Using the live CD just takes WAY too freaking long to load, and it's severely limited by the amount of ram present (in most cases not a lot, the computers that tend to need fixing are the old ones).  First off, is this a viable thing to do?  Does Ubuntu NEED to have a bootloader on the main HD of the computer it is running on for it to work in its full capacity?  Can't I just boot it from BIOS?  Will it be any faster or better than a live CD?  Am I a total idiot for trying this?

I do have a possible solution:
I talked to a friend recently about the problem and she said that it was because I had downloaded the new version right as it came out (may 31, the night of, actually) and there was a now  known problem with the bootloader.  I am downloading the same version now, from the main site, and am willing to try again.  This time I'm going to remove my main HD and just install it on the external.  Will this work?  Do I have to worry about it screwing up my computer again?  

Sorry if there's so many questions, I know a lot about computers but next to nothing about Ubuntu.  :p

---

### Post by mlind on 2007-06-06
why did you format your drive? You could have used the windows repair console and just rewrite the boot sector. All of your data was still there.

I haven't got a external hdd, but I'm quite sure you can install a grub into that device too. You can choose the bootable device from bios/boot menu, and make it your external hdd. If Ubuntu installer doesn't offer you the choice of installing grub into other device, don't install grub at all and then do it manually after base system has been installed. You can use ubuntu cd to boot into installed system and install grub afterwards.

If your windows partitions are in a separate hdd, just disable that drive from bios before installing Ubuntu.

---

### Post by Mechaphoenix25 on 2007-06-06
Wow, amazingly fast response, you guys are good!

I tried doing a repair of the boot section, twice.  It failed both times.  Sometimes there's nothing you can do I guess.

Thanks for the info, I'll just unplug the HD (easier than messing around with disabling it) and install Ubuntu.  I'm glad to see that the tech world has not lost its edge in helping its own.  :)

---

### Post by mlind on 2007-06-06
> **Mechaphoenix25 said:**
> Wow, amazingly fast response, you guys are good!

I tried doing a repair of the boot section, twice.  It failed both times.  Sometimes there's nothing you can do I guess.

Thanks for the info, I'll just unplug the HD (easier than messing around with disabling it) and install Ubuntu.  I'm glad to see that the tech world has not lost its edge in helping its own.  :)

I recall fixing my broken boot sector using FIXMBR command which is available in windows xp's recovery console. Another way is to download a bootable cd image or floppy from bootdisk.com, boot using it and execute: *fdisk /mbr*. I'm not sure about vista though, it could be doing its own thing.

btw. if you unplug your windows drive, you're safe, but grub cannot automatically detect your windows partition and add it as an entry in the boot list. That's fine, because you can add it later, but you'll need to do some manual editing. These forums should contain the info how to do that though.

---

### Post by floke on 2007-06-06
I set this up a few days ago. Here are the steps I took.

(1) Partition the external HD. I used the Feisty LiveCD (retrospect wish I had used the Edgy liveCD since I think the partitioner's better) to shrink the FAT32, to create primary ext3 partition, and an extended partition into which I put a swap partition. The partitioner gave me a few issues since it kept mounting the drive in the middle of the partitioning - so the partitions appeared in GParted as being locked. I had to keep manually unmounting (right click and eject) the drive/partitions to continue. Anyway, got there in the end, but with an error - the ext3 partition was apparently 20% full(!). Not to worry, the next few steps sorted it out.

Before continuing to steps 2+ open a terminal with your external drive plugged in, and type 'sudo fdisk -l' - this will tell you how many partitions etc. you have. You'll need the label (should be sdb or something) for the grub bit - I'll assume below that it's sdb (partitions labelled sdb1, sdb2 etc.)

(2) Used the ALTERNATIVE installer - I read it gives more configuring options on where to put grub etc. And selected the partitions to install Feisty. This part very simple.

(3) When asked where to put grub - manually enter /dev/sdb (as above) - NOT /dev/sdb1, sdb2 etc. - just /dev/sdb. This will (read 'should') put grub on the mbr of your external drive and not your internal one.

(4) Reboot - select boot from usb at startup - you may need to alter your bios settings (actually should make sure you can boot from usb first else all this is pointeless!) - and the grub list on your external drive will appear...

(5) I had a grub error on startup, since grub was pointing to (hd1,1) - which makes sense since Feisty was on partition 2 of the Ext.HD. However, for some weird reason I had to manually edit the grub file (see below) to point it at (hd1,0) - and it worked fine. The Ext. HD grub will also have the partitions from your internal HD on as well - so you might want to comment them out (add a '#' in front of their entries).

(6) Edit menu.lst (you might not need to do this). Reload liveCD. create folder on desktop called 'here'. From terminal 'sudo mount /dev/sdb2 /home/ubuntu/Desktop/here') [sdb2 being the partition in which the system files were stored]. Then 'sudo nano /home/ubuntu/Desktop/here/boot/grub/menu.lst' (phew!) and change the entries accordingly.

(7) Reboot and enjoy. Works peachy!

Hope this helps.

---

### Post by Mechaphoenix25 on 2007-06-06
ok, I just tried removing my main HD, and installing it on my external.  I used the whole thing, because I've got my backups on a different one and I want as much room to play around in as I can.  I also left the default bootloader location at (HD0) (I think that's what it said).  The installation went beautifully, but when I tried to boot from the external, it said "Operating system not found."  I'm guessing this is due to the lack of a proper bootloader installation, but I'm not sure.  Is there some way I can get it to work, this is what happened the last time.  My main HD is fine, but I'm not risking having it plugged in at the same time as the external.  Thanks!

---

### Post by floke on 2007-06-06
What grub error is it (number 17 by any chance?)
You'll need to edit your menu.lst file as I said earlier - it's most likely pointing in the wrong place. If you post it here we can have a shot at it.

---

### Post by Mechaphoenix25 on 2007-06-06
There is no grub error.  There is nothing about grub at all.  I select the external HD from BIOS, and it goes to a black screen with just the words 

OPERATING SYSTEM NOT FOUND

in the DOS font.  Any button just makes it print them again.  The only thing I can do is power off the system.  I'll try posting a copy of the menu.lst file, but my network card doesn't have Ubuntu drivers, so it might be a while.  Also, before I do that, where in the file system is menu.lst? or where is the search function in ubuntu?  Thanks for the help, sorry it's not easier to solve.

---

### Post by floke on 2007-06-06
Sounds strange.
It's in /boot/grub/menu.lst

Very late here now so will be back later in the morning.

---

### Post by mlind on 2007-06-07
Boot using the Ubuntu install cd and select to boot in to existing system. When you reach the GUI, open a terminal window and type
```

sudo fdisk -l

```
From the output, find the device which is your external hdd. You need to find the device, not a partition (partition's end with numbers). The device will probably be /dev/sda.
Also find your root partition (probably /dev/sda1)

Chroot in to your root partition and install grub Install the grub
```

sudo mount /dev/xxxy /mnt
sudo mount -t proc proc /mnt/proc
sudo chroot /mnt

#now logged as root in your installed system
grub-install /dev/xxx

```
The first /dev/xxxy must be your root partition. The second /dev/xxx must be your external hdd (not a partition!).

I hope this helps.

---

### Post by Mechaphoenix25 on 2007-06-07
ok, I tried to boot into the existing system from the linux CD and it doesn't work.  However, I managed to get a copy of my menu.lst.  It's attached, although I'm gonna try some fixes myself to see if I can get it going.  

I have a question: is there a way to set GRUB to boot to the first partition of whatever disk the GRUB itself happens to be on?  If I just set it to HD1 (as I'm going to try doing) it'll try to boot from the second HD, but that wouldn't work on a PC with 2 HDs.  Some of my clients have those, so this would make it much easier for me.

I know the menu.lst isn't attached, my wireless card doens't have linux drivers.  I'm exporting it to a text file now, which I'll send from another comp.

---

### Post by floke on 2007-06-07
With your ext HD plugged in, can you post the outputs of
sudo fdisk -l
and your menu.lst file - it was not attached :)

---

### Post by Mechaphoenix25 on 2007-06-07
ok, here's the menu.lst, I saved it as a TXT so it would upload (my other comp only runs linux).  Open it in TextEdit, it should view, although I can't say for certain.

---

### Post by floke on 2007-06-07
For other readers, this is the relevant entry:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d8e363cc-5231-4b4f-87ec-6cee1179ad73 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

But without the output of sudo fdisk -l with your external drive plugged in its rather meaningless - basically we need to point this to your ext. hdd - whatever fdisk records it as should be right (I think!)

---

### Post by mlind on 2007-06-07
I'd like to know if you get the grub menu when your computer boots. Otherwise it's pointless to fix the boot menu if the actual loader is not in the MBR.

Could you elaborate what exactly didn't work with the chrooting instructions?

---

### Post by homunq on 2007-06-07
If I understand, you want a portable install on an external disk, to use as a "toolkit" for fixing / messing with old computers. Two things - there are probably better distros than Ubuntu for "toolkit" purposes. Especially if you want to do things like recover windows passwords, fix disks when their partition table gets hosed, scan for windows viruses from linux... (Given that you formatted your windows disk after Ubuntu touched it, you would do well to check out the good tools that exist for this kind of thing, generally you can recover from much worse.) Second, older computers won't let you boot from the BIOS into an external drive. So you'll need a floppy or cd with a bootloader that sends you to the external drive (a grub menu with several options to cover the different places your drive might end up in the BIOS). It reduces the simple portability, but you still get the speed and read/write advantages over just a CD.

---

### Post by Mechaphoenix25 on 2007-06-07
Well, my external just encountered disk error while trying to install Ubuntu as per your instructions.  It seems the HD (which I had salvaged from a now 7 year old IBM) finally gave up the goat.  I'm gonna say forget it and just use the live CD, which I guess is sufficient for my purposes.  Thanks anyway for all your help,  I'm sure we would have gotten it working eventually.  Athough, my college that I will be attending in the fall has Linux on all their computers, so I'll soon be able to play around with the OS in a much less- tentative I guess- environment.  Happy trails all.

---

