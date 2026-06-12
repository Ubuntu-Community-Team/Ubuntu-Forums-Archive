---
title: "dual boot"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by shoeshrimp on 2008-01-22
Hey guys,

If I do a dual boot with Windows Xp and Ubuntu, will I be able to access some files (e.g. music files) that are on my windows file system while running ubuntu, or will they be completely invisible to each other. I don't have the hard drive space to have them in 2 places...

Cheers,

Tom

---

### Post by mikewhatever on 2008-01-22
Yes, you will, if you chose to run the latest version (7.10).

---

### Post by Liam-Gorham on 2008-01-22
Cant see why not the only tiny problem which you could have is the format of files when you get it working but there are quite some amount of codecs for it. Ive done this before with a mac and windows and it worked fine. Ubuntu is a good operating system it should work.

---

### Post by shoeshrimp on 2008-01-22
Brilliant, thank you - I'm moving to Ubuntu in the vain hope that it might have better control over my USB ports - my laptop on windows + usb devices just leads to extreme confusion culminating in my laptop refusing to recognise some devices sometimes (but does othertimes), individual ports giving up occasionally (power issue) etc...

hopefully Ubuntu will be better!

Tom

---

### Post by rosegarden78 on 2008-01-22
The program is called NTFS or FUSE if that's the format of your Windows partition.  If it's FAT32 then it's handled automatically in later versions.  Check Synaptic or Add/Remove Programs for the term "ntfs" and "fuse."  In earlier version sometimes you had to mount it by hand by looking for the device in /etc/fstab or /etc/mtab and the using the mount /dev/sda# /mnt/yourMountFolder command.

EDIT: If using USB device not in files above it's located in /dev folder probably /dev/sdb1.

---

### Post by shoeshrimp on 2008-01-22
> **rosegarden78 said:**
> The program is called NTFS or FUSE if that's the format of your Windows partition.  If it's FAT32 then it's handled automatically in later versions.  Check Synaptic or Add/Remove Programs for the term "ntfs" and "fuse."  In earlier version sometimes you had to mount it by hand by looking for the device in /etc/fstab or /etc/mtab and the using the mount /dev/sda# /mnt/yourMountFolder command.

sorry - I'm confused - do I have to install "FUSE" on ubuntu if my windows system is NTFS?

Ta

---

### Post by -1nverse on 2008-01-22
New user here so correct me if I'm wrong but my 6 NTFS  partitions were available from the first time I booted into 7.10. No setup necessary.

---

### Post by shoeshrimp on 2008-01-22
Cool - so people seem to recommend dual boot as a good idea. How much file space will the Ubuntu install take?

---

### Post by shoeshrimp on 2008-01-22
Oooh, and another really simple question, but that I don't know the answer to - how do I chose which OS to boot into at startup once it's all installed?

Ta!

---

### Post by mikewhatever on 2008-01-22
> **shoeshrimp said:**
> Oooh, and another really simple question, but that I don't know the answer to - how do I chose which OS to boot into at startup once it's all installed?

Ta!

You'll be presented with GRUB menu screen (similar to this [http://users.bigpond.net.au/hermanzone/p15.htm#gui](http://users.bigpond.net.au/hermanzone/p15.htm#gui)) and be able to chose witch OS to boot.

---

### Post by rosegarden78 on 2008-01-22
I've never interfaced to NTFS only FAT32.  The programs FUSE and ntfs-3g are in the repositories and they work fine. 

EDIT: I no longer dual boot give Ubuntu whole drive and use XP in VirtualBox.

---

### Post by rosegarden78 on 2008-01-29
See edit above also: Use XP in VirtualBox it networks automatically with Ubuntu desktop just a thought ...

---

