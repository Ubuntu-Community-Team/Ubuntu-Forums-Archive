---
title: "Installing Ubuntu 9.10: Too many primary partitions"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Xtof on 2010-03-09
Hi all,

Sorry if this topic has already been adressed, and I'am sure it has...but I found no answer by googling.

I just baught a new PC, a Packard Bell iextreme.

1 TB hard disk, proc i5-750.

I wanted to install the Ubuntu 9.10 but it was not possible since according to the Ubuntu partitioner or even GParted, I have already 4 primary partitions:

1) sda1: A misterious 1 MB partition
2) sda2: The 15 GB recovery partition
3) sda3: 100MB partition reserved to system
4) sda4: C: with Windows 7
5) some unallocated space where I want to install the Ubuntu

I went back to Windows 7 and according to the disk manager, there is no such sda1 1MB partition; it just shows the 15 GB recovery partition, the 100 MB partition and the C: plus the free space, that is 3 primary partitions. So in principle I should be able to use the unallocated space to create an extended partition. But Gparted or Ubuntu detect this small partition and count it as primary, reaching the maximum allowed primary partitions.

- What is this small 1 MB partition ?
- How do I proceed to install the Ubuntu if I already have 4 primary partitions ?
- Can I convert the C: into an extended partition in which I could create logical partitions ? Would it delete my Operating System ?
- Can I delete the 15GB recovery partitions ? I already have burnt the DVD recovery in case...

Thanks in advance for any idea.
Xtof

---

### Post by Cabs21 on 2010-03-09
I think (but could be wrong) that the 1 MB primary is your BIOS and system info.  I would recommend looking into it deeper to better understand what it is.  See if you can contact the manufacture and ask why or what that partition is for or is.

Didn't see that you had copied the recovery to a disc.  I would drop the recovery partition and maybe make it 20 to 30 GB in size.  Ubuntu can also help, if win7 crashes on you, to recover and fix things in windows.

---

### Post by Xtof on 2010-03-10
Hi,

Thanks for your answer. Yes, the first thing I did was to burn the recovery to DVDs. One never knows ;-) !! So in principle, I could delete the recovery partition. In case something goes wrong, I could use the DVD recovery to restore the system. But I must confess I am a bit afraid of this solution...Could I lose the warranty if I delete this recovery partition ?

What is weird is that W7 does not show this 1 MB partition but Ubuntu detects it as a primary partition. Actually, in W7 I can even create another partition without any problem.

We'll see...

Ciao
Xtof


> **Cabs21 said:**
> I think (but could be wrong) that the 1 MB primary is your BIOS and system info.  I would recommend looking into it deeper to better understand what it is.  See if you can contact the manufacture and ask why or what that partition is for or is.

Didn't see that you had copied the recovery to a disc.  I would drop the recovery partition and maybe make it 20 to 30 GB in size.  Ubuntu can also help, if win7 crashes on you, to recover and fix things in windows.

---

### Post by Mark Phelps on 2010-03-10
Given your list > **Xtof said:**
> I have already 4 primary partitions:
1) sda1: A misterious 1 MB partition
2) sda2: The 15 GB recovery partition
3) sda3: 100MB partition reserved to system
4) sda4: C: with Windows 7
5) some unallocated space where I want to install the Ubuntu

You have a really tough problem to solve.  

This partitioning scheme seems to be very popular on recent Dells.  It's almost as if Dell is doing this INTENTIONALLY, to thwart folks from installing "another OS" on their machines.

Also, since the vendor gets to set the terms of the warranty, not the purchaser, I wouldn't be surprised if ANY changes to the OS and/or partition scheme on this machine end up voiding the warranty.  To know for sure, you would have to obtain and read -- and understand -- every single clause in the warranty.  And, unless you're a lawyer, the "understand" part is going to be a real challenge.

OK, some points to consider ...

1. If you delete the recovery partition, and your MBR is set to boot from the third partition, it might no long boot-- because your third partition would then be the unbootable Win7 partition.

2. If you leave the partition structure as is, even if you shrink the Win7 "C" partition to make room (something you should use the Disk Management utility in Win7 to do), you will still have 4 primary partitions.  Win7 won't run from an Extended partition, so changing that won't solve your problem.

So, first thing I would do is to use the Win7 backup utility to create and burn a Win7 Repair CD.  You might need that later to restore Win7 boot, or to use it to restore from backup.

Second, I would make a full image backup of your drive -- ALL the partitions.  You didn't say how big your drive is, but external 1TB drives are available in the ~$100 range these days.

Barring that, at least make a backup of your Win7 "C" drive -- so that you can restore that if needed.

Now that you have a restorable image and something to boot from, you can experiment as follows:
1) Remove the recovery partition
2) Move the System partition to the left to take up some of the new free space
3) Shrink the "C" partition to make some room, and move it to the left

Note: do these using the Win7 Disk Management utility -- and yes, you can to that to a partition from inside Win7 -- it will reboot to perform the partition changes.

Now that you have space, create an Extended partition and use it to install Ubuntu.

---

### Post by Xtof on 2010-03-10
Hi Mark,

Looks like an impossible mission, right ;-) ?!

I also wonder if they do that intentionaly to avoid people to install another OS. I sent an email to Packard Bell support, to ask about the hidden small partition. The guy just told me that they don't give support to installation of other OS and did not give me any information about the partition. I sent an email back to ask again about this small hidden partition.


I am also thinking of removing the recovery partition. I already burnt off the data to 3 DVDs. In principle I could do that, but as you say, what about warranty ?

The point is that Windows 7 only sees 3 partitions. So in principle, if I had a tool like Partition Magic, I should be able to create an extended partition. But unfortunately impossible to download one for free that could do the job.

