---
title: "When should I format a storage space?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by BKbroila on 2010-12-18
I'm about to do a clean wipe of my laptop, to try out Ubuntu. I've read quite a bit about dual-booting WIn7 and Ubuntu, but not alot about the process of installing. I'd like to install Win7 and Ubuntu on 2 small drives, and leave the rest for a Storage partition. But when should I partition that Storage Drive? Should I do it while I'm installing Win7? Or should I partition the amount of space to Storage after I've installed Ubuntu?
Thanks

---

### Post by 73ckn797 on 2010-12-18
You have not stated how large the hard drive is.

You can boot from the Ubuntu CD and run from the CD. Then go to System/Administration/Gparted and setup the partitions as desired. I would recommend minimum 20-25GiB for Windows (I do not use Windows 7 so I do not know how much space will be required. I do know that Vista requires at least 20GiB for a basic install (my son just tried installing Vista on a MacBook. He went back to XP and it required 4GiB). Plus you will need space for the documents to be available.

Typically Windows wants the first part of the drive. I would also recommend giving Ubuntu at least 12GiB plus create a separate partition designated as :/home" for documents and added apps. That way you could always reinstall Ubuntu later and keep personal files and setting without losing them.

---

### Post by BKbroila on 2010-12-18
Well I plan on giving Win7 and Ubuntu each 80 GBs and the Storage Drive 160 GB (total to about 300)

So you're implying that I install Win7 first?

---

### Post by 73ckn797 on 2010-12-18
> **BKbroila said:**
> Well I plan on giving Win7 and Ubuntu each 80 GBs and the Storage Drive 160 GB (total to about 300)

So you're implying that I install Win7 first?

Yes. I have been able to install Windows XP on a second partition but typically Windows will want the priority in relation to disk space. Ubuntu will set things up to where you can  select which operating system to boot from. Ubuntu will be listed as the first choice.

The "/home" partition will be something that you will have to manually designate during the installation. Give Ubuntu 12GiB for the "/" partition and "/home" as the remainder of the 48GiB.

One suggestion would be to format and create partitions as follows:
Windows as a 80GiB partition.
Ubuntu as 12Gib (system files, designated as "/") options presented when manually setting up partitions.
48GiB as "/home" (personal file storage)

Read this first:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning")

---

