---
title: "Set up a new install of Lubuntu with a software raid 0 configuration."
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by zacmitche11 on 2019-04-28
Can someone please provide the instructions to do so?

---

### Post by zacmitche11 on 2019-05-03
No one knows how to setup raid 0 in a Lubuntu live then install it?

---

### Post by oldfred on 2019-05-03
I do not know nor use RAID.

But there are multiple types of RAID. BIOS (aka fakeRAID), specific hardware card, and Linux software mdadm.
Which are you planning to use?
Advantages & disadvantages of each.

But RAID 0 not recommended for normal desktop use. It is used by those who have all data on a server or just game and do not save any data on system. When one drive fails, you lose all data from both drives.

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)


Is system UEFI or BIOS?

Server install generally required for RAID, but then you still can add desktop of choice.

Install Ubuntu 18.04 desktop with RAID 1 and LVM on machine with UEFI BIOS
[https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios](https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios)
How to install Ubuntu  64-bit with a dual-boot RAID 1 partition on an UEFI/GPT system?
[http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi](http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.

---

### Post by zacmitche11 on 2019-05-04
Thanks for the reply, I have a bios. It only supports raid 1. I'm aware of the risks of data loss. I don't keep anything important on the PC. Occasional games. I can back up my saves somewhere else. I would perfer Lubuntu for resource reasons.

---

### Post by zacmitche11 on 2019-05-04
Also I tried server, but it needed a lan connection or something. I guess the alternate version doesn't, but I don't believe it has a GUI.

---

### Post by zacmitche11 on 2019-05-05
I tried the Ubuntu way and the install hangs, there isn't way to do this from Lubuntu live?

---

