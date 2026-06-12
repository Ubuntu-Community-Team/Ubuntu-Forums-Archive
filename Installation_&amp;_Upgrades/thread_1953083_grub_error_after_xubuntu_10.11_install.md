---
title: "grub error after xubuntu 10.11 install"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by C14 on 2012-04-05
Hello,

I tried to install xubuntu alongside windows xp on an old machine (pentium 4) today.
I had two partitions, a primary windows xp partition and a logic partition for data.

As I did not like the simple slider for the installation size in the installer,
I first shrunk my logic partition to the right size using gparted.
Afterwards, I installed xubuntu, and now i get the following error during boot:
"error: no such partition
grub rescue>"

I tried to fix it with BootRepair, but no success
Here is the info from BootRepair:
[http://paste.ubuntu.com/916315](http://paste.ubuntu.com/916315)

Any idea what I could do to fix this problem or at least recover my Windows install?

---

### Post by Rubi1200 on 2012-04-06
Hi,
for the most part the script results suggest everything is where it should be.

However, on older drives there was a 139GB limit beyond which the BIOS could not "see" the rest of the drive. Check in BIOS if there is an option to enable a large drive feature or if it reports how large the drive is supposed to be.

I would also try reinstalling GRUB just in case:

From a LiveCD do the following:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

This guide explains how to restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by C14 on 2012-04-07
Hi,
thx for your help!

I checked the BIOS, and it sees the full 160GB of my disk.
Nevertheless, I believe there might be this 139GB issue at work, because after deleting the xubuntu partition and using BootRepair again, the system boots just fine into Windows XP now (with grub chainloader), so the problem was the xubuntu partition that wasn't recognized.
Maybe I'll try moving my data partition to the back sometime and install xubuntu directly after the xp partition.

---

