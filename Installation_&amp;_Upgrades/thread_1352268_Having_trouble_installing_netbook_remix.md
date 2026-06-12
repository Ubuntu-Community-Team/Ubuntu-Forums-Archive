---
title: "Having trouble installing netbook remix"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Furm on 2009-12-11
Hey guys, i'm wondering if you can help me out here.

I recently saw that 9.10 came out and there is a netbook remix (this got me really excited) and for the past couple of days i've been trying to put it on my Eee PC. Now obviously i can't burn a disk to install so i've been trying to format my jumpdrive to install ubuntu.

I've ran into a few problems and am wondering if someone has a remedy to my problem.

I've tried copying the ISO onto the jump drive...nothing, i've used a program on the installation instructions...unetboot i think its called...that didn't work. it poped up with a default sreen like it would install but then when i'd hit enter the 10 second timer would restart...such as if it counted down to 0 as well. I've also tried to write the img to my flashdrive however the img writing program wouldn't recognize the ubuntu 9.10 iso? 

I've changed my boot sequences in bios to start with a removable drive, so the only problem is getting it to start the installation process.

(another key point is i've never actually created a "jumpdrive" so to say) i've always just burned iso's to dvd's to do installation processes.

Thanks for your time guys, I appreciate this

J Furm

---

### Post by bluelamp999 on 2009-12-11
I assume your Jumpdrive is a usb memory stick type of thingy?

If so, have you tried *System>Administration>USB Startup Disk Creator*?

Not sure if it's what you're looking for but it's worth a try...

---

### Post by PaulReaver on 2009-12-11
Jumpdrive? is that just a branded usb stick type thing.

Anyway If you have access to a pc with a disk drive it should be really easy. 

Just boot the live cd on a pc and go to system/administration/usb start up disk creator. 
it should automatically find your usb drive and tell you if it needs formatted. 
you just select your usb stick, format and install.

then pop that in your eee

---

### Post by darkod on 2009-12-11
If you only have your netbook to work with, and windows, use unetbootin. But, get rid of the unetbootin menu and enable the ubuntu main menu. To make sure you get rid of any errors that may have happened, format your stick as FAT32.
Use unetbootin to put the ISO on it. After it's finished ignore the message to reboot, just close unetbootin. Open the stick in windows explorer and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the isolinux folder find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the main ubuntu menu. Before installing you can use the Try Ubuntu option to see it will be working on your netbook.
And just to note, you can also use desktop 32bit for netbook, runs just fine. In fact I prefer the desktop look and installed desktop 32bit over UNR two days later.

---

### Post by Furm on 2009-12-11
Thanks for your help guys, I'll try out those methods tonight and see what happens. I'll let you know what i find :)

Thanks again!

---

### Post by Furm on 2009-12-11
sorry, i also ment to post that the "jumpdrive" i was talking about is just a flash drive....memory stick whatever you want to call it.....it's a centrios 2GB flash drive

i guess i called it jump drive because i was trying to make my computer jump or boot with it? heh  sorry for confusing everybody

---

### Post by Furm on 2009-12-12
Hey Guys i have one more quick question....i'm not at the installation trying to set it up on mypartion.....however it always says the same thing "No foot file system is defined, please correct this from the partitioning menu"    i've tried reformating the partition a couple times....i have it as type NTFS and been trying different mount points....Could any body shed some light on this?

Thanks!

---

### Post by darkod on 2009-12-12
> **Furm said:**
> Hey Guys i have one more quick question....i'm not at the installation trying to set it up on mypartion.....however it always says the same thing "No foot file system is defined, please correct this from the partitioning menu"    i've tried reformating the partition a couple times....i have it as type NTFS and been trying different mount points....Could any body shed some light on this?

Thanks!

You should not create partitions for linux from within windows. Linux doesn't use ntfs. You have two options.
First you have to delete that ntfs partition and leave it as unallocated space.
Then you can either create the partitions yourself manually in the step 4 of the installer, or a better option if this is your first experience with partitioning, select Use Largest Continuous Free space option and ubuntu will set itself up in that unallocated space.

---

### Post by Furm on 2009-12-12
thanks darkod, I ended up formatting it to a ext3...i believe thats what it's called....found it on the fourms and followed some instructions on a guy with a similar problem....I got it installed and working....i'm actually using it right now hehe (awesome!)    Since i've never really used Ubuntu before....just 9.04 when it was first relased for about two weeks, where would be the best place to go about asking general simple questions?

Thanks

---

### Post by bluelamp999 on 2009-12-13
Your first port of call should probably be Psychocat's site - [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) - which has some excellent beginner tutorials and lots of other good stuff...

---

