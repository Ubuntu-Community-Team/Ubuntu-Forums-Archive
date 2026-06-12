---
title: "Install Ubuntu then Windows 7 for a newbie"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by Joza on 2012-08-27
Hi guys. I've been using Ubuntu a while now after migrating from Windows and I love it! First post, so let's see how this goes! ):P

I just bought a Compaq Presario laptop that came with Windows 7 (64-bit). naturally, I would like to install Ubuntu, but I'd like to keep Windows 7 as it can come in handy, particularly since I'm doing a Computer Science course.

There are 4 primary partitions on the HDD - 

C: , HP_TOOLS, Recovery D:, SYSTEM

On top of that, I've tried to resize the partitions and Windows still demands nearly 80 GB with the recovery partition. I can't resize any smaller. 

So I'm thinking, can I make a Windows re-install CD, wipe the HDD and install Ubuntu, and then re-install Windows and fix GRUB and voila?!

How should I lay out my partitions exactly? 

And will the recovery and HP_TOOLS partitions be reinstalled from the CD, or are they installed prior to shipment by the manufacturer and not needed if I have the Windows CD?

Any help will be gratefully appreciated!

---

### Post by darkod on 2012-08-27
As far as I know, you can't make a windows install disc. That's the bad side of the restore partition they ship computers with.

You can make restore DVDs from the restore partition (the installed software should be able to make them for you) and after that you don't need the partition any more.

But using those DVDs in most cases will install the exact layout as the laptop came with, in other words it will wipe any ubuntu you install before that. Usually those partitions are designed to return the factory installation on the laptop, wiping any data, new partitions, or other OSs that you may have on the computer.

If you insist with HP I'm not sure if they can send you real windows install media. In that case you would be able to install windows without destroying everything else on the computer. You can't do that with the restore partition in most cases.

Also note that you have all 4 primary partitions used, so you need to delete at least one so that you can create logical partitions for ubuntu.

---

### Post by Mark Phelps on 2012-08-27
Installing Ubuntu on a win7 pre-installed system with 4 partitions is a lot of work -- but if you're up to it, then read on ... 

ince you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

