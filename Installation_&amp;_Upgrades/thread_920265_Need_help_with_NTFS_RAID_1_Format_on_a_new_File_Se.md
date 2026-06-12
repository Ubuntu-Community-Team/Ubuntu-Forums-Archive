---
title: "Need help with NTFS RAID 1 Format on a new File Server based on Ubuntu Server"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by delanet on 2008-09-15
Hello all,

I am new to Linux, but experienced in Windows and I really could use some help with the following: I am setting up an Active Directory connected, Windows Domain Member, Samba File Server based on Linux Ubuntu Server 8.0.4 with Software Raid 1 (Mirroring)

I am setting up the Raid using the native software RAID option that Linux offers. 

There will be 3 partitions on each disk mirrored on the other:
1. a 90 GB ext3 partition (for the system)
2. a 400 GB NTFS partition (for data)
3. a 6 GB SWAP partition

I have already set up once the File Server successfully on a single Hard Disk Test system (i.e. without the RAID configuration ) without any problems. 

Now that I am trying to implement the configuration described above I hit a wall of conflicting and confusing information that led me to come to you for advice.

Can you please advice me what would be the correct path to follow in order to set up, format and mount my RAID NTFS partitions?

Thank you in advance.

---

### Post by delanet on 2008-09-17
<bump>

---