I think the best solution is to buy a second hdd of 500 GB. How much could it cost ? 50 $ ? Not big deal.

Thanks again for your answer.
Xtof


> **Mark Phelps said:**
> Given your list 
You have a really tough problem to solve.  

This partitioning scheme seems to be very popular on recent Dells.  It's almost as if Dell is doing this INTENTIONALLY, to thwart folks from installing "another OS" on their machines.

Also, since the vendor gets to set the terms of the warranty, not the purchaser, I wouldn't be surprised if ANY changes to the OS and/or partition scheme on this machine end up voiding the warranty.  To know for sure, you would have to obtain and read -- and understand -- every single clause in the warranty.  And, unless you're a lawyer, the "understand" part is going to be a real challenge.

OK, some points to consider ...

1. If you delete the recovery partition, and your MBR is set to boot from the third partition, it might no long boot-- because your third partition would then be the unbootable Win7 partition.

2. If you leave the partition structure as is, even if you shrink the Win7 "C" partition to make room (something you should use the Disk Management utility in Win7 to do), you will still have 4 primary partitions.  Win7 won't run from an Extended partition, so changing that won't solve your problem.

So, first thing I would do is to use the Win7 backup utility to create and burn a Win7 Repair CD.  You might need that later to restore Win7 boot, or to use it to restore from backup.

Second, I would make a full image backup of your drive -- ALL the partitions.  You didn't say how big your drive is, but external 1TB drives are available in the ~$100 range these days.

Barring that, at least make a backup of your Win7 "C" drive -- so that you can restore that if needed.

Now that you have a restorable image and something to boot from, you can experiment as follows:
1) Remove the recovery partition
2) Move the System partition to the left to take up some of the new free space
3) Shrink the "C" partition to make some room, and move it to the left

Note: do these using the Win7 Disk Management utility -- and yes, you can to that to a partition from inside Win7 -- it will reboot to perform the partition changes.

Now that you have space, create an Extended partition and use it to install Ubuntu.

---

### Post by Xtof on 2010-03-14
Problem soved...

I asked Packard Bell to tell me what is this small hidden partition at the beggining...but still waiting for their answer !! I asked them what would happen if I deleted the 15 GB recovery partition...still waiting for their anwer !
Since I did not want to mess up my brand new PC and neither did I want to void the warranty, I simply bought a second SATA hdd. I installed the Ubuntu 9.10 64 bits on it and that's it. As simple as that.

Thanks for your help again.
Xtof

---

### Post by phillw on 2010-03-14
You were very nice to them :D

If I had bought a computer with a 1TB drive and found the manufacturer had used all the primary partitions I would have quoting their "we do not support other systems" equalling "we do not allow you to put on other systems" to say that the machine was unfit for the purpose it was bought.

Especially as you have free space on your 1TB hard-drive, it's quite obvious they do not know how to set up partitions !!!

If you're interested from your Ubuntu installation
```

sudo fdisk -l
``` That's a little 'L' not a number one

will tell you which is the boot partition on your hard drive (It will have a little * under the column boot)

Regards,

Phill.

---

### Post by srs5694 on 2010-03-14
The "fdisk -l" command will also help identify the mystery partition. It should have a partition type code, and hopefully a short interpretation of what that means.

Aside from that mystery partition, many recent Windows systems have three primary partitions, all of which you've got (not necessarily in this order):


[list=1]
[*]A type-0x27 ("Windows Recovery Environment") partition that holds some files to help Windows recover from problems, and perhaps to help it boot. I'm a bit foggy about the details.
[*]A type-0x07 ("HPFS/NTFS") partition that holds the main Windows installation (C: in Windows).
[*]A type-0x07 ("HPFS/NTFS") partition that holds the equivalent of the Windows installation/recovery DVD. For a recent Windows 7 laptop I bought, this was about 9GB in size, IIRC.
[/list]


There's usually a utility buried somewhere on the computer that will copy the contents of that partition #3 (#3 in the above list, not necessarily on the disk) to DVDs. The utility is called "create recovery discs" or some such thing, and it doesn't make it clear that it's copying the contents of a separate partition onto DVDs.

This partition is essentially a way to enable manufacturers to shave a few cents off the cost of their computers, since they can then omit a real recovery DVD. If you really need the partition, you can create the recovery DVDs (I recommend making two copies in case a DVD goes bad) and then safely delete the original partition. While you're burning the DVDs, rather than twiddle your thumbs, you can write a letter to the computer manufacturer (with a cc: to Microsoft) telling them what you think of their being so cheap as to do this. They'll keep doing it unless enough people complain.

Depending on how it's installed, the type-0x27 partition isn't required by Windows, either, so you may be able to get rid of it by re-installing Windows. You'll need to re-install to a disk that's pre-partitioned *without* that partition. I can't guarantee that all recovery/installation discs support this, though.

---

### Post by Mark Phelps on 2010-03-14
> **Xtof said:**
> Problem soved...

Personally, I think you made the right choice.  

Rather than muck around with all those partitions, hidden and otherwise, and run the risk of trashing the setup bigtime, you spend a few dollars and added a second drive.  (My same choice, by the way)

Happy Ubuntu-ing!

---

### Post by TutAmongUs on 2010-03-14
> **Mark Phelps said:**
> Personally, I think you made the right choice.  

Rather than muck around with all those partitions, hidden and otherwise, and run the risk of trashing the setup bigtime, you spend a few dollars and added a second drive.  (My same choice, by the way)

Happy Ubuntu-ing!

  I can see 500 optical discs and about ten hard drives from my living room/office chair.

  Most recent DL's:  Ubuntu for the PS3, both desktop and alternate.:popcorn:

---

