---
title: "A Simple Partition Recognition Problem.."
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by -iLluSiON- on 2006-09-03
Well, to start, I've recently resized my 40 GB C: drive (the one with Windows on it) to 30GB and left the remaining 10GB for Linux usage.  I have two other HD,s but chose the 40GB for the OSes.  
Anyways, It was originally 10GB unallocated space, and both the live cd and alternate CD installations did not recognize it. It just listed the 40GB space.
According to Partition Magic, everything should be fine.

Because it didn't work with the unallocated space, I've now set it to ext3 to see if it would recognize it. Still... nothing.
The only other partition on the C: drive that it recognizes is the stupid little Dell Utilities partition.

Does anyone know how to make the installer recognize my 10GB ext partition?

---

### Post by meng on 2006-09-03
Okay, my suggestion is to choose the installer option for manually configure partitions. This should show you the 30GB Windows (NTFS) partition and then 10GB left over. You can then allocate this as you please (the installer has a partitioner too). Have you thought about having a swap partition? Maybe set aside 512-1024 MB for this.

If I read your post correctly, I think you may be making things more difficult for yourself by getting PartitionMagic to do it all for you.

---

### Post by -iLluSiON- on 2006-09-03
Thanks for you help..
However, that's what I mean. It's not showing up when I choose the manual option. It doesn't show that partition.

---

### Post by meng on 2006-09-03
Ok thanks for clarifying. Tell me what DOES show up when you choose that.

---

### Post by -iLluSiON- on 2006-09-03
For my 40GB Drive it just shows the 40GB partition with the 31 MB FAT16 dell partition. 

It does not show the 10GB I set aside. If it did, it would recognize that it's no longer 40GB and it should be 30GB..


Edit: In other words, there should be an Hda3 but there isn't. The hda1 is the 30mb dell partition and the hda2 is the 40GB HD.

In windows, it recognizes my 10GB partition as the H: drive (I've now reformatted it back to NTFS) and it works perfectly fine.  I had used Partition Magic to do the partitions, and that recognizes it as well.

It's just the Ubuntu installers/system that don't recognize the partition. That's where the problem is. I have no idea why they can't see it!

---

### Post by meng on 2006-09-03
Okay that's weird. I don't know how Partition Magic works - are you sure you wrote the changes to the partition table before you exited the program? I'm loath to make any recommendations since I don't understand what the trouble is. This is why I don't recommend using PM before the install, but I realize that doesn't help you.

---

### Post by benbuzz on 2006-09-03
Hi Guys,

I have the same problem with my HDD. I use a Seagate 250G which has 5 partitions.  I had previously partitioned 30G for Linux and 1.5G for swap - I was using Mepis then - (others are for XP and files for both Ubuntu and XP).  Partitioning tool in Ubuntu sees only the whole 250G.

---

### Post by meng on 2006-09-03
illusion, I have read your edited post now. Perhaps the thing to do is use PM to add the 10GB back to recreate the original 40GB NTFS drive, and then use the Ubuntu installer to do all the resizing for you. This worked for me. It goes without saying that your critical data should be backed up, that would be true even before you used Partition Magic. One can never be too careful.

---

### Post by confused57 on 2006-09-04
You could try using the gparted live cd(approx 30 mb download) to set up your partitions:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by -iLluSiON- on 2006-09-04
Okay.. I merged the WP Partition back into one NTFS 40GB. I then loaded the Linux installation and made a SWAP partition and an 8GB Partition for Linux. Everything was working fine...

and then at the very end, when it went to install GRUB, it halts. THere's an error. ](*,)

---

### Post by -iLluSiON- on 2006-09-06
Ok.. I'm at work right now so I'll make it quick. 

This is my current problem:

As stated above, I originally had a problem with the partitions. I have partitioned (in the installer) a 10gb ext3 and a 500mb SWAP on my 40GB HD. The installer recognizes both of these partitions and I can select them for the / folder and the swap. 
(on a side note - windows doesnt' detect them at all, it just sees them as "used space")

So, I go to install.

Everything works fine... that is, up until the GRUB install appears.  
It detects Windows XP and starts to install and then BOOM. fatal error. Both the alternate and live cds have this error.  I can't exactly remember what the full message is, but I think it had something to do with hd0 if I remember correctly.


My question is: Do I have to do something in my BIOS so that GRUB can install correctly?

It's extremely frustrating because GRUB is at the very end of the install, and it's what fails.

Thanks to anyone who can help

-Illusion

---

### Post by -iLluSiON- on 2006-09-07
Anyone??

---

