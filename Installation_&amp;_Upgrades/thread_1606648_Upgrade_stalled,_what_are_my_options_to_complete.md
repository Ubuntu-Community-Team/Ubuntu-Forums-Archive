---
title: "Upgrade stalled, what are my options to complete?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by GROwen on 2010-10-26
Hi all,

Looking for a bit of advice before I jump into doing a clean install.

I was upgrading to 10.10 (from 10.04) but my PC stalled when the installer reached updating of Xorg files. From memory it was around 59% complete.

After restart the machine would only boots to command line and I can't manage to boot into recovery mode. I've tried hitting 'left shift' to get into recovery options without any luck, then I tried 'esc' with the same result.

After logging in to command line I'm told there are no upgrades or security updates available.

What options should I be looking at to try and rectify this before jumping into doing a new install over the OS partition from the LiveCD?

Thanks in advance for any help.

---

### Post by whoop on 2010-10-26
> **GROwen said:**
> Hi all,

Looking for a bit of advice before I jump into doing a clean install.

I was upgrading to 10.10 (from 10.04) but my PC stalled when the installer reached updating of Xorg files. From memory it was around 59% complete.

After restart the machine would only boots to command line and I can't manage to boot into recovery mode. I've tried hitting 'left shift' to get into recovery options without any luck, then I tried 'esc' with the same result.

After logging in to command line I'm told there are no upgrades or security updates available.

What options should I be looking at to try and rectify this before jumping into doing a new install over the OS partition from the LiveCD?

Thanks in advance for any help.

If you have your data backed up, there are various things you could try...
If you have network connectivity, you could try:
```

sudo bash
aptitude update
aptitude dist-upgrade

```
and see what happens...

---

### Post by night_fox on 2010-10-26
That is a good idea. If you want to try more stuff while on the internet, run the LiveCD, then go to terminal

```
sudo mkdir /media/disk
sudo mount -t <file system> /dev/sd<your root> /media/disk
sudo mount -t proc /proc /media/disk/proc
sudo mount /dev /media/disk/dev -o bind
sudo chroot /media/disk
```

now run commands as if you were in that system.

---

### Post by GROwen on 2010-10-26
Thanks guys, I'll give this suggestion below a go. My only concern might be about data, I've got my OS on a separate  partition to music and var, will running those commands delete those  partitions as well?

> sudo bash
aptitude update
aptitude dist-upgrade

---

### Post by whoop on 2010-10-29
> **GROwen said:**
> Thanks guys, I'll give this suggestion below a go. My only concern might be about data, I've got my OS on a separate  partition to music and var, will running those commands delete those  partitions as well?

Those commands should not delete anything. The should only overwrite existing packages with newer versions of those packages...

---

