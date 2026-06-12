---
title: "dual booting on Acer X1420"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2012-01-25
I have dual booted WinXP many times, with no problem, but I recall doing it on a laptop with Vista pre-installed, and after ubuntu had written to the MBR, the hidden system restore partition became inaccessible. All the dual-booting HOWTOs that I can find just seem to focus on the simple WinXP example, starting from a single disk partition.

I now have a new Acer X1420 desktop 64bit system, with a pre-installed Windows 7, where you create your own system restore CDs as a first task - which can see and access two partitions: C:/ contains Win7, size 491GB, and an empty data partition is at D:/ - size 491GB  -- just begging to have ubuntu installed ;)

However, the Ubuntu install disk sees 4 partitions:

/dev/sda1 NTFS 19GB PQSERVICE
/dev/sda2 NTFS 105MB SYSTEM RESERVED
/dev/sda3 NTFS 491GB ACER  -- I am guessing this is Win7
/dev/sda4 NTFS 491GB DATA

I'd be grateful for advice as to options for running ubuntu in /dev/sda4, without the system losing access to the system restore facility.

Thanks in anticipation
Alan

---

### Post by Mark Phelps on 2012-01-26
The only way you can install Ubuntu to an NTFS partition is using Wubi -- which I personally do not recommend.

To install Ubuntu to its own partition, you would have to do the following:
1) Remove the "D" partition -- as 4 Primary partitions is the maximum, and creating another puts you over the limit.\
2) Create an Extended partition in the free space
3) Boot from the Ubuntu media and using "Something Else", do manual partitioning and install to the Extended partition.

However, BEFORE you do that, I strongly recommend you use the Win7 Backup feature to create and burn a Win7 Repair CD.  You may need that later if something goes wrong during the dual-boot setup and you can't boot back into Win7.

---

### Post by alpage2 on 2012-01-26
Thanks Mark - I hadn't thought about the limit on the number of primary partitions ;)

However - I think the process you outlined will write the changes to the MBR? - and based on my previous experience with a vista laptop, this risks losing access to the restore system.

Before sacrificing the restore system, I just wondered if there was a way in which ubuntu could be installed and run from /dev/sda4, without writing to the MBR?  Maybe not if the partitions will need modifying to avoid exceeding 4 primary partitions?

Thanks
Alan

---

### Post by Mark Phelps on 2012-01-27
Alan:

The response to your latest question is the first item in my first post -- using Wubi.  That is the ONLY way to install Ubuntu without partitioning.  And, as I said, I don't recommend it.

If you're concerned about losing the capability to Restore your Win7 install in the future, let me suggest an alternative approach:
1) Download and install the FREE version of Macrium Reflect
2) Use MR to image off your Win7 install to an external drive
3) Use the MR option to create and burn a Linux Boot CD.
NOW, you have the capability to restore Win7 from your backup -- you don't need the recovery partition or feature anymore.

IF you're going to remove the last NTFS partition and use that space for Ubuntu, do the steps above before you do the Ubuntu install and use the Win7 Disk Management tool to remove the NTFS data partition.

If you remove the Recovery partition and THEN want to install Ubuntu in a new partition, suggest you use the Free Partition Wizard Boot CD to do the following:
1) Boot from that CD
2) Remove the Recovery partition
3) Move all the remaining partitions to the left
4) Shrink down the last (data) partition to make some room

Then, boot from the Ubuntu CD and use the "something else" option to install it.

---

### Post by alpage2 on 2012-01-27
Thanks Mark

That's great - certainly gives me some options, and all the details are very helpful.

Thanks again
Alan

---

### Post by bob-linux-user on 2012-02-08
@Mark Phelps
I have a similar issue, having just bought the X1420, so I am gratefully reading your post. What are the downsides to using Wubi as you see it please?

Is it speed- I understand ubuntu runs slightly slower?

Stability? If windows packs up then I suppose it takes down Ubuntu with it?

Ease of installing a later distro? How easy is it to install (for example) Ubuntu 12.04 over 11.10. Can you just run wubi again?

Anything else?

---

### Post by alpage2 on 2012-02-09
bob-linux-user  --  I have never used wubi, so can't tell you much. The wikipedia article says a bit more about the limitations than I could find in the ubuntu documentation:

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)

It does seem to me to expose ubuntu to some of the limitations of windows kind of defeats the object ;)

I think it was only intended as a 'safe' way to introduce ubuntu to windows users who don't have the knowledge/confidence to do a hard drive install - or dare I say it, for windows users with newer machines who are reluctant to lose their pre-installed windows restore features  :)

