---
title: "Installing 12.04 x64 Server on Hardware RAID"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by DarkMorford on 2012-08-15
Greetings, all—

I'm trying to install Ubuntu Server 12.04 x64 on my new system. The motherboard is an ASUS P8B-M and has an LSI MegaRAID Software RAID controller onboard. I have two 500 GB hard drives hooked up, and I've used the BIOS utility to put them in a mirrored (RAID 1) configuration.

When the Ubuntu installer reaches the Detect Disks stage, it offers me a choice that I've never encountered doing single-disk installs, for obvious reasons:> One or more drives containing Serial ATA RAID configurations have been found. Do you wish
to activate these RAID devices?

Regardless of whether I select Yes or No here, the partitioner starts up and presents another unusual menu.> This is an overview of your currently configured partitions and mount points. Select a
partition to modify its settings (file system, mount point, etc.), a free space to create
partitions, or a device to initialize its partition table.

Configure iSCSI volumes

Undo changes to partitions
Finish partitioning and write changes to disk

Selecting the iSCSI option then prompts me for an IP address and port to connect to, and here I'm stumped. How do I get the installer to recognize the RAID array and partition it as usual? Is there a Linux equivalent to Windows' infamous "F5 drivers" I need to be aware of?

---

### Post by DarkMorford on 2012-08-15
BUMP for help, please?

---

### Post by intel on 2012-08-16
If you are trying to go RAID 1 (Mirroring) route, you are shooting for a more reliable system, so using the motherboard feature RAID here is a bad idea.

The RAID 1 mdadm infrastructure in linux is pretty solid, use that instead.

Cheers!

---

### Post by DarkMorford on 2012-08-24
Solved by taking intel's suggestion. Installed on mdadm and it's working like a charm.

---

### Post by zanuxzan on 2013-01-03
> **DarkMorford said:**
> Solved by taking intel's suggestion. Installed on mdadm and it's working like a charm.

Were you using disks that were from an existing installation or were they blank?

I'm getting the same issue with two hard disks that were previously used for a CentOS installation that used LSI MegaRAID in a IBM System x3250 m4.

I'm wondering if I should wipe the disks with gparted before attempting the install.

---

### Post by tgalati4 on 2013-01-03
If you choose to use the BIOS RAID, you need to update the RAID BIOS (which is separate from the motherboard BIOS) for the most reliable operation.  Also, it helps to wipe the disks completely using the RAID BIOS functions before installing software RAID.

I would be curious to know if anyone has measured performance differences between using BIOS RAID versus mdadm for LSI MegaRAID controllers.

---

### Post by chrislott on 2013-01-17
Here's a me-too.  Also really hoping for helpful replies!

I have a SuperMicro with two 2Tb drives that I configured using the machine's BIOS into a RAID 1 (mirrored) array, and did a full clear, that only took a mere 24 hours.  

I previously installed RHEL5 on this machine with a similar setup (2x1Tb as RAID1), had no difficulties.  

Now I'm trying to install 12.10 x64 server.  Astonished at the trouble I'm having here.

If I answer "yes" to the Activate Serial RAID question, I get the prompt screen mentioned above: configure iSCSI, finish partitioning, undo partitioning.  None of those look right.

If I answer "no" to the Activate Serial RAID question, I get the partitioner screen, BUT it shows two separate disks, /dev/sda and /dev/sdb, offers to let me partition them separately. Bogus, this should be offering to let me partition the RAID volume.

I see the suggestion to use Ubuntu linux software RAID.  I have no experience with that.  Maybe it's just fine. I'm just quite surprised that Ubuntu can't handle this, where RHEL worked fine.

---

### Post by chrislott on 2013-01-17
FWIW here's the doc page at ubuntu.  They call this low-rent, motherboard-enabled RAID "fake raid".  Unfortunately the doc has not been updated since mid 2011, with the last comments addressing ver 10.04.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

