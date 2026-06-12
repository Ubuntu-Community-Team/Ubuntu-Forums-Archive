---
title: "Confused by Feisty Install"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Goldspeaker on 2007-05-19
Hi all.

I'm new to Ubuntu and am having trouble understanding how the install works. I have an external 160gb hard drive that I would like to put Ubuntu on. I am already using the drive with Windows and it has about 10gb already on it. I wish to divide it up to give Ubuntu somewhere in the region of 40gb on the drive but am not sure what is the best/easiest method. I have looked at the Wiki but the information at GraphicalInstall is incorrect for Feisty (I think). I know I could use GParted but is it better to use Install? I would just like to be lead step by step through the install. Thanks in advance.

---

### Post by Ub1476 on 2007-05-19
If you gonna dual-boot here's a good guide: [Linky]("http://www.apcstart.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") 
It's for Vista+Ubuntu, so just drop the first part and scroll down to where you install Ubuntu. If you are using XP, i'm not sure of any good programs to divide your hard drive, except for Partition Magic, but it's not free.. If you have Vista installed there's a built in program there, which you can find by just searching at "computer". I think it's called computer managment or something..

---

### Post by Goldspeaker on 2007-05-19
Sorry should probably explain better. I intend to install to the external hard drive and then just plug it in when I want to use Ubuntu. I won't be installing on the same drive as Windows. I just want to know how to partition the external hard drive, without deleting the stuff already on it.

Sorry if there was any confusion.

---

### Post by Goldspeaker on 2007-05-20
^BUMP^

As I've had no response I thought I'd repeat myself.

I have an external hard drive that I want to put Ubuntu on.
It already has some files on it that I want to keep.
How do I use the grahical installer to install Ubuntu on the drive?

Please?

---

### Post by Peter09 on 2007-05-20
> **Goldspeaker said:**
> ^BUMP^

As I've had no response I thought I'd repeat myself.

I have an external hard drive that I want to put Ubuntu on.
It already has some files on it that I want to keep.
How do I use the grahical installer to install Ubuntu on the drive?

Please?

Does the installer give you the option of your pluggable drive as an install target?

---

### Post by Goldspeaker on 2007-05-20
Yes but I'm not sure which  options to go with. I definitely don't want to erase the entire disk.

---

### Post by misfitpierce on 2007-05-20
Click Custom partition and resize and make a partition for EXT3 for however big you want(EX:40 gig) then make 1 more partition anywhere from 600 MB -1.2 GIG for SWAP. Swap is a good thing to have but it does not need to be huge.

---

### Post by Goldspeaker on 2007-05-20
Can I do that in GParted instead?

---

