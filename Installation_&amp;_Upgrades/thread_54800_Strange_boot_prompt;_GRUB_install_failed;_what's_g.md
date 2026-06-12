---
title: "Strange boot prompt; GRUB install failed; what's going on?!"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Deicidus on 2005-08-06
I am a Linux newbie, first of all.

After downloading the Ubuntu image twice and burning it three times, I made it through the base installation without curruption errors.

But then it failed installing both GRUB and LILO. I told it to skip them and restart, hoping that maybe the boot loader from before would be there. Now I get this prompt when I start the computer with the floppy in (which apparently it install GRUB to even though it said it failed).

"FreeBSD/i386 boot
Default: 0:fd(,a)hda1
boot: "

Anything I type results in "No <what I typed>". What IS this? How can I install GRUB so I can load the OS that finally (apparently) installed correctly?

If I start the computer without the floppy, it loads the "Intel Booot Agent" which does something for a few seconds then says "No boot filename received" and asks for a disk.

So how can I get this thing working? I would really really like some help with this.

---

### Post by edwina on 2005-08-06
Hello. I can't answer your question, I'm afraid, as I'm still learning this stuff myself. A few questions though ...

1) Are you just installing as a dual-boot, or is this a fresh install onto an empty drive?

2) Can you create a Live CD (Knoppix, BeatrIX, Ubuntu) and use that to see whether you have a GRUB/LILO file installed anywhere and, indeed, modify that file?

3) Have you tried just pressing "enter" after the "boot:" prompt (just checking!)

4) Where else, if anywhere, did you try to install GRUB/LILO? Onto the Master Boot Record (MBR), the Linux partition, or anywhere like that? Do you need it to be on a floppy?

Sorry that I can't be more helpful, but the more information you can give us, the better chance somebody has of sorting it out for you  :) 

Ed

---

### Post by Deicidus on 2005-08-06
[QUOTE=edwina]Hello. I can't answer your question, I'm afraid, as I'm still learning this stuff myself. A few questions though ...

1) Are you just installing as a dual-boot, or is this a fresh install onto an empty drive?

2) Can you create a Live CD (Knoppix, BeatrIX, Ubuntu) and use that to see whether you have a GRUB/LILO file installed anywhere and, indeed, modify that file?

3) Have you tried just pressing "enter" after the "boot:" prompt (just checking!)

4) Where else, if anywhere, did you try to install GRUB/LILO? Onto the Master Boot Record (MBR), the Linux partition, or anywhere like that? Do you need it to be on a floppy?

Sorry that I can't be more helpful, but the more information you can give us, the better chance somebody has of sorting it out for you  :) 

Ed[/QUOTE]
 1. A fresh install, although I made an extra blank partition to install Windows on sometime later.
2. OK, I'll start the Live CD download before I go to bed.
3. Yes, it says "No /Kernal". I think that's because the boot loader doesn't know where the OS (?).
4. I tried installing it everywhere, and it failed everywhere. On the MBR, main partition, and the floppy. I only tried the floppy because the others didn't work, so no.

Thanks for your response.

---

### Post by edwina on 2005-08-07
Had any luck?

All I can think of (being a noob myself) is ...

Make sure that you install the Ubuntu OS to mount point "/" and add a boot flag, assuming that you're using the advanced partitioner or whatever it's called (i.e. not the guided partitioner, that does it all for you). The help file on the partitioner might help to explain this.

If you can boot via your Live CD, take a look at your GRUB boot file (I think it's called "boot.lst" or something, and it's in your /boot/grub folder) and report it back here. Let us know if you need help on how to do this.

Is this the first OS you've put on this hard-drive? Is it a SATA drive (in which case, select "enhanced mode" from the BIOS)?

When it fails to install GRUB/LILO, what does it say?

That's the best I can do, I'm afraid. Let us know if you make any progress.

---

### Post by Deicidus on 2005-08-07
It should be in the right place with the boot flag, unless it didn't do what it said it would.

