---
title: "Xubuntu install, cannot install alongside Windows 7"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by albert4 on 2013-08-12
I was installing Xubuntu 13.04 from a USB stick, and chose the "Install alongside Windows 7 option"

I re-sized the partition sizes to my choosing and pressed next. It hanged for a good 10 minutes which never happened from ANY of my distro installs, so I shut the PC off and booted up from USB again. Now when I try to install Xubuntu, ""Install alongside Windows 7" is NOT there. It is not my PC so I'm not going to delete W7. Why did that option disappear? How do I install Xubuntu now?

Thanks.

---

### Post by Bucky Ball on 2013-08-12
*Thread moved to **Installation & Upgrades**.*

Welcome to the forums. Did you resize the Win partition with Gparted during install (while running Ubuntu from the CD or otherwise)? Not good. ALWAYS resize the Win install partition with Win software. This could be the cause of your issue if you didn't.

As you resized then the problem occured I'm imagining this is the path you took. The beginning of the Win partition has moved and there's the confusion perhaps. 

When you boot from the LiveCD, get to a desktop and launch Gparted. What does that show? Is there still a Win partition there? Best bet in future; install Windows on a small partition. Leave the rest free space and when installing Ubuntu choose 'Something Else' and manually partition, using the free space. Leave Win partition alone when resizing in Ubuntu.

'Install alongside Windows' is not there because either Windows isn't or its boot sector has been corrupted (or something like it).

If Gparted shows everything to be present and correct try running Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that fails, post back the Boot Info results that you can create with Boot Repair's bootinfo script. That will reveal all. ;)

---

### Post by albert4 on 2013-08-12
Well I gave my cousin back her laptop, and she hasn't complained so W7 must be working fine, which is good. 

I still have Xubuntu on my USB stick, so I should boot from live USB and run Gparted and then boot repair? None of these will corrupt my W7, right?

Thanks a lot. :)

---

### Post by Bucky Ball on 2013-08-12
Nope. Gparted to see if Win is still there. If you have Ubuntu installed already, Boot Repair to fix the boot. If you don't have Ubuntu installed already, then another plan is required, one which forgets about installing Ubuntu for the moment and concentrates on getting Windows booting, something I'm not sure you'll get solved here but you could try posting in ***Other OS/Distro*** sub-forum.

I suggest you boot the machine from the hard drive with no CD in and report what happens. You would expect Win to boot so what happens instead?

---

### Post by albert4 on 2013-08-13
Windows is probably booting, otherwise my cousin would let me know.

---

### Post by Bucky Ball on 2013-08-13
Okay, now I'm confused. Forget about the cousin's machine. What exactly is happening with yours, or is this your cousin's machine you are trying to dual-boot on?

Please outline exactly what is going on and your issue with the machine in question.

Also, I forgot to mention before, is the EFI system? Do you already have four primary partitions? If you have four primary partitions and are trying to install Ubuntu, that won't work, unless you are using EFI (I believe) which is a totally different kettle of fish, a kettle which is not even warm for me. Know nothing about it. Check in your BIOS and try to identify whether EFI or GPT.

---

### Post by albert4 on 2013-08-13
I'm trying to dual boot Xubuntu/W7 on my cousin's machine. From what I saw, it has a W7 partition, and a W7 recovery partition. 

I dont believe Xubuntu installed, because I shut off the PC when it hanged after I decided on the partition sizes. So right now it just has Windows 7.

---

### Post by Bucky Ball on 2013-08-13
Do you actually have this machine in front of you? If not then we are chasing shadows.

If you do, again, and we are starting to repeat, boot from a LiveCD, open Gparted, take a screenshot and post it here so we can see what is on there, where and how.

If you resized Win7 with Gparted or from the LiveCD, and I think this has also been mentioned, then that is probably the issue.

---

### Post by albert4 on 2013-08-13
How do I open gparted from a live USB? It says I require root. I opened terminal and made a root password but it still wont run..

EDIT:Nevermind here you go: [http://imgur.com/1QCo2c1](http://imgur.com/1QCo2c1)

---

### Post by Bucky Ball on 2013-08-14
Okay, now we could be on our way.

If you want to install Xubuntu, I suggest you get into Win (which I presume is on sda3) and shrink that partition with the Win Disk Management utility. It could take awhile. Prior to the shrinkage, run the defrag in Win on that partition and then check in Gparted again to see if it is taking up less than 98Gb. Either way, you are going to need to shrink that partition down to make some free space and you have a number of options to think about.

1/ If, after defrag, sda3 is 85Gb, shrink the partition to 100Gb and leave the rest free space;
2/ Once you have shrunk, create an NTFS partition and move your personal data (Pics, Vids, Music, etc.) into that, then shrink the Win partition further (just the OS will fit on about 35Gb from memory) then install Xubuntu on the free space between what is now sda3 (40Gb) and the NTFS shared partition you created and moved your stuff to;
3/ Backup precious data and start from the beginning, installing Win to a 40Gb partition and leaving the rest free space (your backed up data will go elsewhere and you can symlink to it, from memory Win can be set to look in another place for your 'home' directory (Documents and Folders?);

Reboot when Win resizing complete, make sure it still boots okay and if so, boot from the Xubuntu install CD. 
___

Pen, paper, beverage, think. Everything revolves around shrinking sda3 because that takes up all the room. Concentrate on the Win partitions first. Reboot when Win resizing complete, make sure Win still boots okay and if yes, boot from the Xubuntu install CD.
___

Moving onto the Xubuntu install, whatever you have come up with, you should now be looking at some free space. How much depends on what plan you went with. Before you do anything else, you are going to need to turn that free space into an extended partition into which you are going to install Linux on logical drives. It's straightforward really. Don't bother about creating anything inside the extended partition, you can do that during install by choosing 'Something Else' at the partitioning section and doing it manually rather than letting the defaults take over (for me, never the setup I'm after). DON'T choose 'install alongside' or use the slider (if there is one) or 'Use free space' (although this is an option, depending on the final result you're aiming for).

Depending on whether you are using EFI or not (if so, can't help there), the limitation is four primary partitions on one physical hard drive. You currently have three. Ubuntu needs at least two of any type of partition. The extended partition will act as the fourth primary partition. Xubuntu can be installed on less than 10Gb, but this depends on whether you want to have all your personal data in a /home *directory* within the install, in a separate /home *partition* which you have created during the install, or even on the NTFS data partition you created earlier.

Keep in mind: Xubuntu will read/write NTFS/FAT fine, Win will NOT read/write EXT* filesystem which is what Linux uses. Therefore, any data you want to share between the two OSs _shouldn't_ be on an EXT* partition.
___

Hope that's of some help and not too much of a ramble. Post and ask if clarification required on anything. ;)

---

### Post by mastablasta on 2013-08-14
also back to original question - install xubuntu alongside windows should appear:

1. if all 4 primary partition are not taken yet
2. if there is free **unformatted** disk space available

---

