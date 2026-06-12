---
title: "Lenovo Yoga 14: how to install ubuntu, upgrade ssd"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by vaughn3 on 2016-01-03
I just got a Lenovo Yoga 14 with Windows 10, it has UEFI firmware
I want to replace the existing 16GB M2 SSD with a 128 GB SSD and put the Ubuntu OS on there as part of a dual-boot configuration.
Originally I thought the Windows OS would be on the SSD but it appears to be some kind of cache, as the Windows OS is on the 1TB HDD. When booting from a Ubuntu live CD the SSD shows up as a "GPT" system with an ID of ee. Fdisk tells me to use gparted, but gparted sees it as "unknown." GPT fdisk (gdisk) shows it as a "Basic data partition" with a code of FFFF.
This is my question: is there any data in this partition or is it just a cache? Do I need to image this partition and restore it onto the new, larger SSD? Or can I simply create an empty 16 GB GPT partition on the new SSD?
A related question: what is this cache anyway, some kind of system state for hibernation? Otherwise it doesn't seem to make much sense to use SSD, which has slow write times and a limited number of rewrites, as a cache. If not, what the heck is it for?

Thanks in advance!

---

### Post by Bucky Ball on 2016-01-03
*Thread moved to **Installation & Upgrades**.*

Welcome. ***Ubuntu, Linux and OS Chat ***area is not for support.

Sounds like you have a hybrid drive: an SSD and HDD stuck together, sort of. Yes, the SSD works as a cache and the OS is on the HDD.

Am I right in saying you want to remove the hybrid drive completely and replace it with an SSD? If so, pull the hybrid drive, put in the SSD, install Windows, install Ubuntu. That is the simple version.

If it is a hybrid drive there is no option of pulling just the SSD or just the HDD. They are one unit as far as I can glean.

If you have a second drive bay you could leave things as they are and simply add the SSD in there and install Ubuntu. I removed the optical drive bay in my laptop, replaced with a HDD bay, installed an SSD in there and am typing from an install on that now. I have Win7 on sda and Ubuntu on sdb (sda=HDD, sdb=SSD) :)

---

### Post by vaughn3 on 2016-01-04
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Welcome. ***Ubuntu, Linux and OS Chat ***area is not for support.

Sounds like you have a hybrid drive: an SSD and HDD stuck together, sort of. Yes, the SSD works as a cache and the OS is on the HDD.

Am I right in saying you want to remove the hybrid drive completely and replace it with an SSD? If so, pull the hybrid drive, put in the SSD, install Windows, install Ubuntu. That is the simple version.

If it is a hybrid drive there is no option of pulling just the SSD or just the HDD. They are one unit as far as I can glean.

If you have a second drive bay you could leave things as they are and simply add the SSD in there and install Ubuntu. I removed the optical drive bay in my laptop, replaced with a HDD bay, installed an SSD in there and am typing from an install on that now. I have Win7 on sda and Ubuntu on sdb (sda=HDD, sdb=SSD) :)

Thanks for moving my post to the appropriate forum.
It's not a hybrid, there are two separate drives.
I plan to replace the 16GB SSD with a larger one (128)
I'd like to recreate the 16GB cache partition on the new SSD so Windows can use it. I then want to put the Ubuntu OS on the rest.
The idea is to have the OS on the SSD for faster bootup and the all my data on the 1TB HDD. If it works, it'll be the best of both worlds.
Mainly, I wasn't sure how to recreate that cache partition since it seems to confuse gparted.

---

