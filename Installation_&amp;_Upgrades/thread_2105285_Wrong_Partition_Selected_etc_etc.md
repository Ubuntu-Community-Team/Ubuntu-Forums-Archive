---
title: "Wrong Partition Selected etc etc"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by Arkenbrien on 2013-01-15
Greetings!

I have thought about installing ubuntu alongside my windows 7 operating system. I decided to "test install" it on my old XP, prior to messing with my 7 computer on a separate partition. I shrunk the partition the main partition with Gparted, installed from my home-made disk, and, after a little effort, I had installed ubuntu. It asked me, after installation, to restart my computer. I did so, but it then booted me up to XP. After a little research, I realized that I hadn't chosen the active partition. After choosing what I thought was the correct partition, I restarted my computer. I was then greeted with a black screen with a little white flashing dot in the upper left hand corner. I am convinced that I had chosen the empty partition that I had meant to install Kubuntu. I tried booting windows xp with the same xp installation disk used on that system. For some reason, the moment it asks to confirm booting from CD by pressing any key, the system inconveniently turns off the keyboard, making booting from the XP CD impossible. Wonderful. Thank you for that, Microsoft.

So my only option is to somehow from BIOS to choose another active partition (impossible, from what I have read), install Kubuntu on active partition, or use the Ubuntu disk to run Ubuntu and use something there to change the active partition. 

After wading through loads of generally unhelpful info (for my situation), I still was unable to find anything to aid me in this dilemma. Most of it had to do with Grub or something on the Ubuntu operation system. It was not installed. Furthermore, my old XP cannot connect to the internet to download this Grub.

I really like the interface from what I had seen and experienced, I just wish that hard-drive manipulation was easier.

So my questions are:

If I install Kubuntu (or  later hopefully Ubuntu), will it bring me to a partition or operating system selector screen prior to boot-up?

Can Gparted change the active partition? (I'm going to try this anyways)

And if all else fails, can you give precise instructions on how to change the active partition on the Terminal?

Thank you in advanced. Here I go to see if GParted works.

---

### Post by Arkenbrien on 2013-01-15
Well, GParted worked - halfway. At least I as able to boot XP again.

For the completely lost noob (like me), boot computer with GParted. Simply right-clicking on the desired partition, clicking manage flags, and selecting 'boot' will change the active partition to the selected partition.

While in GParted, I found out that something went awry when installing Ubuntu. I found out that Ubuntu was installed on a sub partition. Which is why my computer didn't boot from that partition. I'm now going to delete the entire partition, turning it into un-allotted space, then start again.

---

### Post by darkod on 2013-01-15
If by "subpartition" you mean logical partitions inside extended one, that's normal. It uses logical partitions because primary partitions have a limit of 4 and it doesn't want to use all of them up in case you need more primary.

As for the boot flag, leave it on the windows partition. Windows uses it, linux doesn't. It doesn't care where it is, while windows can't boot without it (if using the windows bootloader).

From the sound of things, only the grub2 bootloader didn't install. You can add it from live mode. If you still haven't reinstalled and would like to try adding grub2, just say so.

---

### Post by Arkenbrien on 2013-01-15
It is all working now. 

It wouldn't boot at all on the sub-partition/extended partition, where Ubuntu was installed, when that partition was made active via GParted. After making the XP partition active, it was able to boot to XP, but it never showed the OS selector on boot up. I simply deleted the partition with the two sub-partitions, then re-booted Ubuntu from disk and reinstalled it, making a new partition in the process. This has fixed the problem.

Except for one minor detail (that I don't care about). When it shows the OS selector that displays upon boot up, the computer disables the keyboard again. This only happens during the time between BIOS and OS start-up. Must be just a quirk of the old motherboard. I'm just thankful that Ubuntu is the top option in the list. I guess that that means that Kubuntu is out of the question on that computer.

And.... Ubuntu is looking every bit as nice as I thought it would. Although for me right now, my 7 computer is fulfilling all my needs at the moment, so Ubuntu is more of a novelty. However, when this machine breaks down, I'm going to custom-build a super-Ubuntu-computer. :p

---

### Post by Bucky Ball on 2013-01-15
Welcome to the forums and great news! And well sorted.

Please mark thread as Solved from Thread Tools to help others. Cheers. ;)

---

### Post by efflandt on 2013-01-15
What type of keyboard is it?  I cannot see that happening with a PS/2 connected keyboard, but if it is USB maybe you need a different BIOS setting for USB in CMOS setup.  Not sure what settings that would show for USB, but if Auto does not work, try Legacy.

I have an older Logitech di Novo Edge wireless keyboard/mousepad that works for CMOS setup and grub without any drivers and would actually STOP working when Ubuntu started.  So I had to use a different keyboard to edit something under /lib/udev/rules.d/ so Bluetooth would ignore it and allow it to work on its own.

---

### Post by Arkenbrien on 2013-01-16
Thanks, Bucky Ball. I'll mark this thread as solved.

It is a USB keyboard. That is probably the problem. Now that I think about it, I just might have a USB/PS/2 adapter. I'll see if that changes anything, and post the results. 

My XP though has some really old components. It even has a vintage Pentium 4. That's why I decided to test it out on that.

---

### Post by Arkenbrien on 2013-01-18
Update on keyboard: The motherboard is a ASRock 775i65G. It requires a keyboard to have a PS/2 input in order to select boot up from GRUB. 

Well, because the original monitor I used to install everything was unavailable for the test, forcing me to hook it up to my 23", I just might dual boot on my windows 7. It looks that good. :D

I wish I had 2000 dollars to purchase everything in my Tiger Direct wish list full of AMD computer components....

---

