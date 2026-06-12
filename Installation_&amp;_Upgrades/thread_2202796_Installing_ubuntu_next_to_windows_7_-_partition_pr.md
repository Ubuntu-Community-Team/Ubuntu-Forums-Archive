---
title: "Installing ubuntu next to windows 7 - partition problems"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by jechadwell99 on 2014-01-31
I am trying to install ubuntu 12.04 alongside windows 7. Unfortunately, when I follow the instructions from the official ubuntu site (here: [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)) the "Install alongside windows" option does not appear. Instead, there is an option to install 'inside' windows 7. I do not want that so I did a little research and discovered that my problem is probably that there are already 4 primary partitions on the hard drive (C:, HP_TOOLS, RECOVERY(D) and SYSTEM). What do I do? Which ones should I delete/move (if any)? Please help me. Thanks!!!

Note: I have absolutely no experience in partitioning whatsoever.

---

### Post by sudodus on 2014-01-31
Well, it is a common problem with HP computers. I think most people

Edit: {
0. **backup** at least all personal files because editing partitions is risky
}

1. copy the content of thep partition HP_TOOLS to a directory (with the same name) in the main Windows partition.

2. After that they remove the partition and get logicial space for an extended partition.

3. Next they shrink the Windows partition to get disk space (unallocated space) for Ubuntu (I suggest using a Windows tool for that). Ubuntu needs at the very least 8 GB, but I would say 16 GB or more for the root partition and a small swap partition unless you intend to store all personal files in another partition.

4. Now it is time to boot your Ubuntu install CD/DVD/USB drive and run ***gparted***.

5. Use the largest contiguous unallocated space of the drive for an extended partition.

6. Make a small swap partition. 1 GB is enough if you do not intend to hibernate. For hibernation you need as much as RAM (in Gibibytes, base 2 or 1024) if you want reliable hibernation).

7. Use the rest of the unallocated space for an ext4 partition to become the root partition of Ubuntu.

*Edit*: {
8. Run the installer and select ***Something else*** at the partitioning page, or use the[ One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") at the  advanced level.
}

---

### Post by jechadwell99 on 2014-01-31
One thing that came up was recovery media. Should I create a recovery cd?

Also, do you know how to access the HP_TOOLS partition? It does not appear in the windows explorer.

---

### Post by sudodus on 2014-01-31
Making a recovery CD is part of a good backup strategy :-)

You can also make a ***complete image*** of your present system (before you start editing the partitions). Clonezilla can do that, and it is possible to restore the system (exactly like it was) into the same or another disk with the same or larger size.

---

### Post by Bucky Ball on 2014-01-31
Create recovery cd(s) then you can safely delete that partition. I made the recovery cds on my HP (when it lived) and wiped the whole drive and started again.

You are going to need to create at least 20Gb of free space to install Ubuntu to, and that would be linking to personal data on an existing partition rather than keeping much in the Ubuntu partition. This is easy and we can show you how.

---

### Post by sudodus on 2014-01-31
HP_TOOLS should be available when you have booted from an Ubuntu install CD/DVD/USB drive.

---

### Post by jechadwell99 on 2014-01-31
Backing up files and stuff won't be necessary because this is a second hand computer and the contents don't mean much to me. However, the OS itself does, as there are several programs that are only under Windows.

---

### Post by sudodus on 2014-01-31
OK, the recovery disk will restore Windows to the factory defaults (I think). If you want to keep the installed programs and all tweaks, use Clonezilla.

---

### Post by jechadwell99 on 2014-01-31
So I can access the HP tools from the Ubuntu Live CD? Then I would just copy the contents to somewhere on the C: partition and then I can remove the HP_TOOLS, right?

Sorry, that I don't understand much. I've never done this before.

---

### Post by Bucky Ball on 2014-01-31
In that case, create the recovery disks, boot to Windows and defrag a few times then shrink that partition to small as is feasible (using Win software, NOT gparted) and wipe the rest of the drive, leaving it free space. 

Install Ubuntu. It needs about a 15-20Gb partition, /swap needs 2Gb or the size of your RAM if you hibernate. The rest of the free space could be used to create a data partition which you then link to from Ubuntu and Win meaning you are accessing the same data regardless of the OS and if something breaks, you can reinstall the OS without losing your data as it is on another partition.

---

### Post by sudodus on 2014-01-31
It is better to ask too many times than too few times :-P

Yes, according to my experience (about HP_TOOLS)

---

### Post by Mark Phelps on 2014-01-31
Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by jechadwell99 on 2014-01-31
I do not own an external hard drive and I would prefer not to have to buy one. Couldn't I use a windows repair disk and the hp system restore disks? There are no important files or tweaks to back up as this is a new computer. 

Also what do I do when I get to the manual partitioning screen?

---

### Post by Bucky Ball on 2014-01-31
Create the partitions / (20Gb and EXT4) and /swap ('swapfile', 2Gb or the size of your RAM if you hibernate). There are default mountpoints with those names in there. Make sure all other partitions are not ticked to format.

---

