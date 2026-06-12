---
title: "Struggling with Installation of Ubuntu 64 bit v10.04, v9.10 and v9.04"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by abeaty on 2010-08-06
Hello all,

I have a Gigabyte 880GA-UD3H MB with 2 Western Digital 500 GB hard drives that I want running in RAID 1.  I have configured RAID 1 in the BIOS so in theory the OS on install should only see one drive.  I have tried and tried again to get any of the above versions of Ubuntu running against the RAID 1 as configured.

v10.04 and v9.10 fail to install at all.  In searching, I found that 10.04 seems to have problems with this config and the recommendations were to go back to 9.10.  When that failed to install too, I found similar comments about moving to 9.04

v9.04 installs fine, but the partitioner sees two drives sda and sdb both of which are 500GB so it doesn't appear to be "seeing" my RAID config.

What am I doing wrong?
Am I wasting my time?

Please help....

---

### Post by sikander3786 on 2010-08-06
Hi.

Are you installing from desktop cd? It is mentioned on [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID") page that for raid configuration you need to use the alternate cd. Take a look at the link provided.

Regards.

EDIT: This link might also be helpful.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by abeaty on 2010-08-06
> **sikander3786 said:**
> Hi.

Are you installing from desktop cd? It is mentioned on [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID") page that for raid configuration you need to use the alternate cd. Take a look at the link provided.

Regards.

EDIT: This link might also be helpful.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Thanks for the links - I did see those, but didn't realize my configuration was knows as FAKERAID so I moved on without really looking at them.

This time around though, I spent some time and followed their recommendations.  Unfortunately, neither one helped.  The alternative install looked identical to the server install and it gave the same error when trying to create the ext4 partition.  When I tried the live CD desktop install, I got the attached error.  The partition manager is definitely seeing the RAID disk, but then it can't work with it.

It seems like I have a few choices:

1) Get this to work through more elbow grease.  I don't expect that I will have much luck with it since I have already been working on it for some time.
2) Try another distro
3) Buy a hardware RAID card to support my two SATA drives.

For #2 - Are there distros out there that are known to work well with FAKERAID?
For #3 - Are there cards that are fully compatible with Ubuntu 10.04 (ie. guaranteed to work)?

Thanks.

---

### Post by ronparent on 2010-08-06
Your problem is typical for anyone trying to install 10.04 to a raid. The problem with 10.04 is that gparted won't recognize a raid and therefore partitioning with installation fails. I posted a bug report ([https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)) and received a response that suggested a quick fix. The problem occurs because 10.04 was distributed without a package called kpartx which is needed by gparted to read a raid. The solution is to open the 10.04 install from a live cd session, use synaptics to install kpartx for the session, and continue on to run a normal installation within the session. You may run into a glitch writing the grub boot loader to the raid but this can be fixed if needed. Post if you need additional detail on proceeding. Good luck.:D

---

