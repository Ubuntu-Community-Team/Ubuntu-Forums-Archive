---
title: "Trippleboot? W7 32bit, W7 64bit and Ubuntu?"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by psythrone on 2010-04-19
So... For a while I have been planning on installing Ubuntu and since I ran recently ran out of physical space for hard drives (4 mounted in the chassi and a fifth lying loose inside). I have been dual booting W7 32bit and W7 64 bit (the loose drive, both system drives are 200gb and running out of space) so I thought I'd get a new 1tb drive and clone both my system-disks onto different partitions on the 1tb disk. 

After searching for a while I understood that the best (free) way of doing this is probably using dd on linux.

This made me remember that I haven't been using linux in a while and I should install it again, maybe on a third partition on the new disk. 

So the idea is this: I'll format the new drive and make three partitions, one 350gb for win7 32bit, one 350gb for win7 64bit and a final ~300gb for Ubuntu.
Then I'll boot linux from a pen-drive to clone the the windows systems onto the new disk and finally install Ubuntu.

And now the important part of the post: Is this a horribly bad idea, will it even work and could someone please be nice and give me some pointers on how to actually do it?

Also, what Ubuntu version should I install, 9.10 or some other one?

Edit: 
After some research I have noticed that it might not be possible to clone over both my windows drives to different partitions on a bigger drive, so now I'm wondering if it is possible to clone over the 32bit W7, then create the other two partitions and reinstall W7 64bit on the second partition and install Ubuntu on the third?

---

### Post by oldfred on 2010-04-21
I do not have direct answers but a few cautions.

I have seen where someone tried using dd to copy from a old small drive to a new larger drive. dd is intended to only copy from same size to same size. That user then could not see the full size of his hard drive, dd had set it to the smaller size. We were not able to reset it but he ended up downloadinig disk tools from the drive mfg that reset the drive size.

Windows hides some serial number or setup data in the MBR and does some checks to make sure you have not copied to a new system, some changes it will accept, others it wants to call home and verfiy. I put in a new motherboard with same drives and my XP had to check with BillG to see if it was ok with that. (it was :)).

Some info on multiple windows installs, even if you do not want to know all the gory details which this explains it is worth while to check the pictures on MBR, PBR and how windows combines boot into one active (boot) partition.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

With a large drive you may want to have separate data partitions to share data with all installs (NTFS) and/or separate /home for Ubuntu data and settings. Your Ubuntu install then only has to be 10-20GB plus swap equal to RAM.

---

### Post by psythrone on 2010-04-22
Thanks for your answer, you actually replied while dd was running (took 10737 sec :P).

It worked well and all I had to do when it was finished was resize the partition (186 gb to 325 gb), and create a 325 gb partition for w7 64bit and installing it. Being the gamer I am I didn't get any further than that yesterday since I had some gaming to do. I'll probably install ubuntu today.

I don't think I'll make a fourth partition on the drive to keep shared files since I have 3 more drives in the computer with a total space 2.75tb, and then we have the external 1tb drive.

---

