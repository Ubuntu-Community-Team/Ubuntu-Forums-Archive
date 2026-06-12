---
title: "[SOLVED] Upgrade from 7.10 to 8.04LTS"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by marktyler on 2008-05-12
I'm looking for advice on the following upgrade. 

Although I have the desktop version installed the machine concerned is used as a file/media server (Webmin, Samba, mt-daap etc) and is pretty important both stability and data wise - hence it's a linux machine. The machine has the OS and home folders on one SATA drive and 3 other SATA drives setup in a software RAID 5 configuration.

Am I better off performing an in place upgrade using apt or refreshing? My guess is the in place upgrade as this has worked nicely in the past (when the machine had no RAID) and everything should remain working, but I was wondering are there any issues surrounding the mdadm RAID array when upgrading? 

I've read the odd 6.06 to 7.10 issue but that seems to be a regime change with software RAID.

Any further points of note?

Thanks.

Mark.

---

### Post by iaculallad on 2008-05-12
If your machine performs well as what you had expected it to do, stick with your 7.10 for the meantime. Wait for at least three months or so for critical bugs (8.04) to be resolve first.



Im keeping my 7.10 (Ubuntu Desktop Edition) for my FTP server. No plan of upgrading it yet but installed Ubuntu 8.04 LTS on my desktop for testing purposes.

---

### Post by martin1977 on 2008-05-14
Hi Mark,

I'm in a similar position, but perhaps with a more complicated Raid setup.  I think the advice from the first reply is good - to wait a while - but ultimately I would like to be on the 8.04 LTS version with my server.

I've seen reports of problems upgrading where partitions were in the older format of hda1, hdb1, rather than the newer sda1, sdb1 format, but I don't have this problem.

I have four 500GB drives configured using mdadm:

sda1, sdb1 in Raid1 as md0 with Ubuntu 7.04 installed from Alternate CD
sdc1, sdd1 in Raid1 as md1 with /home
sda3, sdb3 in Raid1 as md2 for use in md5
sdc3, sdd3 in Raid1 as md3 for use in md5
md2, md3 in Raid0 as md5 with /business (Raid10)
sda4, sdb4, sdc4, sdd4 in Raid5 as md4 with /multimedia

This gives me about 1.2TB overall.

I'm really pleased with this setup in conjunction with a Gigabit LAN.  It's very fast!  Raid10 (0+1?) where write performance is important and Raid5 where mainly reading media files.

However, I'm wary of breaking it with an upgrade to 8.04 LTS Hardy and would appreciate hearing from anyone who has had experience of similar situations.

Regards, Martin

---

### Post by kubug on 2008-05-23
Hi there,

if you are using 64 bit, then I would suggest waiting.

I am currently working on getting my server back alive after the upgrade from Gutsy to Hardy. I waited until 2 days ago. I rebooted and got stuck on the initramfs. 

Great! I have to say that Hardy has been the worst release of Ubuntu yet. I have been on Ubuntu since 5.10 (long time SuSE user before) and I never had this many issues. Every computer I upgraded had issues. None of them the same, but all had issues ranging from minor to major (as with this server at work). 

Anyways, to get back to the problem, it seems the is a kernel bug, which prevents the HDD's being detected properly and it messes up mdadm. I don't know if a fresh install would help.

---

### Post by martin1977 on 2008-07-29
**Update**

Well we finally took the plunge and upgraded to 8.04LTS (setup described above).  I'm pleased to report that there were no significant problems - all the Raid arrays were intact after the upgrade. The only minor issue was a resetting of the mounted arrays to read only, which was easily sorted.

We did have some problems with localedef causing the upgrade to hang (several documented solutions exist), but they were overcome fairly easily, but not without some angst!

Regards, Martin

---

