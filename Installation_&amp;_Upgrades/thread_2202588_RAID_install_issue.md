---
title: "RAID install issue"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by Lou_Kitz on 2014-01-29
I have a SuperMicro  Super Workstation 5036T-T server.  I previously setup a mirror RAID (hardware) and installed MS SBS 2008 with no issues.  It saw the RAID as one drive and installed. I pulled the two drives, installed two 200Gig SATA drives and setup a striped RAID.  When I tried to install Ubuntu 13.10 64bit server version it detected the RAID drives and asked if I wanted to activate them.  I said yes and then it continued to partition them for me with LVM.  When it got to the System Install it FAILED.  I figured out that it setup a software RAID where I had a Hardware RAID.  I deleted the RAID in the hardware BIOS setup and rebuilt it. I tried again this time choosing not to activate the RAID set.  When I got to the part to partition the disk it asks me which one of the two I want to partition.  I assumed if it was going to have trouble dealing with my hardware RAID it would ask for drivers at some point but it didn't.

Logic dictates that I just don't understand something here.  I don't have a lot of experience with RAID and this is my first time trying it outside of Windows.  What am I missing or misunderstanding?

Thanks,

---

### Post by Lou_Kitz on 2014-01-30
I finally got it to recognize my RAID0 200Gig + 200Gig = 400Gig as a single drive by redoing the RAID and running the install program several times.  I tried to let it do a guided partitioning and it failed to create the file system on / again.  The other partitions it did just fine creating, at least they showed in the list and I received no error about them.  I'm done for tonight.  Any ideas on what I need to look into and read about before I try again would be a huge help.

Thanks,

---

