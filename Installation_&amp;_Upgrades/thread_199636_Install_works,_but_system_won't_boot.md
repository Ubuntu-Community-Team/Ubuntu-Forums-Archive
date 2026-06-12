---
title: "Install works, but system won't boot?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by entropism on 2006-06-19
OK, maybe you guys can help me out here:  I'm a total noob when it comes to Linux, but I wanted to try things out and see if I could get used to a new OS.  

I installed Kubuntu on my system, things seemed to go OK, but when the install finished, I got an MBR error at boot.  I went inot the windows recovery CD, tried fixboot, fixmbr, the whole 9 yards, and eventually I had to completely reformat.

Now, before I try this again, maybe I could get some assistance.

I currently have 3 hard drives in my computer, a 400GB, a 200GB, and a 300GB, all SATA.  I normally have the 400GB split, where 75GB goes to windows, and the rest goes to an extended partition.  The 200GB and 300GB are single partitions.

What I WANTED to do was have the 400GB set up where I'd have 75GB for windows, then the linux /, home and swap, (figure what, 75GB total?), and the rest of the drive NTFS storage, with my 200GB reformatted as a shared, FAT32 storage drive.  Is this what's giving me my errors?  Too many partitions on one drive perhaps?  Heck, would it be possible to install linux on the 200GB drive and have windows on my 400GB drive?

Is there an EASY way to set this up?  I tried this 3 times, and each time I had to reformat the entire 400gb drive and reinstall windows.  Any advice?

---

### Post by th3james on 2006-06-19
Did you get the same problem everytime? It sound like it can't install grub (the bootloader). That partioning scheme sounds fine, how are you partitioning it? I always do it using gparted in the ubuntu livecd

---

### Post by ajgreeny on 2006-06-19
If I remember rightly, fat32 drives shouldn't be more than about 32 Gb, or something like that.  Other than that I see no problems with what you are trying to achieve.  I'm also surprised that the fixmbr command in windows caused problems, unless it was the fixboot, which I've never used.  I have used the fixmbr many times without any hint of a problem, in spite of the warnings given by the recovery system when you do it.

---

### Post by th3james on 2006-06-19
Ive got an exteral hard drive which is fat32, and 230Gb. However, i don't think you can have a file over 4.5Gb or something.

You need to get the grub bootloader install, 'cause the windows one won't detect or boot linux

---

### Post by entropism on 2006-06-19
Well, I'm not too familiar with the whole mounting/partitioning when it comes to Linux, so I TRIED, but most likely did something wrong.  ;)

The first time I tried, I had the CD partition for me in a 75GB partition.  The other times I put 1Gb for swap, and I THINK 20GB for home and /.

Is there any way to put linux on a completely seperate drive and still have a dual boot system?  I think it'd be a lot easier for me, because lord knows I don't want to reformat AGAIN.  #-o   I figure if I could put windows on my 300GB drive and linux self contained on the 200GB, while having grub handle the boot, I'd be on easy street.

As for grub, I had linux installed for a few weeks last year, a SUSE install, and grub was installed automatically.  When I did the kubuntu install, it never even mentioned grub.  Is it a seperate step, or does it go in automatically?

---

### Post by th3james on 2006-06-19
Yeh, install windows on the drive you want for windows, then install linux in the same way on the other drive, and make that the first boot device. The grub boot loader should install and detect windows on the other drive. If it crashes again, just change the the first boot device in BIOS to the windows drive

---

### Post by th3james on 2006-06-19
Oh, and grub should be the last step in the install process

---

### Post by entropism on 2006-06-19
Alright, thanks , I'll try that tomorrow and report back here.  Kind of off topic but...  As a linux new guy, is there any preference between gnome and KDE?  Not sure how well themes are done for either, but I liked the look and feel of KDE (yeah, I'm a windows guy), and gnome seemed pretty bland and confusing.


Oh, and...  Should I download the standard live CD, the alternate CD, or the DVD?  I have a feeling I don't want to take any chances and I'm going to redownload the image over bittorrent tonight.

---

### Post by th3james on 2006-06-19
Ive just gone back to KDE after using gnome for 6 months, and KDE for 6 before that. Personally, i like them both. I find KDE slightly prettier, and its alot more customisable, but gnome is slightly better laid out in my opinion (less is more). If you install one, you can easily add the other with one command. Try living with both for a little while is my advice

KDE
sudo apt-get install kubuntu-desktop
Gnome
sudo apt-get install ubuntu-desktop

---

### Post by entropism on 2006-06-19
Oh, excellent, excellent.  That's exactly what I hoped to hear.  Is this an overwriting process, or can you switch between the formats?

That being said, is there any difference between Ubuntu and Kubuntu then besides the desktop?  I have a feeling installing Ubuntu and then using apt-get for KDE might be my best bet, but you guys would know a lot better than I.

---

### Post by th3james on 2006-06-19
No, its an adding process, at the login screen, you select your session type (kde or gnome). I would have said starting with ubuntu was a better idea, but that only because im more familiar with the install

---

### Post by ajgreeny on 2006-06-19
I completely agree with th3james.  He suggests exactly what I have done with my system both with dapper and breezy before that, and it all works brilliantly
Good luck.

---

