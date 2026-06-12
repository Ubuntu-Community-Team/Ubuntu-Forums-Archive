---
title: "RAID array showing up as 2 drives in installer"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by shapelessplanet on 2005-08-07
So, as the title suggests, my raid array doesn't look right during install...
I've got a Promise PDC20376 raid chip on my motherboard. It's otherwise known as the FastTrak 376. I've been waiting since RedHat 8 for this chipset to be supported. Now the 2.6 kernel is rolled out, there’s distro as great as Ubuntu, and I'm all ready to dual boot my main desktop.

I have 2 80gig drives in a RAID0 and it works great in teh windoze. But when I boot the Ubuntu Hoary installer, it detects 2 separate drives on /dev/sda and /dev/sdb. It's detected, but only half there! Shouldn't it be detected as one device?

Anyway. Does anyone have any experience installing Ubuntu on this device? I can't figure out why it detects each individual device.. Something just isn't right. I've got 15 gigs free on the RAID 0 array. At least, that’s what Partition Magic says within Windows. 

Any input would be greatly appreciated. Thanks!
-Shapeless

---

### Post by JuanPedro on 2005-08-07
Damn I Got the same problem and I don't Know wtf to do

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 when u get to the partitioner on ubuntu is there a raid option/setup at the top of the menu ? ...

---

### Post by shapelessplanet on 2005-08-08
<strike>I'm rebooting right now to check. I think there is, but it's something about software raid.</strike>

Just checked. The first screen just asks me to delete all partitions on one of the two drives. If I select partition drives manually, it gives me the option to setup software raid or LVM. If I select the raid option, it says the changes can not be un-done and to make sure I want to setup software raid, so I didn't do it. It doesn't seem to see any free space on either drive, or even the NTFS partition. It's as if the installer sees right past the hardware raid and down to each individual drive. But that doesn't make any sense.

I've attached "screen shots" from my camera phone.

---

### Post by LinNewbie on 2005-08-08
The answer to this is easy .. but one you won't like:

1) Shut off your on-board chip in your mobo BIOS (trust me this is the only way it is going to work).

2) Install Ubuntu:  
a) When partioning choose "Manual Partitioning"

b) Delete the partitions existing on both your RAID drives so that they show as FREE SPACE.

c) Create a NEW partition on the first drive.  Make it a 6.0 GB Primary (or whatever size you want for your Boot partition ... Ubuntu will NOT boot to a RAID0 array so make it small); set its MOUNT POINT to /BOOT, make sure you enable the BOOT FLAG! , and use EFS3.  Next create a new Logical partition to use the rest of that drive.  Instead of EFS3, set this partition as a Linux RAID volume (not the exact wording ... am going from memory here) and finish the partition process for this drive.

d) Do eactly the same for your second RAID drive, but set the first small partition 
as Logical and make it a SWAP partition instead of boot.  Partition the rest of the drive EXACTLY like your first drive.  Finish the process for that second drive.

e) Go back to the main partition menu and choose the Make RAID menu (not exact wording).  Choose MD0.  If it gives a red screen, no worries a s when you go back to the main partition screen you will see a 152 GB (or thereabouts) RAID partition.  Set the RAID partition's mount point to "/" (or your ROOT).  Finish the process for this partition.

f) Now choose the LAST entry on the partition page to finish and continue with the install.

Now to understand what we just did:

1) We made NON RAID partitions at the beginning of each physical drive that we are going to use in the array.  We did this because a) Linux won't boot to a RAID0 so we need the small /BOOT partition; b) We make the small SWAP partition at the beginning of the 2nd drive because if we did not, we would waste the disk space (6.0 GB) on the SECOND drive due to the fact that RAID0 always uses the smaller of the drives used .... Doh!

2) Your end result is two small 6.0 GB partitions that are NOT part of a RAID array.  The rest of your two drives however, are.  

