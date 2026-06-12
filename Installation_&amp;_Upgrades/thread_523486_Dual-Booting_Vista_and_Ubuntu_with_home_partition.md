---
title: "Dual-Booting Vista and Ubuntu with /home partition"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by Tom B on 2007-08-12
I just bought a refurbished Dell that came pre-installed with Vista. I have been using only Ubuntu happily for about two years, but I've decided to keep the vista for a few reasons; Joost, my Creative mp3 player that I could never get to work properly on Ubuntu, and my midi keyboard. Other than that, I would like to use only Ubuntu. I have been reading various guides  ([like this one]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")) and threads and I decided to partition my drive like [this site]("http://www.psychocats.net/ubuntu/partitioning") suggested: a small NTFS partition for vista, a large Ext3 /home partition for shared data (using FS-Drive for windows to read/write), a small Ext3 / partition for Ubuntu, and a Swap partition. Now, before now I knew absolutely nothing about partitions and dual-booting, so I just have a few questions. Does this configuration make sense? Is there a better one? Right now under "Disk Management" vista shows me three volumes: a blank one with 39 MB, the OS C: drive with about 223 GB (90% free), and a the Recovery D: drive with 10 GB (63% free). I'm assuming I shrink the C: and leave D: and the other one alone, right? Everyone has said to do the shrinking with vista's built-in tool and not the ubuntu live cd, but what about the /home and swap partition. What should I use to make those? About how big should all of those be? Sorry if I'm overloading with questions, but I'd rather not mess this up because I didn't ask. I've reinstalled Ubuntu a couple times, but I would like to avoid having to reinstall vista (I've heard stories). Thanks in advance.

---

### Post by ddrichardson on 2007-08-12
I would use gparted to resize.I don't know about a Windows utility - but would be surprised if MS provides one to handle ext2/3.

Swap is best set to double the size of installed memory (depending on who you talk to). Remember you can only have 4 primary partitions so you will need to create at least one logical partition - which can then give extended partitions.

Don't touch the recovery drive at all. Recovery partitions usually have a utility in Windows that hides them and they don't like changes. Plus if you mess it up you'll lose the ability to restore Windows without obtaining discs which can be a pain.So yes shrink C.

As for sizes, apart from swap, WIndows tends to use much more space than Ubuntu, you can install root (/) comfortably in 6 to 8 Gb - it depends how much stuff you need to store in home.

---

### Post by forestpixie on 2007-08-12
I would use the vista shrinking tool to shrink c:\ (only because I've read it here more than once) to whatever size you want to give it. Leave the blank and recovery partition alone.

You can obviously use the livecd to deal with the rest of the partitioning or download the gparted livecd and use that. I now use gparted to do the partitioning before I do the install, personal preference though.

I'd have a 7Gb /root partition, 2 times RAM size for a swap and leave the remainder as /home. 

Make sure you do all the defrag and backup before you start though.

Edit - just like buses - wait for hours and 2 come along at the same time :D

---

### Post by ddrichardson on 2007-08-12
> **forestpixie said:**
> Edit - just like buses - wait for hours and 2 come along at the same time :D

I don't know where abouts in the UK you are but I'd wait for days for a bus, and still none would come. ;-)

---

### Post by erfahren on 2007-08-12
I'd use the Vista Disk Management tool as well to shrink the C:\

I've found that the Ubuntu Alternate CD partitioner (text based) is a little easier to use than the Desktop (or "Live") CD for creating logical partitions. I've had to mess with the Desktop one a little to get it to do what I wanted (but maybe that's just me). [Herman's Dual Boot Guide]("http://users.bigpond.net.au/hermanzone/) has excellent info on partitioning on his pre-install page, as well as a great overall guide (with screenshots) for installing with the Alternate CD.

Here's a great little standalone freeware defragger that works better than the Windows defragger: [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

--- just my input!

good luck!

---

### Post by Tom B on 2007-08-12
I defragmented and then tried to use windows tool to shrink the C: drive. It gives me 

Total size before shrink in MB: 228137
Size of available shrink space in MB: 68449
Enter the amount to shrink in MB: 68449 (a dropdown box that lets you pick any number lower than that)
Total size after shrink in MB: 159688

This dosen't seem right to me. It says there are 200GB of free space on that partition. Why can it only shrink it 68? Or am I reading/converting that incorrectly?

---

### Post by Tom B on 2007-08-18
Update: I got the vista partition down to about 75 GBs with various defraggers and gparted. It still seems huge, but I don't think I'll ever really need that space anyway. I successfully installed Ubuntu in a 7 GB partition and have a 140 GB partition for /home and shared files. But now I have a problem I hadn't anticipated: all of my settings, preferences, music, documents, and everything else are on my old (and I mean old) dell. The music I can transfer from my mp3 player, the documents I can put on a thumbdrive, but how can I get all my preferences transferred? Is it possible?

---

