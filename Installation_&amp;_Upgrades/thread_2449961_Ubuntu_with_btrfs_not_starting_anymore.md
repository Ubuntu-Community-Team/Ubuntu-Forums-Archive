---
title: "Ubuntu with btrfs not starting anymore"
date: 2020-09-04
forum: Installation &amp; Upgrades
---

### Post by dorpapst on 2020-09-04
Yesterday, I installed Ubuntu 20.04 with btrfs and encryption, following that manual here:
[https://mutschler.eu/linux/install-guides/ubuntu-btrfs/](https://mutschler.eu/linux/install-guides/ubuntu-btrfs/)

It worked pretty well, until I restarted the computer.
After I did so, it asked me for the encryption pw for (hd6,gpt3) like every time.
Afterwards, I came into the grub menu, without any more response.
Ls gives me:
error: failure reading sector from hd0
... for hd0, hd1, hd1 (twice), hd2, hd2, hd3, hd3, hd4, hd4

Everything seems normally and its weird, that the second boot did not work, while I was working in the system the entire day.
lsblk shows the following (Sorry, I am not copying but typing, because its another PC):
sda 931.5G 0 disk
-sda1 512M 0 part
-sda2 16GB 0 part [SWAP]
-sda3 915G 0 part
—cryptdata 915G 0 crypt /mnt

(because I was currently on an live USB stick, having encrypted the cryptdata when I put out that information)
sdb 931.5G 0 disk
-sdb1 200 0 part /boot
-sdb2 931.5G 0 part

sda is my external disk on which I am installing (due to portability) and sdb is the internal (apple) disk.

mount -av shows:
 /                        : ignored
 /boot/efi                : successfully mounted
 /home                    : successfully mounted
 none                     : ignored

I am 100% sure to have set the UUIDs properly, following the manual, they did not chance since the first boot.

Is there somebody having an idea how I can solve that?
I wanted to use boot-repair, but that is not working for encrypted devices.

Many greetings

---

### Post by TheFu on 2020-09-05
Please post commands and output wrapped in "code tags" - you can edit any post you've made if the thread isn't closed.

I suspect btrfs has more to do with this than anything else.  I've been using encrypted installs (dm-crypt+LUKS) since around 2014, but with LVM and ext4.  So far, no issues beyond the odd grub update problem that happened once, a few years ago.  However, I'm not on 20.04 for any encrypted installations and I cannot use BTRFS for a number of reasons.

I'm never 100% sure about anything.
My layout: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) Notice that encrypted "container" is a full partition, then the PV, VG, and LVs are inside that LUKS encrypted container

---