I'm sure Mark can tell you more.

Alan

---

### Post by bob-linux-user on 2012-02-09
Thanks Alapge2. The wiki on wubi (!) confirmed pretty much what I had read already. This is the first new PC I have bought for about 15 years and I would have preferred to have bought it without a preinstalled OS at all, but it was a good price even with the Windows 7 already on it. I have done many installs/repartions etc on my older computers but, (as you guessed) I am reluctant to mess about with this new one more than necessary. I don't like Windows 7 but I paid for it and might as well keep it.

---

### Post by bob-linux-user on 2012-02-26
Here is how I got on installing on my Acer X1420 (which has a bigger hard drive than the original OP)

Running from the install CD (64 bit version) I changed the folders as follows using Gparted:-

BEFORE

Ubuntu	 Gig Windows
------   --- -------
sda1	 016 Healthy recovery partition
sda2	 100 System Preserved
sda3	 915 C drive Programs and files 
    	----	
	1031 TOTAL


AFTER

Ubuntu	 Gig Windows
------   --- -------
sda1	 016 Healthy recovery partition
sda2	 100 System Preserved
sda3	 377 C drive Programs and files 
sda4 extended
 sda5	 530 Healthy Primary Partition (for Ubuntu)
 sda6	 008 Primary Partition (for linux swap)
    	----	
	1031 TOTAL

CAUTION: Backup everything first

I split the sda3 (Windows C drive) and formed a new extended partition sda4 that I then further split so I have a partition for installing ubuntu and a swap partition.

When I installed ubuntu from the live cd I used the "something else" option so I had complete control over what was going on and installed to sda 5 with sda6 as swap.

When I rebooted I had the following message from my monitor, "out of range" or similar. At this point I very rashly assumed I had totally wrecked the computer and reinstalled windows back to factory settings. I reinstalled ubuntu again and had the same problem. BUT this time I let the pc carry on and ubuntu appears. I looged on and :-
1) Installed startup manager from software centre and set the grub screen to 800x600 resolution.This stops the "out of range" problem
2) DEinstalled the NVIDIA drivers and went back to the generic driver. This stops the pc logging out of lightdm when booting up- a problem others have reported with Nvidia drivers.(Later on I set the DPI of the screen to 80 (96 is default) to partly compensate.)

Reboot.

CAUTION
I recall when I first had the computer that windows showed a Q drive which had (i thought rather oddly) the setup files for MS Office 2010 Starter. This was missing later, I think it went missing during the Windows reinstall I did (see above) As MS Off Starter 2010 doesn't look like worth getting out of bed for I was not bothered by this.

I hope this helps someone.

---

### Post by alpage2 on 2012-02-26
Thanks for the details, bob-linux-user.

So now that linux is installed, does the original windows restore system function normally, if it were to be needed again?

Alan

---

### Post by bob-linux-user on 2012-02-26
Hello Alan

I assume the Windows restore would work, or if you were in any doubt you could create all the restore discs again.

As far as I can tell everything is working normally- a full dual boot system where you choose at the beginning using grub.

I am actually running a recent download of ubuntu 12.04 with the xfce, that is, xubuntu desktop. All seems very stable for a pre release.

Regards

Bob

---

### Post by darkod on 2012-02-26
I see this is marked as Solved, but to add few words.

In most cases you shouldn't worry about the restore partition because usually they have boot files on them too.
Ubuntu discovers all boot files and makes an entry in the boot menu for all of them. So don't be surprised if you see:
win7
win7 (which is your restore, or it may say win vista depending how the boot files are detected)

Also, you shouldn't test the partition without any need because part of the restore process might start even before you confirm you want the restore done, and the MBR can get overwritten even if you say No to the restore when it asks you.

Wubi was always meant as a quick try only. In lots of cases simple updates or upgrade to the next version can break it. The developer himself stated that he never planned it as long term install and the development doesn't take that into account. Which doesn't mean it can't run a long time without any problem. Depends... Also, of course, if windows packs up, there goes wubi too.

---

### Post by bob-linux-user on 2012-02-27
Just reading the last entry on this subject. I did not mean to suggest that restoring from a backup of windows was a good idea, what I meant was, create the backup discs from windows, so you are reassured that if anything goes wrong in future you can restore the PC.

Personally I attach a lot more importance to backing up my personal data.

Note that I did not invent any of the solutions in my post, just found them elsewhere, they are other people's work.

---

