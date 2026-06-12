---
title: "Installing 10.04 on Asus 1215N; Drive Partioning"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by TrendRat on 2010-10-10
I want to install 10.04 on my netbook alongside Win7.  I have 10.04 on a USB stick, and Ubuntu is booting up in demo mode.  This is all good.  But when I get to picking the location for the installation, I only have two options: 1)erase everything on the drive, and 2)an advanced option that requires me to manually partion the drive.  

There is no option to "Install alongside other operating system, you mama's-boy moron with no knowledge of Ubuntu" (like it says there is in the instructions). ](*,)  If it was there, I would happily admit my Ubuntu shortcomings and click on it.  But it's not - and it's been to many years since I did a manual partion. Can someone tell me what I am doing wrong, or point me to the basic partitioning primer?

---

### Post by TrendRat on 2010-10-11
I've been reviewing the posts here and have found several related to the issue I am having.  One reply had a comment:  "If you have only one hard drive with 4 existing partitions on it, you have a lot of work ahead of you to install Ubuntu".

My Asus 1215N has one hard drive with four partitions.  One has Windows 7, one has something to do with Windows Vista, I think one has the Asus version of Linux on it (I think, can't confirm), and the content of the fourth is unknown.

Am I going to have to wipe this drive, repartition, re-install Win7, then install Ubuntu?

---

### Post by TrendRat on 2010-10-11
Found a solution after digging a bit and trying a few things.  For the sake of others that are running into the same problems, I'll post my experience.  Although I'm fairly proficient with computers, they are not the center of my life - I use them as a tool, so I am often unfamiliar with the finer points of the technology I use.  Hence my struggle with what many of you might consider basic stuff.

After reading the comment about having 4 primary partitions, I went into "Win7 - Manage Computer - Disk Management" and deleted two of the partitions, leaving me with two.  I checked first and these were empty partitions, lucky for me, and I could do this without wreaking havoc on Win7.

Then I booted up using LiveUSB Ubuntu Netbook 10.1 and selected "Install Ubuntu".  This time, when I got to step 4, there was an option that said "Install alongside other operating system".  Accomplishment #1.

Ubuntu wanted to shrink my Win7 partition (which I didn't want), so I had to go in and manually partition.  I was struggling with this a bit, as I kept trying to assign the free space to a primary partition, and Ubuntu didn't want me to do this.  I finally figured out that I could set up a swap, root, and home using the unassigned free space if I selected "Logical" partition, and did so.  Accomplishment #2.

It is now loading files - fingers crossed.  I told it to put the boot loader on the Win7 boot section - I hope this is correct, otherwise I may be in deep doo-doo.

Cheers,
Stumbling Thru Ubuntu with Good Intentions  :-\"

---

### Post by TrendRat on 2010-10-11
Accomplishment #3.  It finished loading the files, I rebooted, the boot loader came up allowing me to select Ubuntu or Win7, and now I'm playing in Ubuntu.

---

### Post by Mark Phelps on 2010-10-12
I'm presuming your Netboot came with Win7 preinstalled, right?

SO, did you go ahead and remove the Recovery partition? OR is it still there?

If you removed it, it's likely NOW that you will have no way to restore Win7 later because that partition contained the image file you would need to do such a restore.

Just letting you know in case you come back later asking how to restore your machine to its original state.

---

### Post by TrendRat on 2010-10-12
Not an issue.  I made an image of the entire Netbook drive prior to messing with partitions.  Also made a recovery USB flashdrive using the Asus recovery utility.

---

### Post by nilbot on 2010-10-13
ah. Thanks for the shared experiences. tooo bad I don't have a USB drive big enough to backup the recovery data. The only external storage I have is a NAS 1 TB drive.

can you confirm that if you have lost the recovery menu aka F9 function after deleting the partitions?

right now I'm looking into these 2 mysterious hidden partition that come with asus 1215n. I think they didn't installed the main bootloader at the beginning of the win7 partition. if that can be confirmed, we might have to find an alternative to safely backup the boot sector.

---

### Post by TrendRat on 2010-10-13
> **nilbot said:**
> can you confirm that if you have lost the recovery menu aka F9 function after deleting the partitions?
Yes, that is correct.  It seemed pretty silly to me to have the recovery files on the same hard drive as the operating system, even if it is on a different partition.  So my goal was to set things up so that I could recover from a system crash by using external peripherals like the USB Recovery flashdrive (which is no longer effective since F9 doesn't work) and an external usb CD/DVD drive (which I used to create a Windows Repair Disc), and the image backup to an external hard drive.  I really need to get a DVD of my Win7 OS from Asus, which I am in the process of investigating.

They sell these netbooks cheap, but they really don't come equipped to deal with a serious crash.  You need several USB sticks, an external hard drive, and an external CD/DVD drive in my opinion.  I'm lucky I have this stuff laying around.

> right now I'm looking into these 2 mysterious hidden partition that come with asus 1215n. I think they didn't installed the main bootloader at the beginning of the win7 partition. if that can be confirmed, we might have to find an alternative to safely backup the boot sector.
I can't definitively identify them; I made a few semi-educated guesses and I'm probably lucky I didn't do any permanent damage.  When I installed Ubuntu I selected the primary drive for the boot loader, and it worked.

Let us know how yours turns out.

---

### Post by ch3rryc0ke on 2010-12-06
Hey TrendRat,

I'm running into an issue with my 1215N that I'm wondering if you came across.

I used wubi to install, and then after running updates I accidentally installed GRUB, which I believe overwrote the existing bootloader.

Now I can't boot into either OS, and the F9 functionality doesn't work to restore the system.

Do you know how I can reinstall the stock bootloader?

---

### Post by booyootoo on 2011-01-15
If you have overwritten your bootloader, the new bootloader should still see all the partitions (unless you have also removed those).

If you see a partition that says vista something, that is the restore partition. I did not try a complete restore, but did try to enter the restore mode and it asked my if I was sure to restore the system. For me it was not necessary, so I exited.

But I'm sure all will end up in the state you bought the netbook.

---

