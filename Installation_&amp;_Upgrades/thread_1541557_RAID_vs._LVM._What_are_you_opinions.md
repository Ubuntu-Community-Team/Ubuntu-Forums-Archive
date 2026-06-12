---
title: "RAID vs. LVM. What are you opinions?"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by psv1120 on 2010-07-29
I am currently in the process of making a file server at home. My friend suggested that I do an LVM (more for learning purposes than anything) instead of a RAID. What would you suggest?

As a side note, I have a RAID card with 5 HDD's attached (each one being a 250GB ATA HDD) to the computer. I am planning on using these for the server.

---

### Post by chopinhauer on 2010-07-29
> **psv1120 said:**
> I am currently in the process of making a file server at home. My friend suggested that I do an LVM (more for learning purposes than anything) instead of a RAID. What would you suggest?


If it is RAID0 you are thinking about, LVM can replace it and offer more features. Otherwise I'd recommend putting LVM on top of a RAID device.

> **psv1120 said:**
> 
As a side note, I have a RAID card with 5 HDD's attached (each one being a 250GB ATA HDD) to the computer. I am planning on using these for the server.

If you have a hardware RAID you should use it. And put LVM on top of it, so you can easily resize partitions.

---

### Post by psv1120 on 2010-07-29
> **chopinhauer said:**
> If it is RAID0 you are thinking about, LVM can replace it and offer more features. Otherwise I'd recommend putting LVM on top of a RAID device.



If you have a hardware RAID you should use it. And put LVM on top of it, so you can easily resize partitions.


How does that work? I understand how RAID works and LVM works but how can they work on top of each other?

And what would be the purpose of that? Would it ensure more security to my files?

---

### Post by jacekk015 on 2010-07-29
Example:
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

---

### Post by YesWeCan on 2010-07-29
> **psv1120 said:**
> How does that work? I understand how RAID works and LVM works but how can they work on top of each other?

And what would be the purpose of that? Would it ensure more security to my files?
LVM has nothing to do with security. It is just a convenience method for allowing you to change the size of an existing partition without having to erase existing data.
RAID is a means to add data security by duplicating your data across multiple hard disks.
The two are independent.

---

