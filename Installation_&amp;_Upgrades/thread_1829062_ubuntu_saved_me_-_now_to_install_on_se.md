---
title: "ubuntu saved me - now to install on se"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by silvercue on 2011-08-20
I recently had a Buffalo Linkstation with 1TB of data fail on me (I know I should have backed up better). I thought all was lost until I managed to take the HDD out and access it via my PC and Ubuntu.
 
Windows cannot see the disk as it is an XFS file system.
 
I have never used Ubuntu and used a Live disk rather than install. I was so impressed with it and I managed to copy all of my data to a new ReadyNas Ultra 2 NAS - which again Windows could not do, even using a proigram like UFS Explorer.
 
Now I would like to install Ubuntu on the drive I salvaged from the Buffalo - I have Windows Vista 64 on a Raid_0 set up and want to leave that intact.
 
I have read a lot here about dual boots, but that is not really what I want as the Operating Systems will be on totally different physical disks.
 
I would like Ubuntu on a seperate disk to Windows so I can chose when I want to boot into it.
 
I assumed this would be a simple case of installing onto that disk, but am worried there may be a conflict created with Windows.
 
Should I detatch the Windows disks first?
 
Any other problems I need to be aware of? (I have searched, there is just too much and can't see the wood for the trees!)
 
Only minor problem is how I can format the disk as Windows can't see it! And UFS Exploprere doesn't have that option.

---

### Post by Frogs Hair on 2011-08-20
I don't think disconnecting the Windows drive/s will be a problem , but if you run into boot loader problems see the link . There is a lot of information about boot loader problems and how to solve them .[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by silvercue on 2011-08-20
sounds like people have problems with this....I am not sure I will bother if it will be a headache.

---

### Post by recluce on 2011-08-20
This might be easier than you think if your machine has a good BIOS that offers a boot menu. On my system, if I wanted to do what you are planning, I would disconnect the Windows drives and install Ubuntu. After that, reconnect and during the BIOS boot post, hit whatever key you need to get to the boot menu. Here, you should be able to either select your Windows RAID or your Ubuntu drive.

---

### Post by Basher101 on 2011-08-20
this wont work like this. if you install ubuntu on a drive whilst no other is connected, then the ubuntu bootloader (which is called Grub2) wont find any other OS it could boot. You can easily fix this however, you must first have both hdds connected, then login to ubuntu , open a terminal and type ```
sudo update-grub
``` this will create a new configuration file for your bootloader and then it will search again for other bootable OSs. After that you should be able to select windows in the grub2 menu

---

### Post by recluce on 2011-08-20
> **Basher101 said:**
> this wont work like this. if you install ubuntu on a drive whilst no other is connected, then the ubuntu bootloader (which is called Grub2) wont find any other OS it could boot. You can easily fix this however, you must first have both hdds connected, then login to ubuntu , open a terminal and type ```
sudo update-grub
``` this will create a new configuration file for your bootloader and then it will search again for other bootable OSs. After that you should be able to select windows in the grub2 menu

I am not sure that you read the OPs request or my post. When selecting the drive to boot through the BIOS boot post, GRUB is neither needed nor involved in any way in order to boot the Windows drive/RAID. Again, this is a scenario with TWO separate drives for Windows and Ubuntu.

---

### Post by Basher101 on 2011-08-20
would then not the two bootloaders interfere? i havent tried a system where windows and linux have their own hard disk. Though if that DOES happen, use my instructions.

---

### Post by silvercue on 2011-08-20
Hi all,
 
thanks for taking the time to reply.
 
I should clarify.  I am looking to have the two OS on two totally seperate drives.  Vista on my RAID Config and Ubuntu on my other drive, which is currently XFS, but I am looking at how I can change that...if possible.
 
Anyway - I simply wanted the option of booting into an installed Ubuntu sometimes, set it up and play.  I am happy to select Ubuntu from BIOS menu when I want it.
 
It would also give me quick and easy access to my NAS stored data if my Windows install died.
 
What I don't want is anything that introduces risk to my current Vista set up.

---

### Post by Basher101 on 2011-08-20
If its on the other hdd nothing can happen to your vista. Except you somehow are able to select your vista hdd during the install process as the install destination^^

---

### Post by recluce on 2011-08-20
> **Basher101 said:**
> would then not the two bootloaders interfere? i havent tried a system where windows and linux have their own hard disk. Though if that DOES happen, use my instructions.

I have tried it, it works if the system has a BIOS with a working boot menu. The BIOS will then load the MBR of the selected drive and thus invoke the boot loader. In this scenario, GRUB and the Windows boot loader are completely unaware of each other.

So to the OP: if you disconnect the Vista drives before installing Ubuntu, they will be completely safe. Ubuntu will see the connected XFS drive and offer you to wipe the drive during installation. So no worries about formatting, it will be automatic.

---

### Post by Basher101 on 2011-08-20
Wont it be more comfortable to have Windows inside the grub menu? then you would just make your HDD with ubuntu on it the default hdd, then when it loads grub you can either select windows or ubuntu...much easier then having to switch the hdds from the bios or F12. But for the installation alone, it is better to ***_NOT_*** have your windows hdd connected.

---

### Post by recluce on 2011-08-20
> **Basher101 said:**
> Wont it be more comfortable to have Windows inside the grub menu? then you would just make your HDD with ubuntu on it the default hdd, then when it loads grub you can either select windows or ubuntu...much easier then having to switch the hdds from the bios or F12. But for the installation alone, it is better to ***_NOT_*** have your windows hdd connected.

Of course it is more comfortable - and that is the way I have set it up for myself. But it is not what the OP wanted...

---

### Post by silvercue on 2011-08-21
I thank you all :)
 
See you on the other side!

---

### Post by silvercue on 2011-08-21
OK installed - so far so good, though I haven't logged back into Vista yet.

One strange thing - the installation has wiped disk of data - that is fine, but it said I needed 4gb (or similar to install) yet when I look at my file structure it has already taken up 5.2GB with over 530,000 items - this seems rather high.  I installed a couple of updates but that took seconds at 1.5mbps - so can't have added up to over a GIG.

Is this normal?

---

### Post by silvercue on 2011-08-23
Solved:
 
Here is what I did:
 
1. Disconnect Vista drive(s) so only the spare drive is connected.
2. Change boot priority in BIOS to CD/Hard Drive and make sure hard drive priority is correct.
3. Boot into Ububtu Live disk
4. Install Ubuntu - which wipes data on disk.
5. Update Ubuntu as required
6. Power down and reconnect Vista drives
7. Power up and enter BIOS to select default boot priority.
 
Now I can simply change the hard drive priority in BIOS when I wish to swap operating systems.
 
This may seem cumbersome, but it is very clean and suits my needs perfectly as I will be using Ubuntu for backups and for making lots of changes on my NAS (moves, renames, deletes) as it does that faster than Vista (router issue I think).
 
There appears to be no conflicts or issues whatsoever - two seperate, mutually exlusive and clean installs.
 
Thanks for the tips.

---

