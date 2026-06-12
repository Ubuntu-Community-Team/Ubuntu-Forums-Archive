---
title: "Hoping I have everything figured out regarding dual-booting with XP?"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by oneleaftea on 2007-08-08
Hello,

I recently had a near-disaster trying to use Wubi-installer on my old PC (froze during the install and corrupted my C:\ directory structure, making it impossible to boot into either OS until I fixed it in recovery mode). After fixing it, I uninstalled Wubi, and as such, never did get it working.

I am now faced with the desire to do a more standard dual-boot install with my newer PC. Due to the major hiccup I had with Wubi, I am now more nervous about this than I was initially!

I read through the tutorials on howtoforge.com and psychocats.net, and they were pretty helpful. But I wanted to clarify a few details, related to my particular situation, which I believe should actually be pretty easy.

Details:
- my PC is an Intel Core 2 Duo 4400, with a new Gigabyte G33 board, 2 gigs of RAM, onboard sound and video, and a 300 gig SATA drive.
- I have already installed Windows XP on a 270 gig partition, leaving me with 30 gigs of unpartitioned space for Ubuntu.
- I plan on keeping the partitioning simple, with only the existing Windows partition (at its current size), a 28 gig / partition, and 2 gig swap. 

First of all, in this particular situation, would you recommend the Live CD or the Alternate CD? I am inclined to go Live CD, since it seems easier.

When using the Live CD, I understand that I will be faced with 2 options that could work for me:
- Guided - resize IDE1 master, partition xxx and use freed space
- Manual

Since I will not need to resize the hard drive (already have 30 gigs available for Ubuntu), which would be the easier path to choose? In the tutorial it was not very clear whether the Guided path still lets me set a swap partition? Is it done automatically or does it allow me to decide on the size?

Either path i choose, I should be able to see the 270 gig NTFS partition and leave that alone. Additionally, I should see a 2 gig swap partition and a 28 gig / partition, both with checkmarks on the column that states "format"?

In the situation above, does it look like the guided or manual path is easier, considering that I do not need to resize the existing windows partition?

Also, i don't have much of a desire to import any Windows settings. I am happy to set everything up fresh in Ubuntu, unless there is some reason why it would be a good idea to import from windows?

Thank you very much for your patience. After the wubi fiasco, I just wanted to make sure that I had everything figured out correctly before proceeding!

---

### Post by Steve1961 on 2007-08-08
I generally use the alternative CD but you're probably better using the live CD if you're new to Linux.  As for partitioning, I generally create the partitions I need before installation (you can do this from the live CD with gparted) and then choose manual installation.  You would only then need to setup the main partition with a mountpoint of / and choose to format ext3.  Your swap partition should be picked up automatically if you created it as a swap partition.

Having said all of that, if the guided partitioning step gives you the option of just using the free space on your disk (as you don't need to resize anything) that might be the simplest option for you.

---

### Post by upthelum on 2007-08-08
You could choose the free space in a manual partition setup and then select "Automatically setup partition", which will work fine too.

---

### Post by oneleaftea on 2007-08-08
Thanks for the responses!
so if I go manual, and ask it to automatically set up the partition on the free space, I can then edit the size of the swap partition?

Also, do you see any problems with the hardware I listed?

Thanks so much, and hope I can get this up and running this weekend!

---