You may wonder WHY DO WE HAVE TO GO THROUGH THIS when our mobos have onboard RAID controllers?

a) Onboard mobo RAID is always a combo of software and hardware RAIDs ... So, in Linux, if you need a driver to enable your mobo hardware RAID, you are out of luck unless someone has made one (which I have yet to see for any distro but I could be wrong) ...  So, just go with Linux's software RAID setups (MDO for RAID0, MD1 for RAID1 etc.)  It works well IMO.

Hope this helps ... and remember that it is from memory so there may be a few mistakes, but I am sure there is enough to get you installed with RAID0 on your system with a bit of effort...

Now, the fun is just beginning .. :)

Good luck :)

---

### Post by shapelessplanet on 2005-08-08
Wow... Thank you SO MUCH for the reply. That is more than I could have ever asked for! 

Unfortunately, I don't have an option to turn off the chip. However, I could dissolve the existing raid array. The mobo actually has 2 BIOSs on it. One for the mobo, and another that boots directly after that which is for the RAID controller. The SATA bus is ONLY usable in a raid configuration with the Promise chip. I've tried installing Windows on the drives when I haven't built a RAID array and it flat out doesn't see the drives, even with drivers. I have to build an array for it to be visible to any OS. However, with the way Linux sees things, it sounds like it may work if I didn't have hardware raid setup... Just had the drives plugged in. 

But, I still have an active windows partition on those drives and can't go mucking around with the RAID array and risk hosing all my data.

While reading your post, I had another thought. I have an 80gig drive in my server that is currently not being used. It is PATA. Fully supported by Linux and my mobo. The ideal option to install on. However... I need to force GRUB to install ONLY to /dev/hda. 

In the past, I've tried installing to a USB HD (It came up as /dev/sdc). Installed great. But after the reboot, my system couldn't boot. It installed GRUB on one of the RAID drives and totally hosed my MBR. Couldn't boot either windows or Ubuntu. I was able to restore the MBR on the array and get back to windows. But the Ubuntu installer installed the GRUB app to /dev/sd_ and not to the USB drive, so I wasn't able to boot.

What I want to do is install Ubuntu to /dev/hda which will be the 80gig drive from my server, and absolutely FORCE grub to install to the mbr on /dev/hda. Thus, I should be able to go into the bios and set the 1st boot device to either the RAID array, or to /dev/hda. And basically manually select which MBR my system sees first when booting... So I could manually choose which boot loader to see and boot my system. I have no idea if that makes any sense at all. But basically, is there a way to install Ubuntu onto my system and make it ask which drive's MBR to install to? The only way I can think of would be to disconnect my RAID drives during the install so it only saw the PATA drive on /dev/hda. Complete the install, then plug the RAID drives back in.

Thanks so much for your help. I hope to have Ubuntu working on my desktop soon. It's already the Primary OS on my laptop, and it works FLAWLESSLY. I love it!

Thanks again.
-Shapeless

---

### Post by Larkki on 2005-08-09
shapelessplanet, do exactly as you said in your last post !
That is the only safe solution to make everything work.

