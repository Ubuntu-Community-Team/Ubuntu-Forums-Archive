---
title: "I'm newly installing Ubuntu onto a USB Drive, and I have a partition question"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by tolbert on 2012-10-11
Hi, everyone.

I'm new to Ubuntu and new to these forums.  I've been trying out Ubuntu from the Live CD and I love it, but I need  to keep Windows (sadly) to run some of the software that I need.  I'd  like to run Ubuntu from a persistent USB drive so I can have the  awesome-ness that is Ubuntu without screwing with my Windows OS.  I  searched around, and I found the thread at [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699) describing what I want to do, and it seems to be one of the most clearly  written set of instructions online.   But there's just one thing I don't understand.  I'm a total newbie to  working with partitions.  I do understand that I make an ext4 primary  partition on my USB drive to serve as my root partition, which will hold  the Ubuntu OS files.  I also have read about swap partitions and  understand that I need to make one.  However, I have seen other  instructions online that say to create a third partition or even a fourth partition.  (I understand that a drive can only have 4 primary partitions.)  With the method  described in this thread, which creates just two partitions on the USB  drive, where do things get saved (things like downloaded applications or documents that I create or download)?  Would files that I save go into the root directory along with the  OS files?  Or do I need another partition if I want to save all my  Ubuntu-related files to the USB drive?  It would be great if someone could clarify the number, type, and size of partitions I should make.

Thanks!!!
tolbert

P.S.  My USB drive is 64gb.

---

### Post by nothingspecial on 2012-10-11
In linux everything is in/under / (root).

You can mount as many partitions as you like inside / or just have / and everything inside/underneath it on one partition.

For example, you can have a /home partition that would contain all your user settings and personal data if you like, or you can have it on the same partition. But which ever way you do it, it will still have to be mounted at /home.

So 2 partitions would be fine (as would 17).

---

### Post by darkod on 2012-10-11
The root and swap partitions is the usual minimum, although technically it can work without a swap partition which makes the bare minimum of one partition which is logical. :) The files need to go somwehere. :)

Most people would also add a third partition with mount point /home making it a separate partition where all users Home folders are.

So, if you have only the root partition, all files of course get saved there.
If you have the separate /home partition your Home folder and everything inside it is on that partition, while the rest of the root filesystem is on the root partition.

But since this is only a usb of 64GB and not an external hdd of 500GB or 1TB, it doesn't make much sense splitting it into many partitions. You can, if you want the exercise.

If you don't want any (small) ntfs parition on the stick so you can use it in windows sometimes guarding files, you can simply create a big root partition and a 2GB swap partition. So the root will be the whole stick - 2GB.

I suggest you use the manual method during installation because it controls where the bootloader goes. You want the bootloader on the stick, not on your main hdd. The automatic method will probably put it on your hdd making the machine temporarily unbootable without the usb stick connected and you having to restore the windows bootloader on it.

---

### Post by tolbert on 2012-10-11
Ok, I think I get it now.  Thanks a bundle, guys!  I'm going to go ahead and try to install, and I'll let you know how it goes.

tolbert

---

### Post by furtom on 2012-10-11
I'm sure it says so in instructions you are following, but to reiterate a MOST IMPORTANT POINT: Be sure to install grub onto the USB stick and not your local sda (or whatever it's called). If you do, you won't be able to boot without the USB stick even if you don't want to run Ubuntu.

I've done this before and it works like a charm. Good luck.

---

### Post by tolbert on 2012-10-11
Ok, so I managed to boot Ubuntu from my flash drive.  (and I did make sure that I put the boot loader on it.  Thanks for the reminder, furtom :)  I just used the two basic partitions, the root and swap partition, in the sizes suggested by darkod.  I installed the 100+ updates that were detected.  And I restarted.  But I've got some serious issues.  The main issue is that it is so, so, so, so slow.  Just about anything I try to do will cause the screen to go dim.  Then after a while, it might or might not do anything.  (I'm back in Windows now) Plus, there doesn't seem to be an option for the display to match my screen resolution (1366 x 768 ).  It either has to be too small to see well or big enough but blurry.  Perhaps this has something to do with the fact that the display settings say "Laptop" but my computer is a desktop?  Laptop seems to be the only option.  There might be other problems but this is as far as I got.  I had to get out of Ubuntu because I couldn't really do anything without freezing it all up.  When I used the Live CD, everything worked great and was super-fast.  I know that my flash drive doesn't have nearly as much gigabytes as an internal or external hard drive, but I've seen people talking about running Ubuntu from a flash drive much smaller than my 64 gb one and still having great results.  Any suggestions?

---

### Post by furtom on 2012-10-11
It's very odd that you say it was super fast with the Live DVD and slow with the USB stick. Something certainly is not right.


Any chance there's something wrong with the stick? Those things don't last forever.

I assume you are using stock Ubuntu. Maybe you can try Xubuntu for example. But it's not your hardware if it ran well from the DVD.

I installed Xubuntu on a USB and it ran really well on old hardware. I DID NOT put swap on the USB, though. I had a swap file already on the HDD. I can't say I love the idea of putting swap on a stick, but still, it shouldn't behave that way.

If I were you, I'd resize your windows partition and put swap on the HDD. I know you didn't want to do that, however, so I'm assuming that isn't an option.

Since there's not a lot of info, I'd say some experimentation is in order. If it were me, I'd try the following in this order:

1. Try a new USB stick with same layout as before.
2 Try Ubuntu installation without swap.
3. Try Xubuntu (or Lubuntu) with swap.
4. Try Xubuntu/Lubuntu without swap.

---

