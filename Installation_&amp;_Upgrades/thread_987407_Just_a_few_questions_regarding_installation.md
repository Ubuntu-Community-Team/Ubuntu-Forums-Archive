---
title: "Just a few questions regarding installation"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by Scarlath on 2008-11-19
Hello there!

I finally recieved my Ubuntu 8.10 CD (and I might add, it only took 17 days for it to arrive!) and I'm now planning to install it when I get the time to do so (damn school), either way, before doing so I have a few questions. Before getting to those however I figure I'll tell you a few things about the current setup.

Okay, so I have two harddrives. One (150~ GB) which Windows XP is installed on and one completely empty (also 150~ GB). I'm planning on using up the entire space on the empty one for Ubuntu.

So here are my questions:

1. How would you advise me to partition the hard drive for Ubuntu, what partitions should I include, and could someone post a how-to (linking to one works too, I haven't had much time googling) describing how to actually do it (seeing as I'm not really familiar with GParted)?

2. Seeing as I'm installing on another harddrive than Windows XP boots from, do I have to do anything with GRUB (during installation process and/or after installation process) in order to make every OS boot as it should or will it fix everything nicely by default, so to speak?

Hmm.. that's all questions I can think of right now. Thanks in advance!

Thank you!

---

### Post by icanfly0307 on 2008-11-19
Hi,
      Partitioning Ubuntu is very easy. My recommendation is that you create your partition layout like this:

               --20 GB / (root partition)
               --130 GB /home (all your document and other stuff)
               -- And of course, Ubuntu will create a swap partition (around 768 MB)

Good to have plenty of space on your HDD :)

And, no, you won't have to make any special changes to GRUB. It will automatically detect Windows XP and allow you to boot into it. Let me know what happens.

Good Luck! :)

---

### Post by aysiu on 2008-11-19
I would (after backing it up, of course), resize the Windows drive and make a new partition on the same drive for Ubuntu. Then I'd format the other 150 GB drive as FAT32 and use that as a shared storage space for both Ubuntu and Windows.

---

### Post by Scarlath on 2008-11-19
> **icanfly0307 said:**
> Hi,
      Partitioning Ubuntu is very easy. My recommendation is that you create your partition layout like this:

               --20 GB / (root partition)
               --130 GB /home (all your document and other stuff)
               -- And of course, Ubuntu will create a swap partition (around 768 MB)

Good to have plenty of space on your HDD :)

And, no, you won't have to make any special changes to GRUB. It will automatically detect Windows XP and allow you to boot into it. Let me know what happens.

Good Luck! :)

Thank you for those answers! :D
I have a RAM of 1024 MB, should I still just use 768 MB of swap?

> **aysiu said:**
> I would (after backing it up, of course), resize the Windows drive and make a new partition on the same drive for Ubuntu. Then I'd format the other 150 GB drive as FAT32 and use that as a shared storage space for both Ubuntu and Windows.

That seems rather complicated, it's a very neat idea though, might look into it.

---

### Post by icanfly0307 on 2008-11-19
Glad to have been able to help. :)

---

### Post by aysiu on 2008-11-19
If you have 1 GB of RAM, you don't really need any swap partition at all, so I'd either not make one or just make it as small as possible.

I don't really see how what I suggested is any more complicated.

[quote=My suggestion]
75 GB Windows / 75 GB Ubuntu
150 GB data for both[/quote] [quote=icanfly0307's suggestion]150 GB Windows
20 GB Ubuntu / 130 GB home partition[/quote] In both cases you have two partitions on one drive and one partition on the other drive.

---

### Post by icanfly0307 on 2008-11-19
Yeah, go ahead with aysiu's idea. Here's a step buy step HOWTO:

1. Back up documents in Windows. (VERY IMPORTANT!!!!)
2. Resize Windows Partition to 75 GB.
3. Run Ubuntu Installer, and create another 75 GB partition on the FIRST Hard Drive.
4. Install Ubuntu onto the new partition you just created.
5. From Ubuntu, format the SECOND Hard Drive as an FAT32 filesystem. 

Now, you can use your second hard drive to share documents between Ubuntu and Windows! So even if you run out of space in Windows, you'll still have space your second Hard Drive.

Good Luck!

---

### Post by aysiu on 2008-11-19
I'm not really saying my idea is the one to go with. Either one would work fine. I just wanted to make sure Scarlath knows they're equally complicated / simple.

There are a lot of different ways to set up a dual boot with two drives, and each way has its own pros and cons.

---

### Post by icanfly0307 on 2008-11-19
Yeah, that's true. However, your idea DOES seem more useful and more effective.

---

### Post by Scarlath on 2008-11-19
Thanks guys, I greatly appreciate your help ^_^

I'll think about how I'll do it for a while, dont have time to install it today anyway so... :p

So.. yet again; thanks! :D

---

### Post by loboc on 2008-11-19
You should have swap regardless of how much ram you have but i can never get a straight answer on how much in terms of ram size, google it and make up your mind yourself. 

If you put ubuntu on its own drive another goot partion to have is /boot where kernel images and ram images go it only needs to be like 128 megs I had to use one to over come a grub 18 error that occurs on huge disks.
 /boot should be the first partition to prevent this error

If you have a huge movie music photo collection that you want to maniplulate play view in both systems i recommend the both OS on one drive and FAT Storage on the other, 

if you are adventurous or want a journaled filesystem
you could format the storage as 

ntfs and use the fuse ntfs tools in linux 

ext3 and use the IFS drive tools in windows

Ive used both on my dual boot laptop and both worked great

---

### Post by Scarlath on 2008-11-21
Hello again everyone!

When partitioning, do I choose primary or logical partition type? What is the difference?

Sorry if the questions might sound dumb but I've really not done these type of things alot before. Thanks in advance :)

---

### Post by aysiu on 2008-11-21
If you're planning to have four or fewer partitions on one drive, go with primary.

You can have only a max of four primary partitions.

You can have as many logical partitions as you want.

---

### Post by Scarlath on 2008-11-21
What is the difference between the two though?
Can one have four primary + unlimited logical partitions or is this not advisable (as in, if I want more than 4 partitions, should I only use logical)?

---

### Post by Scarlath on 2008-11-22
Bumping the other question as it's been approximately 24 hours and adding another one:

My wireless usb network adapter seem to be working out of the box while using the live cd, should I keep it plugged in, plug it out while installing or does it not matter?

---

### Post by icanfly0307 on 2008-11-22
If you want to use your partitions for storage, I would reccommend logical drives. Usually, the only place I create primary partitions are where the OS is stored like /(root).

Since, your wireless hub is working already, don't do ANYTHING to it and just leave it the way it is. The installation shouldn't mess anything up and everything will work the way it did in the LiveCD once you install Ubuntu.

---

