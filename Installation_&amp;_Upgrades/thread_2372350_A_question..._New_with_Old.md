---
title: "A question... New with Old"
date: 2017-09-24
forum: Installation &amp; Upgrades
---

### Post by rubberduck1968 on 2017-09-24
Hi all,

New system and hardware, running with old hardware.

Having been a Linux disto user for some seven years now and being capable of getting around a Ubuntu/Kubuntu OS system, I thinking about upgrading my OS but installing on to a new SSD drive but keep the old 1TB disk drive. Once new OS is up and running, use the new SSD drive to boot from and keep all my files on the 1TB drive. But then remove the 14.04 root files and drivers from the old 1TB drive, leaving my photography, music and other files behind and using the TB drive for storage. 
The idea being that I could get the new OS running on the new SSD separately, set up to how I want it leaving the old 14.04 running, without having to format the old 1TB drive and reinstate all my files from back up drive and disks after the change over.

Has anyone done this, and was it successful?

Cheers.

---

### Post by Bucky Ball on 2017-09-24
Just to get this straight ...

[LIST=1]
[*]You want to install 16.04 LTS to a brand new SSD.
[*]You want to leave the 14.04 install and you data files on the HDD untouched, exactly as is.
[*]You want to remove the 14.04 LTS install from the HDD once you are sure the SSD install is running.
[/LIST]
Please confirm the above and if I've got it right, then yes, done a million times so yes, can be done. Nothing unusual about this.

You could start by sticking in the SSD and installing 16.04 LTS on it. If you want to be ultra-safe, unplug the HDD so you don't get confused and wipe the lot (although you should always keep good backups, anyway). Once you know you have the SSD install working without issue, plug in the HDD and let us know if you get that far.

* Just a note, and might not be relevant to you: if you have Windows installed, is it installed in UEFI or legacy mode? It matters as whatever mode that is in, Ubuntu should be installed in the same mode. Also, if you are wanting to boot the other 14.04 LTS (which will not be necessary as you'll be able to access its files from the 16.04 install, but if it is) then same applies. Install them both in the same mode.

You can check and select in the BIOS. Good luck.

---

### Post by TheFu on 2017-09-24
Yep. Pretty easy.  After you get 16.04 installed on the SSD, just mount the partition(s) from the other disk and delete anything you don't need anymore.   The Linux File System Hierarchy document spells out what is stored where, so you can know what is safe to delete and what isn't.  

But .... in general, anything that isn't under /home (from the old install point of view) or on some data partition, can be deleted safely.

Definitely want to have backups of everything (old and new) before starting. It is easy to get confused since the old partitions will be mounted in new places ... just have to be careful to only delete things from the new mount areas.

---

### Post by rubberduck1968 on 2017-09-24
re; Bucky Ball. 1 & 3 ... Windows... perish the thought!

Seriously though, yes number 1, the idea is to set up 16.04 on the SSD till I get it right. Thought about using a external plug in caddy until it's ready, disconnecting the HDD while working on it. It's so the missus can use Facebook while I&#8217;m away during the week. Then number 3.

re; TheFu. Got everything backed up in triplicate.

---

### Post by TheFu on 2017-09-24
Doing this is about 1 hr of work, worst case.

Install 16.04 on the SSD - 15 min.

Connected the old disk, mount the partitions someplace temporarily - I would use /mnt/1, /mnt/2, /mnt/3 ... .... /mnt/N  ... for as many partitions as you have.  Then I'd look inside each for OS stuff compared to personal data files ... like the old HOME would have.  Deleting files is 5 min to get the major stuff.  The other 40 minutes is cleaning out all the crap in your HOME ... like in the .cache/ directories left behind by browsers, emailers, etc.

---

### Post by Bucky Ball on 2017-09-24
> **rubberduck1968 said:**
> Seriously though, yes number 1, the idea is to set up 16.04 on the SSD till I get it right.

I use LTS releases only and run all OSs on one SSD (including Windows :)). When a new LTS release comes out I install it on a partition on the SSD and play around with it until I'm happy, then just change the grub to put the newest install at the top of the list and booting first. 

I have one large data partition on a HDD, OSs installed on small partitions on the SSD (installing OSs on the SSD and data on HDD is common) and all Ubuntu installs are linked to the data partition on the HDD using symlinks. 

No matter how many installs I make on small partitions on the SSD, create a few symlinks, delete a few default folders, and they all reference the same data in the data partition on the HDD. No redundancy, no confusion. :)

(PS: See my first post. Once you have 16.04 installed, plug in the HDD, boot to 16.04, open a terminal and 'sudo update-grub'. That should pick up the 14.04 install on the HDD and add it to your grub list when you boot so your wife can choose it from there. You can even stick it back at the top of the list. 

That's another option. ;))

(PPS: As TheFu mentions, the install shouldn't take long, particularly if all you have in the machine is one new SSD. Sweet. Blank slate. As this is the case, suggest you 'Try Ubuntu' from the install media, launch Gparted and put a partition table on the SSD before you start. When done, double click the 'Install Ubuntu' icon on the desktop.)

---

### Post by efflandt on 2017-09-24
I have a 512 GB mSATA SSD card from a gaming laptop that no longer turns on properly. So I put that in a 2.5" SATA adapter and used a different laptop to install Ubuntu to it. Then I added that mSATA in SATA adapter to my desktop.

So I currently have 14.04 on my 1 TB drive (along with Win7) and 16.10 on the mSATA SSD. But since 16.10 has reached end of support I need to figure out if 16.04 LTS works for me now or whether to upgrade to 17.04 once I am sure that I have everything backed up. I have only done a version "upgrade" once on an older 80 GB SSD from 11.10 to 12.04 and kept that for years as a backup system in case, which came in handy when my 1 TB drive began failing to run e2fsck including locking out bad blocks until eventually replacing the 1 TB drive which also had 12.04 on it at the time. I later did a fresh 14.04 LTS install to the 1 TB drive, but kept 12.04 on the old SSD until I started playing around with 16.04 from scratch on that 80 GB Intel SSD.

The reason that I am not currently running 16.04 is because I originally had problems with blank screen during boot (no text for BIOS splash or grub menu) until some OS did actual graphics (like gui login in Ubuntu, or Win7 graphics if that was set as default). That happened regardless of whether 16.04 was on the 80 GB SSD or 512 GB mSATA SSD, but only on my main PC, it worked fine for even older computers or laptops. That has never been a problem with 16.10. I put a newer 16.04 release on the 80 GB SSD using a laptop and need to test that on my desktop before making a decision.

So my suggestion would be to leave 14.04 on your hard drive (or upgrade it to 16.04 once SSD is working) to have a working bootable backup system in place until such time that you need the space. And assuming that this is a legacy BIOS system (not UEFI) install grub for the SSD system on the SSD mbr, so you can set BIOS to normally boot grub and either system from that, but still have the option to boot either drive independently. Note that if normally booting from the SSD and an update on the hard drive includes a kernel update, you will need to run "sudo update-grub" on the SSD for its grub to find the updated kernel on the hard drive.

---

### Post by rubberduck1968 on 2017-09-25
Thank you everyone for your help and answers.

Cheers.

---

### Post by gordintoronto on 2017-09-25
I wouldn't bother removing 14.04, it doesn't take much space on a 1 TB drive, and provides a fallback option.

However, I might run: sudo apt clean
also fire up the browser(s?) and empty the cache.

---

