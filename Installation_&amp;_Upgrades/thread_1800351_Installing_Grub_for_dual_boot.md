---
title: "Installing Grub for dual boot?"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2011-07-08
11.04 installed on free space I had setup but it didn't install Grub2 for a dual boot (with Windows 7 Pro).  It may have gotten confused with my disk setup.

Drives and their groupings (Windows lingo):
- Windows 7 Pro on C-drive (appears to be sdb2), it is a SSD
- The free space was setup on this SSD and Ubuntu is located on sdb5 (Linux) and sdb6 (swap space).
- Applications stored on D-drive (RAID0 with 2 small SSDs using RST (Intel Rapid Storage Technology).
- data on a RAID card using HDs in RAID0.
Small wonder it got confused, if that is the problem.

I have a LiveCD I can use to boot, is that the best?  What are the commands to install.  Is there a better way?

Many thanks for assistance!!

---

### Post by deeppow on 2011-07-09
Found what I needed here, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

### Post by lisati on 2011-07-09
I could mark the thread as "solved" but it is better if you do it.... :)

---

