---
title: "Partition Recommendation Needed"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by cprofitt on 2007-07-06
Hello:

I have searched and not found a topic that answered my specific question.

Scenario:

I have two SATA disks (250GB) each and one external 320gb drive.

I usually (windows OS days) installed the OS and applications (not games) on disk 1 and put all my games and documents on disk 2 and all my music on my external drive.

I am not familiar with the purpose of each of the Linux partitions so I am curious what the best way to partition the two internal disks would be.

Thanks.

---

### Post by moore.bryan on 2007-07-06
[I]there are endless choices.  most will suggest you have a separate partition for your /home folder.  the rationale is if something goes "funky" with the system, you can reinstall the system with your personal settings and documents secure.
my guess would be you could set-up one hd as root, one as /home, and the external for your music.  i'm not sure there's a guide for that... i'd check the forums/google again.
if i think of anything, i'll post back.
[/I]

---

### Post by Pumalite on 2007-07-06
I would suggest you install in one hardrive, preferably sda1 (or hda1); keep the other for data. In the one you install: 20GB for '/'; 1GB for /swap; the rest for /home. Format both with Gparted prior to installation ( ext3 ): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) The other drive ( for data or downloads ) you can mount from the console or at boot from /etc/fstab.

---

### Post by dabl on 2007-07-06
Yep, what Pumalite said.

Download and burn your GParted live CD and use that to set the partitions.  Use the Ubuntu Feisty Alternate Install CD to format, install, and mount the system.  Put your 3 required partitions (/, /{swap}, and /home) on one of the SATA drives, put /DATA (or whatever you want to call it) on the other SATA drive.  Don't try to install anything permanent on the external drive, unless you intend to keep it connected full time.  Just format it and put whatever folders you want on it.  :popcorn:

---

### Post by UnixAnt on 2007-07-06
Hmm, if you are just installing linux on these disks, would not a RAID 1 mirror (of the 2 250gb SATA drives) be worth considering?  Once the logical drive has been created, you could pretty much partition however you liked, safe in the knowledge that the resiliency was in place in case of a catastrophe.

Is this a feasible solution?

---

### Post by dabl on 2007-07-06
According to posts I've read, you can use mdadm to make a software RAID array.  Looks a little tricky -- not sure it's the best way for a noob to start out with Linux.  But yeah, I think it's possible.  Personally, with the reliability of the new SATA drives, I'd go for RAID 0 striping (for performance) rather than mirroring (for security).  Just one fool's opinion ...

\\:D/

---

### Post by UnixAnt on 2007-07-06
Yes - that's the debate I suppose.  Do you want maximum performance and no resiliency?  Or reasonable performance with the loss of one drive but the means to survive a disk failure?  I suppose its personal preference.

The system I am putting together at the moment is most probably going to consist of 2 36Gb Raptors running in RAID 1 (Mirroring) configuration, with all my data being held on a RAID 5 desktop NAS.

I'm not sure how difficult it would be for somebody new to Linux to set up RAID either - but I imagine the on-board hardware would take care of the initial striping, leaving you with 1 logical drive.  From there, the installer would take care of the rest.

This is one of those posts which strikes a nerve with me, as for years I used up to 4 external USB drives, with data scattered all over the place, scripts set up to rsync each night, etc, etc and in the end I just had one big mess of disorganised data.

Taking the time to think about partitioning and system setup from the offset is sure to pay dividends.

---

### Post by dabl on 2007-07-06
> **UnixAnt said:**
>  I imagine the on-board hardware would take care of the initial striping

Actually, I _think_ that is wrong -- what I read on the forums suggests that these RAID hardware controllers have no Linux drivers available, which will force you to use the software RAID method via mdadm.

>  Taking the time to think about partitioning and system setup from the offset is sure to pay dividends. Truer words were never written! :popcorn:

---

### Post by UnixAnt on 2007-07-06
> **dabl said:**
> Actually, I _think_ that is wrong -- what I read on the forums suggests that these RAID hardware controllers have no Linux drivers available, which will force you to use the software RAID method via mdadm.

Oh really?  I must admit I really don't know for sure :p

I've never even used SATA drives (I'm a SCSI man), to my eternal embarrassment, so I just assumed you pressed some magical key combination at the initial POST screen, and it took you into a utility where you can configure the RAID array, like you can on a high-end SCSI RAID system (which is pretty much where all my exposure to RAID comes from).  After that, you would reboot the system and enter the Ubuntu installer (or whichever distro) and it would see 1 logical drive in RAID formation.

However, if its FRAID (fake RAID) only controllable by software, then I would scrap the RAID idea altogether, because that's just craziness :o

Thanks for the info :D

---

### Post by t4thfavor on 2007-07-06
I just got 4x500Gb seagate drives and a primise raid controller that supports linux. I push some magical key combo at boot and then set up my raid and then it just works.

My BOSS wants me to make our NAS unit run Windows 2k3 server, though if it were my dime it would almost certainly be an ubuntu box.

I will be installing the w2k server tomorrow so I will let you know how it works out. (if its harder/easier to install drivers aside.)

For now I am just playing around.

As for the quantity of drives, I wanted a 5x drive array (one for parity), but he only wanted to have to buy one controller (promise says that two will work together in the same box)

---

### Post by cprofitt on 2007-07-07
> **UnixAnt said:**
> Hmm, if you are just installing linux on these disks, would not a RAID 1 mirror (of the 2 250gb SATA drives) be worth considering?  Once the logical drive has been created, you could pretty much partition however you liked, safe in the knowledge that the resiliency was in place in case of a catastrophe.

Is this a feasible solution?

If I thought Raid was needed I would go with at least three disks so I could use Raid 5, but I have no such need - I was more looking for how to force the /home to the other disk and have the OS know that its there. My experience with Ubuntu installs to this point has been with single disk laptops.

The only case I would use Raid 1 would be to mirror the system partion (OS) but for data I would always perfer Raid 5 with an Hot Swap Spare.

---

