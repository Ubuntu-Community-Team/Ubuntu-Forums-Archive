---
title: "Partitioning help needed - Triple boot with full disk encryption"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by wconstantine on 2011-03-28
I need some help to structure the layout of my partitions. I'm installing Windows 7, Backtrack 4 R2 and Ubuntu 10.10 Desktop on my laptop. I've got a 500 GB HDD named sda. 

I've already installed Windows 7. It's my opinion that it's easiest to begin with Windows. 

The partitions look like this right now:
/dev/sda1 ntfs System reserved 100 MB
/dev/sda2 ntfs Windows OS 100 GB

The Windows installation is unencrypted and I want it to stay that way. It's only there in case my laptop gets stolen, I've installed various nasty things there. :)

The Backtrack 4 installation will also be given 100 GB space, I want it to be encrypted. The Ubuntu installation should get the rest of all the remaining space and preferably be encrypted but it's not 100% necessary. 

So, got any ideas how I should partition this? There's a limit on 4 primary partitions? How do I circumvent this? There should be one dedicated GRUB partition which will point to each of the installations own boot loaders?

---

### Post by Sean Moran on 2011-03-28
> **wconstantine said:**
> I need some help to structure the layout of my partitions. 

The partitions look like this right now:
/dev/sda1 ntfs System reserved 100 MB
/dev/sda2 ntfs Windows OS 100 GB

There's a limit on 4 primary partitions? How do I circumvent this?

Make either /dev/sda3 or /dev/sda4 an EXTENDED partition, so you can create a good range of logical partiitons inside the extended partition.

Linux root (/) and /home/ and SWAP partitions are all quite happy as logical partitions within an extended partition, but GRUB will want to be somewhere that's bootable, as you probably already know.

---

### Post by wormyblackburny on 2011-03-28
It really depends on what you will be using each OS for as far as deciding the size of the partitions. As far as Grub, just make sure you install ubuntu last and it will install grub and detect all of the operating systems.

---

### Post by wconstantine on 2011-03-28
> **Sean Moran said:**
> Make either /dev/sda3 or /dev/sda4 an EXTENDED partition, so you can create a good range of logical partiitons inside the extended partition.

Linux root (/) and /home/ and SWAP partitions are all quite happy as logical partitions within an extended partition, but GRUB will want to be somewhere that's bootable, as you probably already know.

Is it possible for me to have both / for BT and Ubuntu in the same extended partition? The only partition that needs to be primary is the dedicated GRUB partition?

This is how I plan to partition my system now:

Primary /dev/sda1 Windows bootloader 100 MB
Primary /dev/sda2 Windows OS 100 GB
Primary /dev/sda3 DEDICATED GRUB BOOTLOADER 100 MB
Extended /dev/sda4 368 GB
Logical /dev/sda5 BT4 BOOT 256 MB
Logical /dev/sda6 UBUNTU BOOT 256 MB
Logical /dev/sda7 BT4 ROOT 100 GB
Logical /dev/sda8 UBUNTU ROOT 270 GB

Could this work?

---

### Post by Dutch70 on 2011-03-28
> **wconstantine said:**
> Is it possible for me to have both / for BT and Ubuntu in the same extended partition? The only partition that needs to be primary is the dedicated GRUB partition?

This is how I plan to partition my system now:

Primary /dev/sda1 Windows bootloader 100 MB
Primary /dev/sda2 Windows OS 100 GB
Primary /dev/sda3 DEDICATED GRUB BOOTLOADER 100 MB
Extended /dev/sda4 368 GB
Logical /dev/sda5 BT4 BOOT 256 MB
Logical /dev/sda6 UBUNTU BOOT 256 MB
Logical /dev/sda7 BT4 ROOT 100 GB
Logical /dev/sda8 UBUNTU ROOT 270 GB

Could this work?

No, you don't need a boot partition for Ubuntu, however you do need a Swap partition, equal to the size of your RAM.

Have a look at mine, although I don't have windows on this hdd.

---

### Post by wconstantine on 2011-03-28
Totally forgot about swap! But since I got 4GB RAM I guess I hardly need 4GB swap space. Thanks.

---

### Post by Dutch70 on 2011-03-28
You may also want to make Ubuntu "/" about 15-20GB and create a /home partition with the rest of the 270 or so GB. That way if/when you have to reinstall, you won't lose anything, not even your settings.

---

### Post by wconstantine on 2011-03-28
> **Dutch70 said:**
> You may also want to make Ubuntu "/" about 15-20GB and create a /home partition with the rest of the 270 or so GB. That way if/when you have to reinstall, you won't lose anything, not even your settings.

I'm regularly backing up my laptop home directory to a file server.  But it doesn't hurt I guess. :)

---

### Post by Dutch70 on 2011-03-29
Nice! It's up to you, but when the day comes that you have to reinstall, you'll still be glad you have a separate /home. When you can have your OS on a different partition that your files, it's just a smart move. You can have over 60 logical partitions, so that's not an issue.

Best regards
Dutch

---

