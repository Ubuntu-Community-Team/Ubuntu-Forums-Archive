---
title: "The Incredible Shrinking Extended Partition"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by J. Random User on 2010-10-26
Okay, this is really weird.

I have been attempting to set up a bunch of partitions on a bunch of hard disks, in preparation for installing Maverick.  I will be setting up a number of RAID partitions, so I will install from the alternate disk (ubuntu-10.10-alternate-amd64.iso).

Now ever since they added support for GRUB2 and a new partition type and align-to-megabyte and a whole bunch of other goodness, partitioning has been buggy.  This has been true for Maverick and Lucid.  Even the 10.04.1 version (an Ubuntu LTS!) still has problems.  Every time I try something else, some other bizarre bug rears its ugly head.  (Yes, I have been reporting them on Launchpad when I find a new one.)

In order to move forward on this project, I have been using a variety of partitioning tools.  I temporarily installed Maverick on a small partition, and have used Disk Utility (palimpsest) and GParted while booted into that.  Occasionally when things get really strange I boot up the latest version of System Rescue Disk, which contains the latest version of gparted.  I use these various tools to try out various partitioning schemes, just laying out empty partitions that will be formatted or assembled into RAID arrays later.  When I get all the desired partitions set up, I will boot into the alternate installer and do the final installation.  (I don't want to do the entire thing within the alternate installer because it makes my head hurt.  I do have a *lot* of partitions.)

This has been going on for weeks now.  Every time I try something different, something weird happens, and I have to try various workarounds, or switch to different tools.  Basically, my partitions eventually become unstable.

Here's the latest mind boggler: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=173561&stc=1&d=1288125754[/IMG]
Disk Utility displays nice graphical maps of your partitions.  This image includes before and after screenshots showing what happens to my partitions occasionally.

We start with three primary partitions and one extended partition.  The extended partition goes all the way to the end of the disk.  We put a small logical partition into the extended partition, at the beginning of it.  We can then click on the "free" portion of the extended partition and create additional logical partitions if we like.

Afterwards, the extended partition has magically shrunk itself down until it is the same size as the small logical partition it contains.  The free space has migrated out of the extended partition, and is now useless, as you can't have more than four primary+extended partitions.  Disk Utility won't let you create another partition.

What happened between the Before and After pictures?  *I don't know.*

I do know that I did not ever tell any tool to change the size of any partition.  Moving or resizing partitions can trigger various known bugs, so I never even try to do that, I just delete partitions and start over.

I have created partitions about a kajillion times during this death march, using various tools, and I long ago gave up keeping a detailed log of what I have done, so I can't tell you what I did between the Before and After pictures.  All I know is, I went back the next day to check my progress, and found that an extended partition had mysteriously shrunk.

At first I thought that I had made a mistake, and inadvertently instructed a tool to make a small extended partition.  So I became extremely careful, and triple-checked, nay, *triple-dog-dare*-checked absolutely everything, every time I created any partition.  And sure enough, this happened again, *at least four times so far!*

I have two different brands of drives in this system, connected to two different controllers, and this problem doesn't seem to be specific to any of those, it's an equal opportunity bug.  One thing these drives all have in common:  They are all 500GB drives (horrors!  Don't get me started...).

Because I have been switching back and forth between various tools (all supposedly the latest versions), and trying various different arrangements, and stumbling over bugs and stopping to report them, and occasionally having a life, I cannot determine what is triggering this, at least so far.  It just seems to randomly happen.  If I had infinite time I could probably track it down, but I'm getting tired of this and need to get this system up and running.

So I don't know which tool is rearranging my partitions, and am therefore not inclined to report a bug yet.


So I put to you this question:   Have any of you seen this behavior before?

---

### Post by ronparent on 2010-10-26
The short answer is yes. I noted earlier on that the win 7 disk manage handle extended partition differently. Consequently although it is advisable to make unallocated space for an Ubuntu install available by using the win 7 disk manager to shrink the win7 partitions, all subsequent needed extended partition creation and manipulation should be done with gparted either with an installed system of from a live cd session.

---

### Post by J. Random User on 2010-10-26
> **ronparent said:**
> The short answer is yes. I noted earlier on that the win 7 disk manage handle extended partition differently. Consequently although it is advisable to make unallocated space for an Ubuntu install available by using the win 7 disk manager to shrink the win7 partitions, all subsequent needed extended partition creation and manipulation should be done with gparted either with an installed system of from a live cd session.

Interesting.

Of course we should have partitioning tools that can handle any kind of partition.  Obviously we don't yet.

Let me rephrase my question:

Has anybody seen this kind of behavior in a computer that has only been touched by Linux, and only really recent versions of Linux (like Maverick and SystemRescueCD 1.6.2, both of which are only a couple weeks old)?

---

### Post by srs5694 on 2010-10-27
I don't recall hearing of this specific thing happening, but I've heard of so many weird partitioning issues that I've forgotten most of them! I do know that libparted, which is at the core of many Linux partitioning tools, is a constantly changing mass of bugs; every time one is fixed, a new one takes its place.

If you're only using Linux, I recommend switching to the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning system, which eliminates the whole primary/extended/logical system; all GPT partitions are equivalent to MBR primary partitions, although the name "primary partition" is really meaningless under GPT. If you need to preserve existing data on the disk, you can use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert them without losing data (although you'll need to re-install your boot loader).

---

