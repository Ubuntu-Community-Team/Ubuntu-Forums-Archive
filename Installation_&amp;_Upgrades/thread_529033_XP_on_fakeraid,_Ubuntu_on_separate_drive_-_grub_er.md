---
title: "XP on fakeraid, Ubuntu on separate drive - grub error 21"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by corpkid on 2007-08-18
complete noob - so help me out here if you can.

I have XP installed on an sata RAID0 array (intel ich8r fakeraid) as well as another pair of disks in RAID1 for my data.  I went out and bought a 5th sata drive and installed ubuntu 7.04 to that.

Now I am getting an ERROR21 from grub on restart.   Ubuntu live CD/install can NOT mount my RAID0 array, though It can see my RAID1 disks (but it sees them as two drives, not one).  I suspect this is the problem.

Any ideas what I should do to fix this?  If possible, I do not want to reinstall windows.

Thank you!
Dominic

---

### Post by corpkid on 2007-08-19
UPDATE - Well, here's what I have done so far.

First, I booted up the Windows install CD and used the recovery console to issue a FIXMBR so I could boot windows again.

Then, I unplugged my raid drives (the two RAID0 windows drives and the two RAID1 data drives).  So, all I had left was the single new drive for Ubuntu.

I then reinstalled Ubuntu choosing the guided partitioning method.

Now, I have all of my drives plugged back in.  I'm trying to figure out how use the NT boot loader to load Ubuntu.  As it stands I have to go into my BIOS and change which drive is the boot drive if I want to switch OS's.

Any good articles out there on using the nt boot loader to do this?

Thanks again!
Dominic

---

### Post by Jonnothin on 2007-08-19
If i'm not mistaken you installed Windows first then Ubuntu? And I thought you had XP, not NT

---

### Post by corpkid on 2007-08-19
LOL, yeah I still call it the "nt boot loader" for some stupid reason.  

Yes, I installed XP a long time ago and then just bought a new HDD to house Ubuntu.

---

### Post by Jonnothin on 2007-08-19
What guided partition did you use? And how does it mess up. Does it automatically starts up with Windows?

---

### Post by corpkid on 2007-08-19
During the install, I just told it to use the only disk it could see (I unplugged everything else) and let it partition it using the full drive.

I don't get any errors now that I reinstalled - it's just that I have to use my BIOS to switch which drive/volume boots (either the XP Raid array or the Ubuntu disk).  Certainly not a great solution.  I'd like to either use GRUB to present me with a boot menu or just use the XP boot loader.  I found some articles on how to use the XP boot loader to load linux, but thus far have been unsuccessful.

---

### Post by herdwick on 2007-08-21
> **corpkid said:**
> I don't get any errors now that I reinstalled - it's just that I have to use my BIOS to switch which drive/volume boots (either the XP Raid array or the Ubuntu disk).  Certainly not a great solution.  I'd like to either use GRUB to present me with a boot menu or just use the XP boot loader.  I found some articles on how to use the XP boot loader to load linux, but thus far have been unsuccessful. I had most success by downloading bootpart.exe for Windows which is a command line tool that looks for available partitions and allows you to add them to the XP boot loader menu. I do get a grub error but hitting enter twice gets me into Linux via the XP boot menu without resorting to BIOS changes, switches, unplugging drives or inserting/removing floppies or CDs !

Phil

---

