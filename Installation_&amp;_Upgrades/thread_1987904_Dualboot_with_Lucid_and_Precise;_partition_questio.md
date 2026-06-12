---
title: "Dualboot with Lucid and Precise; partition question"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by Tuxedo Mask on 2012-05-26
I've got a system with Lucid installed, and imagining I'd want to try out newer releases independent of it I have set aside space for another release. As it stands, my main drive - sda - is divided as follows:
sda1: boot
sda2: swap
sda3: extended with sda5 (Lucid) and sda6 (empty ext4)
sda4: home

I set up /boot, swp, /, and /home when I installed Lucid, telling it to format those partitions in the process. I'm trying to install Precise now, but in the partition manager there's an additional option at the bottom to define the location of the bootloader installation, and it gives all the drives/partitions available, including sda. If I remembered where the bootloader was installed in Lucid, I'd just point it to that location, but as it stands I don't know; I'm GUESSING it's in /dev/sda but I can't be sure, because as far as I know it was modified automatically on installing Lucid.

My question, then, is twofold: how can I find out where the mbr is located, and should I just pick that location from the dropdown menu in the Precise installer? Thanks.

EDIT: A new concern: When indicating the partition to use as /boot (i.e., /dev/sda1), I do not need to format it, correct? Thanks again.

---

### Post by wilee-nilee on 2012-05-26
> **Tuxedo Mask said:**
> I've got a system with Lucid installed, and imagining I'd want to try out newer releases independent of it I have set aside space for another release. As it stands, my main drive - sda - is divided as follows:
sda1: boot
sda2: swap
sda3: extended with sda5 (Lucid) and sda6 (empty ext4)
sda4: home

I set up /boot, swp, /, and /home when I installed Lucid, telling it to format those partitions in the process. I'm trying to install Precise now, but in the partition manager there's an additional option at the bottom to define the location of the bootloader installation, and it gives all the drives/partitions available, including sda. If I remembered where the bootloader was installed in Lucid, I'd just point it to that location, but as it stands I don't know; I'm GUESSING it's in /dev/sda but I can't be sure, because as far as I know it was modified automatically on installing Lucid.

My question, then, is twofold: how can I find out where the mbr is located, and should I just pick that location from the dropdown menu in the Precise installer? Thanks.

EDIT: A new concern: When indicating the partition to use as /boot (i.e., /dev/sda1), I do not need to format it, correct? Thanks again.

Generally you do not need a boot partition, any reason why you have one?

---

### Post by Tuxedo Mask on 2012-05-26
I set one up when this machine had Windows and Ubuntu dualbooting off of it, and it became a habit to keep it around. I'd rather not remove it right now as shuffling that space over anywhere would involve moving the other partitions and taking hours to resolve itself.

---

### Post by oldfred on 2012-05-26
You cannot share a /boot, best not to have a separate one unless you have an old system that can only boot from first 137GB (BIOS limit). If you format your current /boot, you will not be able to boot the old install as that will erase its kernels & grub files.

You have to install grub2's boot loader to the MBR or sda, not a partition like sda1, sda2 etc.

While the intent of a separate /home is to make it easier to upgrade, trying to use it in both systems may lead to issues of compatibility. Software is designed to update so the new version will find all your old settings and update for the new version. But some software then may not like the new settings in the old version.

If just testing do not mount /home. If converting include the mount of /home in your new install but be sure NOT to format it. But not all apps may then work well in old install.

---

### Post by Tuxedo Mask on 2012-05-26
Can I copy the stuff in boot to the new root partition, then edit the fstab accordingly? I figure also that not defining a home partition for the new installation would leave the original intact, so it would truly be its own independent entity.

---

### Post by darkod on 2012-05-26
Man, you just don't listen. :)

Why would you wanna copy /boot? The kernels are different, the files are different.

The /boot folder/partition is not meant to be the same between different versions. Just let /boot to be a folder inside / for the new install, happy end.

---

### Post by Tuxedo Mask on 2012-05-26
> **darkod said:**
> Man, you just don't listen. :)

Why would you wanna copy /boot? The kernels are different, the files are different.

The /boot folder/partition is not meant to be the same between different versions. Just let /boot to be a folder inside / for the new install, happy end.

OK, yes, that certainly would make life a whole lot easier. For some reason I thought the new install would try to "see" the older one's boot partition.

Thanks to everyone for your help.

---

### Post by oldfred on 2012-05-26
Grub2's os-prober will find your old install and add an entry to your grub menu to let you boot it also.

If for any reason it does not add it as part of the install, just run this:

sudo update-grub

---

