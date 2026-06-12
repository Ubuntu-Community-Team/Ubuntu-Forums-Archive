---
title: "3ple Boot, second attempt - please help !"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Amamba on 2010-01-26
Last Friday, I attempted to install Ubuntu as a 3rd boot option on a system already running Windows XP and Open Suse. This resulted in a major "ouch" with completely reinstalling Windows and repairing Suse. The problem was, after install, Grub2 would not see Windows and no matter what I did it wouldn't see it.

I still want to try Ubuntu. What I would like to do - if it is at all possible - is to install Ubuntu without installing Grub2, then going into Grub menu editor in Suse (which I am much more comfortable with) and manually adding Ubuntu to the menu.

Also, I want to install Ubuntu in the currently empty partition on the disk that already has Suse and 2nd windows partition installed (the other Windows partition is on a separate disk and it holds the system, this one holds files and programs).

So, is it possible, and how can I do it ?

---

### Post by Amamba on 2010-01-27
Anybody ? This question isn't ***that*** stupid, or is it ?

---

### Post by darkod on 2010-01-27
OK, so you have empty partition on one of your disks right? Delete that partition so you have unallocated space instead.
Then boot with ubuntu cd, Install Ubuntu option, and in step 4 tell it Use Largest Available Free space. That will use the unallocated space. For swap partition it might detect your Suse partition and use it, I'm not sure.
On the last screen, before clicking Install, click the Advanced button and that will show you advanced settings for the bootloader. Just deselect installing the bootloader and it won't install grub.
Then you can edit Suse grub to include ubuntu.
I have to say I'm surprised it didn't work first time, grub2 is usually fine finding other OSs.

PS. You don't have to delete the existing partition as I said above. If you feel confident using manual partitioning, just use it as ubuntu root and use the existing swap partition. It all depends how well you can handle linux. Sorry, the advice to delete and let ubuntu create partitions is usually for people new to linux.

---

### Post by Amamba on 2010-01-27
Thank you !!!!

This time Ubuntu did see XP, so the installation went smooth (I hope - didn't check if I can actually boot XP, but it shows in Grub menu so I'm sure it's going to be fine).

Now I can start playing with it & comparing with Suse. Straight out of the box it seems faster and font rendering is exceptional.

---

