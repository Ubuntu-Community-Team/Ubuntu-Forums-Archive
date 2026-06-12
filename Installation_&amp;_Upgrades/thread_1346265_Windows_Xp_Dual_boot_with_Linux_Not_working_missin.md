---
title: "Windows Xp Dual boot with Linux? Not working missing hard drive...!"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by earfer on 2009-12-04
Hey everyone,

I have a Laptop and the main or original os is a vista. I installed ubuntu on the entire disk and now i want to dual boot it with windows xp home edition sp0.

The problem is, is that windows xp cant find any hard drive on my laptop...
I had a search around and it said something about SATA hard drive and not letting xp install. so i was wondering if anyone could help out? 

I followed this guide but i rly dont get wha tit said when it got to about selecting .inf on drivers so i rly need help~!

Thanks in advance...

---

### Post by jitup on 2009-12-04
there is probably a better way of doing this but this is how I would go about it. Backup all the stuff you care about, reformat your hd. install xp, let it create the partition. install ubuntu 9.10, specify how much of the hd you want partioned, do not format the partion xp is on. make sure grub installs, and BAM! dual boot. like I said, there is probably a better way of doing it you dont want to back your stuff up, but I always felt that a fresh install only makes things run smoother, especially in windows about every  year and a half ta two.

---

### Post by u.b.u.n.t.u on 2009-12-04
> **earfer said:**
> I installed ubuntu on the entire disk and now i want to dual boot it with windows xp home edition sp0.

Windows, XP in this case, needs to be installed first. After Windows is installed (eg 7, Vista, XP), then install linux (eg Ubuntu).

The reason for this is that linux will create a valid boot loader and Windows will not. That means you will not be able to start an operating system if you install Windows where Linux is.

> **earfer said:**
> The problem is, is that windows xp cant find any hard drive on my laptop...

Windows is an ignorant operating system when it comes to linux. Only with some effort can it read Ext2 and Ext3 file systems and the new Ext4 file system used by Ubuntu 9.10 cannot be read at all at this time.

As jitup essentially said, backup your data and reinstall. Windows XP first and then Ubuntu 9.10 (or which ever version you were wishing to use).

---

### Post by earfer on 2009-12-04
Thanks for the reply,

Yes that is the best way ever~! But...

Windows Xp Home won't install no matter what. I wont find the hard drive on the computer~! There is a way to make it find it but i cant do it bacuse i rly dont get it.
So i was hoping some one can explain further for me.

But if i could do that i would by far long ago :D

---

### Post by u.b.u.n.t.u on 2009-12-04
If the HDD is using a linux file system then that is likely the cause. During the XP install, choose the option to format the HDD to NTFS and it will become visible again.

**Back up all important data before proceeding.**

---

### Post by garvinrick4 on 2009-12-04
You have already formatted your drive in NTFS and XP cannot see your drive? I imagine
your whole drive was ext3 before you formatted. Something sounds like XP is looking at
ext3 instead of NTFS.

---

### Post by earfer on 2009-12-04
i made another partition that is unallocated. shouldnt it see that? or do i have to make it ntfs?

---

### Post by u.b.u.n.t.u on 2009-12-04
> **earfer said:**
> i made another partition that is unallocated. shouldnt it see that? or do i have to make it ntfs?

1. Backup and verify important data.

2. Install XP, doing a quick format to NTFS.

3. Check that XP works, start it, shut it down.

4. Install Ubuntu 9.10.

This will save you time and effort.

---

### Post by earfer on 2009-12-04
true. but then i have to re download the updates and re configure the whole enitre ubuntu  again. or is there a software that can save every single info or settings?

---

### Post by u.b.u.n.t.u on 2009-12-04
> **earfer said:**
> true. but then i have to re download the updates and re configure the whole enitre ubuntu  again. or is there a software that can save every single info or settings?


There is the **_hard way_**. You can create a partition, format it to NTFS, install XP and then try to edit the necessary files to have XP working.

Sure, if you want to try that. I never bothered for the reasons I have already made clear. It isn't easy.

Windows gives no consideration to Linux. Conversely Linux gives every consideration to Windows.

Your call.

UPDATE

You can back up your settings you know and then reapply them!  eg /home   /etc    /usr/local

Here is a good read on the topic.
[https://help.ubuntu.com/community/BackupYourSystem#BackupPC](https://help.ubuntu.com/community/BackupYourSystem#BackupPC)

---

### Post by earfer on 2009-12-04
> **u.b.u.n.t.u said:**
> There is the **_hard way_**. You can create a partition, format it to NTFS, install XP and then try to edit the necessary files to have XP working.

Sure, if you want to try that. I never bothered for the reasons I have already made clear. It isn't easy.

Windows gives no consideration to Linux. Conversely Linux gives every consideration to Windows.

Your call.

aha ok thanks a lot then~

---

### Post by u.b.u.n.t.u on 2009-12-04
* from the previous page.


UPDATE

You can back up your settings you know and then reapply them!  eg /home   /etc    /usr/local

Here is a good read on the topic.
[https://help.ubuntu.com/community/BackupYourSystem#BackupPC](https://help.ubuntu.com/community/BackupYourSystem#BackupPC)

---

### Post by earfer on 2009-12-05
- Delete -

---

### Post by Bartender on 2009-12-05
I'm not sure if anyone gave the OP some ideas for getting Windows to boot?

If it were me I'd get out a GPartedLiveCD.  Link to get you started under my sig - you make a bootable CD out of the download just like you would an Ubuntu CD.  Download and burn the latest stable version.

So you boot from the GPartedLiveCD (GPLCD) and delete all partitions.  Then create a primary partition, formatted as NTFS, for Windows out of half of the drive, or all of the drive, or whatever space you want.  Apply the changes.  The idea here is to create an NTFS partition that Windows will recognize and install to.

Get out of your GPLCD, pop in your Windows CD, it'll recognize the NTFS partition, install to just that partition.  The rest of the drive is then ready for Ubuntu install.

---