I've booted with a Live CD before, so it should work again as soon as I finish downloading it (in about two hours). When I get it, I think I'll be able to find that boot file.

I've had Windows installed on the drive before. I think it's a SATA drive, but I'm not sure. Virtually all modern computers have SATA drives, right? Mine is a two-year-old Toshiba laptop.

For that last question, I'll have to get back to you next time I reply.

---

### Post by krusbjorn on 2005-08-07
[QUOTE=edwina]If you can boot via your Live CD, take a look at your GRUB boot file (I think it's called "boot.lst" or something, and it's in your /boot/grub folder) and report it back here. Let us know if you need help on how to do this.[/QUOTE]

Hey, i'm also a newbie, but i have been through this before ;) 

When i screwed my boot.lst up, i booted from a live cd and got it fixed. However, if you boot form the live CD and just go to /boot/grub/menu.lst, you will be "editing" the CD, which will not work. To edit your actual menu.lst file, you need to mount your HD. I did this by creating a mountpoint in my home folder, and doing "sudo mount /dev/sda1 /home/lyle/mount/" (sda if you have a sata drive, hda if you have an ordinary IDE). Then navigating to /home/lyle/mount/boot/grub/menu.lst.

However, on your description it doesnt really sound as it is your menu.lst that is messy. Sounds more like a bad CD or that you did something wrong during the installation.

Good luck!

---

### Post by aveline on 2005-08-07
[QUOTE=krusbjorn]Hey, i'm also a newbie, but i have been through this before ;) 

When i screwed my boot.lst up, i booted from a live cd and got it fixed. However, if you boot form the live CD and just go to /boot/grub/menu.lst, you will be "editing" the CD, which will not work. To edit your actual menu.lst file, you need to mount your HD. I did this by creating a mountpoint in my home folder, and doing "sudo mount /dev/sda1 /home/lyle/mount/" (sda if you have a sata drive, hda if you have an ordinary IDE). Then navigating to /home/lyle/mount/boot/grub/menu.lst.

However, on your description it doesnt really sound as it is your menu.lst that is messy. Sounds more like a bad CD or that you did something wrong during the installation.

Good luck![/QUOTE]
 Laptops, afaik, do not have SATA drives.  Just an fyi.

if you're going to want windows on the hdd, install it first.  Windows likes taking over the mbr which sucks.  Leave a space for ubuntu (don't create apartition using the windows partioning tool, just leave a blank space) then install ubuntu.  This ofc assumes you practice enough to get ubuntu to work.  

When installing ubuntu, you can let it partition stuff for you (but it will take over the whole hard drive a la windows btw) or do it manually.  I do it manually & make a / (root), swap & /home partition and when I install windows I adda FAT32 partition to xfer files from windows to ubuntu.  I have yet to get ubuntu to work on this comp tho b/c my drive is sata. bleh... anyway... hth

aveline

---

### Post by Deicidus on 2005-08-13
[QUOTE=krusbjorn]Hey, i'm also a newbie, but i have been through this before ;) 

When i screwed my boot.lst up, i booted from a live cd and got it fixed. However, if you boot form the live CD and just go to /boot/grub/menu.lst, you will be "editing" the CD, which will not work. To edit your actual menu.lst file, you need to mount your HD. I did this by creating a mountpoint in my home folder, and doing "sudo mount /dev/sda1 /home/lyle/mount/" (sda if you have a sata drive, hda if you have an ordinary IDE). Then navigating to /home/lyle/mount/boot/grub/menu.lst.

However, on your description it doesnt really sound as it is your menu.lst that is messy. Sounds more like a bad CD or that you did something wrong during the installation.

Good luck![/QUOTE]
 Ok, I did all that, and there is no menu.lst file in that location. Unless it's hidden or something, but I think in Linux hidden files start with a dot.

Since the install failed by saying it couldn't install GRUB, is there a way I can just say "install GRUB to this mounted drive" and it will magically work and be happy?

---

