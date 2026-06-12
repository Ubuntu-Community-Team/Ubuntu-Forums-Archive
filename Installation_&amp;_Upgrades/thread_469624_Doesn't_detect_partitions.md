---
title: "Doesn't detect partitions"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by prodigy_00 on 2007-06-10
I have my hard drive split into 3 partitions: 
180gb for Windows XP
80gb for data
20gb for Linux

and the rest is free space. I tried installing Ubuntu from the LiveCD but I got stuck on step 4. I only have 2 options:
Guided - use entire disk
 SCS13 (0,0,0) (sda) - 320 GB ATA ST3320620AS
Manual

I don't have the option to install it on the partition I made for Linux. If I select "Manual" there's only /dev/sda listed there and if I try to install Ubuntu on it it says the other partitions will be removed. I tried formatting the partition to ext3 but I still have the same problem.

---

### Post by coffeecat on 2007-06-10
I don't know why the LiveCD installer isn't offering you the third option. 'Custom' is it? Can't remember. The only thing I can think of is that because you haven't set up a swap partition perhaps the live CD is programmed not to offer you the custom option. That's just a theory. I really don't know whether it's true.

But whatever - you need a swap partition. Are you new to Linux? I notice that you only have 1 post so far. (Welcome to the forum by the way :). ) If you are new to Linux, a word of explanation. Whereas Windows uses a swap file, Linux needs a separate partition.

So - fire up the live CD, go to System > Administration > Gnome partition editor and you'll open a very nice graphical partitioning tool. Select your unpartitioned space and create a partition with 'swap' as the filesystem type. Rule of thumb for size is 2x your RAM, but no more than 1GB, unless you intend to use suspend to disk when the swap needs to be at least as large as your RAM.

Once you've created the swap partition go back into the installer and see if it now plays ball with you.

**Edit - afterthought**: I don't know how much you know about partitioning, so you may know this already, but I'll post it anyway. If those three existing partitions are primary ones (Gparted will tell you when you open it) and you create a primary swap partition, you'll make the remaining free space inaccessible in the future because you're limited to 4 primary partitions. Instead, to give you future flexibility, I suggest you format all the free space as an extended partition, and then create a swap/logical partition within that. Then, if you need more partitions in the future, you can create more logical ones. Windows can't boot from a logical partition; Linux can. Game, set and match to Linux! :wink:

---

### Post by prodigy_00 on 2007-06-10
When I started GParted for some reason it just showed my entire hard drive as "unallocated". It didn't show any of my partitions. 

EDIT:
I just tried opening up the "disk" app on the desktop and all of my partitions were listed on the left side. I could access all of my files on my data and xp partitions.

---

### Post by coffeecat on 2007-06-10
> **prodigy_00 said:**
> When I started GParted for some reason it just showed my entire hard drive as "unallocated". It didn't show any of my partitions. 


I experienced something similar on my Sony Vaio laptop. The partitions showed up OK in some GUI apps (in Suse) but Gparted showed everything as unallocated. The first partition was a hidden recovery one and I think Sony had done something weird to the partition table which was confusing Gparted. What was odder was that Suse was able to set up partitions and install itself but Ubuntu, Fedora and Mepis all failed. That was over a year ago and I solved the problem by making an image of the hda2 Windows C: partition with Acronis, completely reformatting the HD using Gparted to get an intelligent partition layout and then restoring Windows to hda2. (It wouldn't work on hda1 for some reason.) Since then I've had no problems installing any of several Linux distros and I've ceased to puzzle over what was going wrong.

I'm afraid this doesn't help you much and I don't have much more to offer, but one question? How did you create the Linux partition if Gparted won't work and what filesystem type is it? The reason I ask is that some Windows-based partitioners can create Linux filesystems. Acronis Disk Director is one and if you have access to such a thing it might be able to cope where Gparted has failed.

I hesitate to suggest using a command line utility such as fdisk. With the possibilty of something irregular in the partition table it might do more harm than good.

What make of machine is it, by the way?

---

### Post by prodigy_00 on 2007-06-10
This is my machine [http://support.gateway.com/s/PC/R/4053/4053sp3.shtml](http://support.gateway.com/s/PC/R/4053/4053sp3.shtml)

I was able to create an ext3 partition using Partition Magic so I'm not sure why its not detecting it.

---

### Post by coffeecat on 2007-06-11
Thanks for the link. I've no experience of Gateway but I guess they've done something similar to what Sony did to my machine.

I have only one suggestion left. You've got about 40Gb unformatted space left. Check to see if Partition Magic will create Linux swap partitions. I've had a quick look on the specifications page of the Norton website and Linux swap is not listed, but hopefully that spec page may not be complete. If it can, bear in mind what I said about creating an extended partition first. Do that and then in that make a logical swap partition of 1Gb. Then see if the installer will work properly.

Failing that, the only solution I can offer is the rather drastic one I took with my Sony. That means making an image of your Windows partition with something like Norton Ghost, backing up your data and completely reformatting the whole drive with Gparted. If you do that you'll invalidate any Gateway warranty you have. And I make no guarantees either. It worked for me. As the old saying goes - your mileage may vary.

Actually there is one other possibility - to fit another hard drive. That will appear as sdb and Gparted will be able to partition it for you and you can install Ubuntu on that. BUT - if my theory is correct and there is something odd about the partition table on sda, the installation of grub to the mbr may fail.

---

### Post by floke on 2007-06-11
Some partitioners do weird things so that gparted can't read them - the partitioner for PCLinuxOS does this too. If you type 'sudo fdisk -l' in a terminal you'll see that linux itself can see the partitions. My suggestion would be to try the alternative installer. Or - worst case - reformat everything from scratch and use gparted from the live cd rather than pt. magic. to set partitions up.

---

### Post by prodigy_00 on 2007-06-11
I solved my problem. I tried creating partitions with Acronis and the installer detected them. I'm running Ubuntu now :D

---

### Post by coffeecat on 2007-06-12
Excellent news! Acronis comes to the rescue again. :) I hope you enjoy Ubuntu.

---

