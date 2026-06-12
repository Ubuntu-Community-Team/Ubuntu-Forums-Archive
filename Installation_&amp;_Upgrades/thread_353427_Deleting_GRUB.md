---
title: "Deleting GRUB"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by J0G on 2007-02-04
Hey there

I see the other big error 17 thread down below, but i feel that my issue, and what I'm trying to get accomplished run along different lines.
So to make this easy let me layout my situation

**_WHAT I HAD:_**
1x 100 GB NTFS partition (D:\)
1x 20 GB NTFS partition (with XP on it) (C:\)
1x 20 GB NTFS partition (G:\)
1x 40 GB EXT3 partition (with kubuntu on it)

**_WHAT I DID:_**
Using partition magic 8, I added the 40GB EXT3 partition to the 20GB G:\ partition.
This effectively erased my Linux partition, and turned all those 40GBs of linux into blank NTFS space.

**_WHAT I'M LEFT WITH:_** 
Now when I turn on my machine I get GRUB 1.5 error 17 message.

I want to totally get rid of GRUB and have my machine load into windows (on the c:\ drive)
everytime I turn on my computer.

For those who are wondering why I am ditching ubuntu it is simply because 1.) Game support is way to lacking, even with windows emulation programs. 2.) My Logitech G7 mouse controls dont work with it. 3.) The mouse pointer is laggy as hell (I dont blame this on ubuntu, but on my mouse incompatibility issue).

---

### Post by bulldog on 2007-02-04
Put in your windows install cd and boot into recovery console.
Type fixmbr and your grub is gone.

---

### Post by dcstar on 2007-02-04
> **bulldog said:**
> Put in your windows install cd and boot into recovery console.
Type fixmbr and your grub is gone.

And if you don't have access to the CD, there is a freeware "mrbfix" DOS utility that you can download to do essentially the same thing.

---

### Post by J0G on 2007-02-05
I am currently on a kubuntu live CD and Im wondering if their is anyway to fix the mbr from here.

I dont care what i have to do, i just need to be able to load my windows partition again.

I dont have an XP cd, and sadly cannot find any floppy disks :(


Is it possible to resintall grub juts so i can get back into windows and fix the issue from their?

---

### Post by Herman on 2007-02-05
Hello J0G,
You should try [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), that can do lots of things for you, including booting Windows, and also re-installing Windows bootloader too if you like.

Regards, Herman :)

---

