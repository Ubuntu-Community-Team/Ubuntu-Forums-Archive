---
title: "Installation of Feisty on my desktop - will GRUB recognise my SATA RAID0?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by geeforce on 2007-06-16
Hiya!

Well I bought the Feisty Fawn book from Kofler and to be honest there is a big problem. ATM Windows is running on a SATA Raid 0 with 2 Seagate 120GB drives. My backup drive is a 250GB hard drive where all my backups have been saved to.

Well to install Ubuntu one hard drive has to die so to speak. But which one. First I thought Ubuntu could run on my 250GB disk and Windows would stay on the Raid. All my backups have been copied to an external one so the backups are there.

The only problem is GRUB. I know Ubuntu won't recognise the SATA drivers to be in a Raid array so Grub isn't able to refer to the Raid properly so when I select Windows XP Prof. that he boots that properly?

I'm really in a quandrary and need help. Another option would be to destroy the Raid and install Ubuntu on SATA1 and Windows on the EIDE drive. SATA2 could be used for other data.

What do you think?

My mainboard is a P4P800 Deluxe with the Raid controller onboard.

---

### Post by trak87 on 2007-06-16
I would keep the backup drive as a backup. I'm not sure what the "ATM" means in "ATM Windows". The raid 0, as I understand it, divides the data onto two drives for the purpose of speed, and you need a backup in this situation in case one of the drives goes bad, and you do have a backup. Good. On the other hand raid 1 is for backup safety via redundancy, but that doesn't apply here. If I have the facts straight, I would convert the Windows in the raid 0 configuration into a regular (non-raid) partition on one of the drives and use the other drive for Ubuntu. Then the backup drive would still continue to function as a backup for both operating systems.  I  have no raid experience so please get other advice before proceeding.

---

### Post by bigken on 2007-06-16
strong word of advice backup your data and ditch the raid 0 belive if it goes wrong you have had it well you data has

---

### Post by geeforce on 2007-06-16
Thanks trak87 but the problem is - and I should have mentioned that - that the SATA Raid 0 is on the EIDE drive which is nearly full. If I destroyed the Raid the whole image of the Raid would farly extend the 120GB :(

The external USB Disk is a 320GB disk to provide enough space for my old EIDE backup plus my notebook backup.

---

### Post by raijinsetsu on 2007-06-16
First off: your raid is probably software raid masquerading as hardware (ex.: nVRaid).
Secondly: if you boot from the first drive of the raid-0, windows should boot normally, but only if it knows it was installed on a raid-0. Have you tried this?

---

### Post by geeforce on 2007-06-16
> **raijinsetsu said:**
> First off: your raid is probably software raid masquerading as hardware (ex.: nVRaid).
Secondly: if you boot from the first drive of the raid-0, windows should boot normally, but only if it knows it was installed on a raid-0. Have you tried this?

When my BIOS went mad because the battery broke both SATA drivs weren't configured in RAID mode so Windows couldn't boot.

---

### Post by Pumalite on 2007-06-16
> **raijinsetsu said:**
> First off: your raid is probably software raid masquerading as hardware (ex.: nVRaid).
Secondly: if you boot from the first drive of the raid-0, windows should boot normally, but only if it knows it was installed on a raid-0. Have you tried this?

I'm sorry to disagree with preceding post. I have to also advice against Raid 0. In my experience, it's not supported by Feisty Fawn. The good advice here is ( and was already given ) backup all your data, work with independent drives, install and you will not have problems in the future.

---

### Post by geeforce on 2007-06-16
> **Pumalite said:**
> I'm sorry to disagree with preceding post. I have to also advice against Raid 0. In my experience, it's not supported by Feisty Fawn. The good advice here is ( and was already given ) backup all your data, work with independent drives, install and you will not have problems in the future.

It looks like that my RAID0 will be dead in a few minutes time. Instead Ubuntu will be installed on SATA1. SATA2 will be free or be used for normal storage and my EIDE Backup drive will be transformed into my Windows drive.

This way I shouldn't have any probs.

---