### Post by krusbjorn on 2005-08-13
[QUOTE=Deicidus]Ok, I did all that, and there is no menu.lst file in that location. Unless it's hidden or something, but I think in Linux hidden files start with a dot.

Since the install failed by saying it couldn't install GRUB, is there a way I can just say "install GRUB to this mounted drive" and it will magically work and be happy?[/QUOTE]

If I were you, I would download the image again, make sure it is not corrupted by looking at the md5 sum, burn it in a VERY slow speed. I didnt get a working CD until I burned at 4x speed. Crappy CD-burner I guess.

If it still doesnt work, I hope someone else can help you.

Good luck!

---

### Post by Deicidus on 2005-08-13
Aah! Not again! I've already downloaded it twice. I download big files all the time; why is this one so fragile? But ok.

As for the md5 sum, how do I check it? I'm downloading it on a mac, which I think checks md5 sums automatically when you open a disk image. I tried to figure out OS X's built-in md5 sum checker, but I couldn't understand all of the jargon.

I'm about to give up on this thing. I decided to try to get a Linux disto running (again) because I heard Ubuntu was so simple for new users, and because Windows erased all of my mlDonkey settings randomly. But I'd rather have my system running like crap than not at all.

---

### Post by aveline on 2005-08-13
[QUOTE=Deicidus]Aah! Not again! I've already downloaded it twice. I download big files all the time; why is this one so fragile? But ok.

As for the md5 sum, how do I check it? I'm downloading it on a mac, which I think checks md5 sums automatically when you open a disk image. I tried to figure out OS X's built-in md5 sum checker, but I couldn't understand all of the jargon.

I'm about to give up on this thing. I decided to try to get a Linux disto running (again) because I heard Ubuntu was so simple for new users, and because Windows erased all of my mlDonkey settings randomly. But I'd rather have my system running like crap than not at all.[/QUOTE]
 if you have access to a windows comp, use MD5Summer to verify the sum files...thats what i use and it works fine.

I doubt your d/l is corrupt, and to save on cd's i use cdrw's, that way if the burns bad, I erase & redo it plus it burns @ 4x which is almost guaranteed to work on any cd drive.

You don't have a SATA drive I'm sure of that much if this is a laptop.  However laptops often don't like "acpi" or powermanagement controls on linux, so in the bios turn off powermanagement for now.  When you get the "Boot:" prompt after booting the cd, type this in and see if it works:

linux expert pci=noacpi noapic nolacpi noapm 

aveline

---

### Post by Deicidus on 2005-08-22
Ok, I'm done with Ubuntu. I have now downloaded the install image three times, the live image twice, and wrote at least seven disks total. This is ridiculous--the last disk I wrote STILL has an install error, and at a different place! I wrote it at 8x, the slowest my computer will go. This is the only time I've ever had problems with cd-writing, so it is NOT my computer. Unless someone has something blisteringly solutive to say, I'm going to go find a working distro for my download server.

---

### Post by agiledata on 2005-08-22
I've had the same problem with corrupt CD burning. My Hoary (5.10) system was made by installing Warty (4.10) before Hoary came out, and then upgrading it on-line. I've yet to burn a good CD for another PC I'm trying to install it on. However, it works OK on other PCs. 

Strange problem, but worth persevering with a little longer... Ubuntu is really good for me, trying to escape from Windows.

---

### Post by Deicidus on 2005-08-22
[QUOTE=agiledata]I've had the same problem with corrupt CD burning. My Hoary (5.10) system was made by installing Warty (4.10) before Hoary came out, and then upgrading it on-line. I've yet to burn a good CD for another PC I'm trying to install it on. However, it works OK on other PCs. 

Strange problem, but worth persevering with a little longer... Ubuntu is really good for me, trying to escape from Windows.[/QUOTE]
 I want to stop using Windows because of all the time and trouble it takes. Ubuntu is doing the same thing to me. Besides, I'm not going to be using it; it's just to run my mlDonkey server on.

---

