---
title: "Installing around bad sectors"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Mr. Snuggles on 2008-10-27
I'm trying to install ubuntu on a somewhat-old laptop, but when I try to re-size the partition via gparted, if always fails. The installer says it is because of bad sectors on the hdd, but Windows doesn't pick anything up, and numerous chkdisk /r did not improve the situation.

The details on the installation errors seem to imply that there is a way to install around these bad sectors; is that possible?

Yes, I know that easiest thing to do is get a new hard drive, but I don't really want to put money into this old thing.

---

### Post by oilchangeguy on 2008-10-27
> **Mr. Snuggles said:**
> I'm trying to install ubuntu on a somewhat-old laptop, but when I try to re-size the partition via gparted, if always fails. The installer says it is because of bad sectors on the hdd, but Windows doesn't pick anything up, and numerous chkdisk /r did not improve the situation.

The details on the installation errors seem to imply that there is a way to install around these bad sectors; is that possible?

Yes, I know that easiest thing to do is get a new hard drive, but I don't really want to put money into this old thing.

please define old laptop. specs please, it may not even be able to run ubuntu.

---

### Post by Mr. Snuggles on 2008-10-28
It's a Compaq R4000. I know ubuntu will install on it (seen examples).

---

### Post by oilchangeguy on 2008-10-28
> **Mr. Snuggles said:**
> It's a Compaq R4000. I know ubuntu will install on it (seen examples).

that may be true, if the laptop in question has enough ram. which is why i asked for the specs of YOUR computer.

---

### Post by Mr. Snuggles on 2008-10-28
CPU: Athlon 64 3200+ 1.8ghz
Ram: 512 mb 
HDD: 80gb

Wubi works fine, but the disk performance was a little slow for me and I really would like hibernation.

---

### Post by Mr. Snuggles on 2008-11-01
Solved!

Used the guide on the Parted Magic website for resizing via command line ntfsresize (using the --bad-sectors option) and then repartioning with fdisk.

Got 8.10 installed and running great.

---