### Post by C.S.Cameron on 2012-10-12
Try a persistent install using Startup disk creator from the Live CD or UNetbootin, it can be faster.

Max persistence size for the casper-rw file is 4GB as it is FAT32.
You can make ext2, 3 or 4 partitions named casper-rw and home-rw of unlimited size. Home-rw contains home and can be reused when upgrading to new versions, casper-rw can't.

Do **not** run software update with a persistent install. It can quickly fill your disk and once full it will not boot.

USB3 may make slow bootable USBs a thing of the past, I have not managed to get it working yet but understand others have.
You can do a persistent install on a disk as small as 2GB.

---

### Post by tolbert on 2012-10-12
furtom-

The stick is brand new, but it's certainly not out of the question that it was just a bad stick already when I got it.  It's a 64 gb PNY from Walmart, and the package claimed it was "high performance."  I've been horribly busy lately and didn't really take the time to research the best flash drives, so I honestly don't know anything about the usual quality of that company's products.  I realize that Walmart isn't the best place to shop for electronics, but it was convenient at the time.  

Some info on my current setup -- an HP Pavilion Slimline running Windows 7 Home Premium (64 bit).  The processor is an AMD Sempron 140, 2700 Mhz, and my HDD still has 228 gb free of the total 287.  The Ubuntu that I'm working with is stock Ubuntu, the 64-bit version.  

I would really like to just resize my Windows partition and install not just the Swap partition but all of Ubuntu on to my HDD, but I'm terrified of messing with my Windows OS.  

I'm starting to think maybe I need to just wait to figure this all out when I have more time.  I'm working part-time, going to school part-time, and raising two small children, so maybe that just doesn't leave enough time and brain power to be changing operating systems .....

---

### Post by tolbert on 2012-10-12
nothingspecial, darkod, furtom, and C.S.Cameron, 

Thank you all so very much for all your help.  I think I might have just figured out how to fix the situation, but I need to try it out.  Once I see if this works, I'll let you know.

tolbert

---

### Post by furtom on 2012-10-12
Well, you didn't ask, but I'll tell you how I would do it.

If I already had windows on a partition and I really wanted to be careful, I'd use a rescue CD like rescatux and repartition the HD with gparted.

Let's say you can get by with half the disk for windows. Resize it. Then I'd make a swap the same size to the amount of RAM you have and the rest an Ext3/4 partition for ubuntu. 

Next, don't install ubuntu, but boot windows. (The MBR is still the same at this point.) It will tell you the disk is bad, and then fix itself. Now windows is happy and you can install ubuntu on the partition you made.

Of course, you don't need to do it this way. You can use the install procedure to do all that, too. That's what it's meant for. My way just gives you the chance to boot windows first on the new smaller partition and make sure all is well or fix it if it isn't.

There are other things you may consider.

1. Is half the disk enough for what you have in windows right now? If not, make sure you leave windows enough space. 

2. maybe even optimize the disk first in windows. I've heard it's a good idea. Never did it myself.

Of course, this is scary, especially the first time. But back up and go for it. Live a little. :)

Just don't blame me if you bork windows. That's why you back up first. ;)

Best,

---

### Post by darkod on 2012-10-12
I usually don't recommend using Gparted to shrink windows, and definitely don't use the ubuntu installer to do that.
Since win7 has the ability to resize partitions using Disk Management, you have all you need.
Make sure you make a rescue cd of win7 first with the included Backup utility, and also a full backup, just in case.

Also, before you start anything you need to plan your hdd layout. Branded machines these days come with all 4 primary partitions used, so you can't create more. In that case you would also need to delete one of the partitions, not only resize to get unallocated space.

And the next thing to consider is whether or not the machine uses UEFI boot. If it does, the limit of 4 partitions doesn't apply but there are other considerations to take into account.

If you decide to install to the hdd feel free to ask for details how to do this.

Having the stick labeled high performance doesn't really say much. Even if they claim a certain transfer rate, it's alwaus "up to", not something they guarantee. It will always be slower than a hdd, but I am little surprised it is slower than the cd.

---

### Post by furtom on 2012-10-12
> **darkod said:**
> I usually don't recommend using Gparted to shrink windows, and definitely don't use the ubuntu installer to do that.
Since win7 has the ability to resize partitions using Disk Management, you have all you need.
Make sure you make a rescue cd of win7 first with the included Backup utility, and also a full backup, just in case.

Good post darko. I always use some form of gparted without major problems, but yes, the windows utility would be better. Accessible from booting the win7 dvd?

---

### Post by darkod on 2012-10-12
> **furtom said:**
> Good post darko. I always use some form of gparted without major problems, but yes, the windows utility would be better. Accessible from booting the win7 dvd?

No, from windows itself. Since Vista, the built-in tool Disk Management can do partition resize. In XP this was not an option so you had to use third party tools. Since Vista you can do it with Disk Management and of course it's the way windows prefers.

---

### Post by furtom on 2012-10-12
> **darkod said:**
> No, from windows itself. Since Vista, the built-in tool Disk Management can do partition resize. In XP this was not an option so you had to use third party tools. Since Vista you can do it with Disk Management and of course it's the way windows prefers.

Yeah, but you would be running on the partition you want to resize.

---

### Post by darkod on 2012-10-12
> **furtom said:**
> Yeah, but you would be running on the partition you want to resize.

It only sort of schedules the task, it will ask you to reboot and do it when windows is not running.

---

### Post by furtom on 2012-10-12
> **darkod said:**
> It only sort of schedules the task, it will ask you to reboot and do it when windows is not running.

Ahh. Got it. Cool. Thanks.

---

