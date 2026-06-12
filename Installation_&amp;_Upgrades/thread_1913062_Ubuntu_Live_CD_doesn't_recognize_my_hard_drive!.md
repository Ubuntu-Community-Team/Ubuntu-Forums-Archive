---
title: "Ubuntu Live CD doesn't recognize my hard drive!"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by Jowe on 2012-01-21
When I try to install Ubuntu on my pc using the live cd the installer doesn't see my hard drive. I've tried making a partition that doesn't have any os on it but that didn't work. Any ideas?

---

### Post by Penguinnerd on 2012-01-21
What sort of PC is this?

What type of hard drive? How large?

What version of the live CD?

---

### Post by Jowe on 2012-01-21
> **Penguinnerd said:**
> What sort of PC is this?

What type of hard drive? How large?

What version of the live CD?

Standard PC - Intel i5 2500k, 8gb ram, Windows 7

Hard Drive - 1 TB Seagate Barracuda 7200 RPM

---

### Post by darkod on 2012-01-21
If the disk has been used in raid before, it probably has meta data remains. Ubuntu installer ignores disks with raid meta data.

Boot into live mode and execute in terminal:
sudo dmraid -E -r /dev/sda

If the disk is not /dev/sda change accordingly. Confirm the removal of meta data and you're good to go.

NOTE: Do this only if NOT running raid. It will destroy your raid if you are. You install in a different way on raid.

---

### Post by Jowe on 2012-01-22
> **darkod said:**
> If the disk has been used in raid before, it probably has meta data remains. Ubuntu installer ignores disks with raid meta data.

Boot into live mode and execute in terminal:
sudo dmraid -E -r /dev/sda

If the disk is not /dev/sda change accordingly. Confirm the removal of meta data and you're good to go.

NOTE: Do this only if NOT running raid. It will destroy your raid if you are. You install in a different way on raid.

That didn't do it, I've never used the drive for raid anyway... :\

---

### Post by darkod on 2012-01-22
Another option is an error on the partition table. Many times windows ignores them and it can appear to work fine, while linux doesn't ignore these errors and it can happen it doesn't display any partitions because it can't figure them out.

Does it not show a hdd at all, or it shows it whole as unallocated without partitions?

---

### Post by Jowe on 2012-01-22
> **darkod said:**
> Another option is an error on the partition table. Many times windows ignores them and it can appear to work fine, while linux doesn't ignore these errors and it can happen it doesn't display any partitions because it can't figure them out.

Does it not show a hdd at all, or it shows it whole as unallocated without partitions?

It doesn't show the hd at all.

---

### Post by jasonrisenburg on 2012-01-22
is there anyway to repair them?

---

### Post by darkod on 2012-01-22
If you try:
sudo fdisk -l (small L)

Does it show the disk partitions or not? Post the output.

If it still doesn't see it, I have no idea.

Try another sata port, sometimes it seems the disk on a new sata3 port is not recognized properly. Try different port just to see if it changes anything.

---

### Post by eduan on 2013-05-03
Tnks!!!!!!!!!!

---