I had the exact same situation when I was installing my ubuntu, and the installer is definitely flawed. I found this kind of logic in it:
If you choose to manually do the partitioning of the drives AND you choose to format some partition (doesn't matter which), ONLY then you get the option in the end, where it asks where you want to install the GRUB.
Now, if you do manual partitioning and doesn't format anything (because everything is already set perfectly, but you just want to check the drives with the partition tool) you DON'T get the GRUB loader prompt in the end, and it breaks your MBR.

So, disconnect your SATA drives, make PATA as 1st bootable drive from bios, and install ubuntu. Then just connect the SATAs again and you can always choose which OS to use, but you have to do this through BIOS.

---

### Post by shapelessplanet on 2005-08-09
I ended up doing that last night. Although, I didn't disconnect the SATA drives. I just did it. I realized that my mobo BIOS boots before the RAID bios, and the installer seemed to think that my PATA drive was more important than the rest of them. That, or /dev/hda gets highest priority when installing the boot loader. Anyway. I'm all up and running. 

I'm lovin it! I think I'm going to buy a subscription to TransGaming when I get paid and try out the point2play thing. Everything seems to be going well.

I ran that script thats in the tweaks forum... 'ubuntusetup.sh'
And a few things from ubuntuguide.org. Does anyone else have any suggestions of things I should config? I heard there is a sound problem on many machines.. I haven't noticed anything too much.

My only complaint is this:
I installed a few games from Synaptic like Flightgear and tuxracer, and they didn't put themselves into the Applications>Games folder. I had to go in and figure out what the program names were and launch from the CLI. Is there an easy way to add applications to the Gnome menus?
Thanks so much!
Shapeless

---

### Post by JuanPedro on 2005-08-09
[QUOTE=LinNewbie]The answer to this is easy .. but one you won't like:

1) Shut off your on-board chip in your mobo BIOS (trust me this is the only way it is going to work).

2) Install Ubuntu:  
a) When partioning choose "Manual Partitioning"

**b) Delete the partitions existing on both your RAID drives so that they show as FREE SPACE.**

[/QUOTE]

There must be a safe way to do that, or not? I have several Gigabytes of very important information on Windows. :neutral:

---

### Post by GreyFox503 on 2005-08-09
> My only complaint is this:
I installed a few games from Synaptic like Flightgear and tuxracer, and they didn't put themselves into the Applications>Games folder. I had to go in and figure out what the program names were and launch from the CLI. Is there an easy way to add applications to the Gnome menus? 

Fire up Synaptic and search for "smeg"

It's menu editor for GNOME and KDE.

---

### Post by eeyoredragon on 2005-09-17
[QUOTE=LinNewbie]e) Go back to the main partition menu and choose the Make RAID menu (not exact wording).  Choose MD0.  If it gives a red screen, no worries a s when you go back to the main partition screen you will see a 152 GB (or thereabouts) RAID partition.  Set the RAID partition's mount point to "/" (or your ROOT).  Finish the process for this partition. [/QUOTE]Sorry to dredge this up...

My problem is that it *didn't* give me a red screen once I set up the partitions as stated. Now I'm at a menu:

"You have chosen to create a RAID0 array. Please choose the active devices for this array.

Active devices for the RAID0 multidisk device:

lists my two devices here. 

<Go Back> <Continue>

Where my devices are listed is a little yellow cursor looking thing. The only problem is, it's never stated how I select both of them (which I assume is what I'm supposed to do). If I hit enter on either one, I'm taken back to the RAID create menu. If I go back from there, I do not see a sum created partition. It's just as it was before I went to the RAID menu. It also doesn't tell you how to get to back or continue when you're trying to select devices.

Any help with this?

---

### Post by chippy57 on 2005-09-17
[QUOTE=shapelessplanet]I ended up doing that last night. Although, I didn't disconnect the SATA drives. I just did it. I realized that my mobo BIOS boots before the RAID bios, and the installer seemed to think that my PATA drive was more important than the rest of them. That, or /dev/hda gets highest priority when installing the boot loader. Anyway. I'm all up and running. [/QUOTE]

I also have XP Pro loaded on to SATA RAID 0 FastTrak 378 and Hoary 5.04 on another drive attached to the SEC IDE. I use bios to boot which ever I want, I already started a thread a week or so ago about this very subject except I am going to use a 3rd party Bootmanager which is part of a package called Acronis Disk Director which will allow you to boot several os's and partition whatever,  with Ubuntu grub needs to be installed in the root partition, then Acronis will recognise it. I downloaded the trial version and it pretty slick you get 15 days to try it out.....and of course one has to pay but for me its worth it ...saves all the faffing around with raid, maybe the stable version of breezy will address this prob.

regards

chip

---

