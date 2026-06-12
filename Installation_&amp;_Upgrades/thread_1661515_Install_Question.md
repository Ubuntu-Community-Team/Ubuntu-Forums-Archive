---
title: "Install Question"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by ChrisWells on 2011-01-06
Hi, I just registered to ask a single question as I don't want to mess anything up.

I've got a 1TB HDD with only data on it (only music and videos) it is a single 1TB NTFS partition.

I have got a 60GB SSD with Windows 7 on it, as my main drive.

I understand if I want to install Ubuntu (10.10) on the 1TB drive I need to unplug the SSD while installing it in order to dual boot by pressing F8 (the way I want it to be) so that Grub doesn't get installed on the SSD (which has happened previously).

What I want to know is can I partition the 1TB drive to install Ubuntu without any data corruption or anything? I have read that NTFS can lose data if partitioned with data already on it (I have no way of backing up my 100GB of files on the drive, as currently this IS my backup drive).

What I want to do is have 900GB for files, and a 100GB partition (or partitions adding up to 100GB) for Ubuntu- what is the best way to do this?

I don't need seperate partitions for ubuntu, can I install the whole thing to the 100GB partition and boot from it? Or do I need swap as well?

I was thinking of making 900GB partition, 4GB partition for swap (if needed) and 96GB partition for Ubuntu (/ if I understand) as this is what the "erase entire drive" option creates.

Sorry if I've made a wall of text out of this, I am another noob but want to use Ubuntu as my primary OS, as I think it will force me to learn it, and I want to keep Win7 on my SSD as it's optimized for it and thought I may as well use HDD for Ubuntu as it doesn't need defragging.

Thanks for any help O:)

---

### Post by Quackers on 2011-01-06
Welcome to UF :-)
You should use Windows disk management console to shrink the data drive by 100GB. This will create unallocated space for Ubuntu to install into.
In the installer do not select the "install alongside" option as this could possible over-write your data! You should select the "specify manually" option and create the /root and swap partitions manually.

You should also be aware that using your "backup drive" to install an operating system is potentially hazardous, by virtue of the fact that any re-partitioning carries a (small) risk!

---

### Post by Bucky Ball on 2011-01-06
> **Quackers said:**
> Welcome to UF :-)
You should use Windows disk management console to shrink the data drive by 100GB. 

+1. BUT, defragment first. VERY important as Windows spews data all over the partition so you will get an inaccurate reading of how much you can shrink it by. Defrag and that will jam the data back together (as well as Windows is capable anyhow).

This is the best defrag tool I have found and defrags ANY file type (including tivo which the Windows defrag tool won't touch).

[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

Good luck and welcome. ;)

---

### Post by ChrisWells on 2011-01-06
Thanks for the replies, I'm on a PMagic disk right now playing with GParted.

I did wonder about defragging, so I'll do that first. Maybe it's not needed- but is there a way to defrag the drive unmounted? Or is that not even possible?

I need help with 2 other things (please), do I create the Ubuntu partitions as preceeding, or following (when I resize)?

I'm looking at it now and when I go to do free space preceeding it says something about an operating system might not be able to boot, not that it matters as no OS is on the drive, but how do I go about making 2 partitions (one 96GB for the / and  the other 4GB for swap)? If I choose preceeding I can only make 1 unallocated space, do I need to make that first, then make another preceeding space? The / and swap partitions are both logical yes?

I am so sorry if I'm confusing, I just know I'll end up pressing apply and it'll mess it all up otherwise lol

Thanks for the help

---

### Post by Bucky Ball on 2011-01-06
Drive need to be mounted to defrag.

Are you sure you're looking at the Tb drive? Sounds silly but odd message about he OS.

It is wise to have a separate /home partition also. 

/ = 15Gb should be plenty.
/home = big as you like - your personal data.
/swap

It is odd because you only have the one partition on that drive. Your problem can occur when you are trying to add a fifth partition to the same physical drive. They can only have four primary partitions. One of these, of course, can be an extended inside which you can have up to 99 logical partitions. ;)

If you look at the drive in the partition tool you are using you will see data is probably spewed all over the place so defrag definitely necessary else you will only be allowed to shrink the partition to the first lump of data at the end of the partition (which might be 20Gb from the end of the partition).

---

### Post by ChrisWells on 2011-01-06
Yes it's definately the TB drive. I had 1.71MB of unallocated space for some reason, I merged that with the remaining space so it's 1 large partition, booted into Windows and it ran chkdsk turned out fine- drive and data works fine.

I've defragged the drive just now.

Now I'm back to GParted with the 1 large partition. When I click resize, I get the option of where to create the new free space. Should this be free space preceding, or free space following?

I'm guessing it's preceding (at the start of the drive) I take it I should have the 96GB partition at the very start, then the swap, then the files.

It's just that this error message about OS not booting is putting me off.

If I go to make free space following, I get no error.

Maybe I should try this with my SSD unplugged just to be safe.

---

### Post by Bucky Ball on 2011-01-06
Yes, unplugging the SSD if safer, but then Windows will not be picked up and added to the menu list during the Ubuntu install. This can be fixed later, though. 

/ first, /home second, /swap at end.

You would always put the OS at the beginning of the drive. Thinking is that part is the fastest but on speedy modern drives this doesn't make much difference.

That message suggest the MBR is on that Tb drive but I can't imagine why.

---

### Post by ChrisWells on 2011-01-06
Ok, thanks for the help. I'm off to bed now, but I'll try some stuff tomorrow.

I'll try booting Windows from SSD with the HDD unplugged, just to rule out the MBR thing (god knows why I'm getting the message- you sure it's not a generic message *in case* an OS is installed on the drive?)

If it all boots fine I'll unplug the SSD, then partition the HDD like you said and leave the Files partition at the end.

I'm thinking of leaving the home partition out and just having a / and swap, but say 11.04 was out tomorrow and I wanted to upgrade from 10.10, does the home folder get wiped? Is that the reason for the partition? I know it's so you can re-install, but does an upgrade from the update manager wipe the home?

Anyway thanks for the help I'll let you know how it went if it's all up and running. I know it's a silly thread but I've messed things up in the past and need to make sure it's all done 100% this time :wink:

P.S- I don't want Windows added to Grub, I want it so I have to press F8 to select boot device, just to explain why I'm leaving SSD unplugged.

---

### Post by Bucky Ball on 2011-01-06
You won't get an upgrade from the update manager for 11.04 I don't think. Generally, the upgrade is to the next LTS release (10.04 LTS currently).

f8 to boot from device? Got you. Not sure why, but again, sure you have your reasons. ;)

---

### Post by ChrisWells on 2011-01-07
Ok I went to GParted after defragging the drive and went to create a new partition at the start of the drive, ETA was 4 hours just for the read, then another 4 hours for copy, I don't know what comes after that because I cancelled it, funny enough all my data is fine. I took a huge risk just because I'm impatient lol.

I dug out an old 74GB Raptor I had and put Ubuntu on that, after all this lol I chose just to erase and use the entire disk which made the / and swap partitions, what I want to know is if an upgrade does come up in the future, will I lose any data from /home or whatever? Or can I upgrade just like any other package from update manager?

I can always reformat if I need a seperate /home partition as I'm on a clean install anyway.

Thanks for the help

---

### Post by Bucky Ball on 2011-01-07
No. Upgrade shouldn't kill anything.

Always wise to have a separate /home. Advisable. This order:

/ first
/home second
/swap last

Good to hear you got it all sorted. Enjoy the OS, the learning curve, and be sure to post back in a new thread with any further issues. 

Good luck! ;)

---

