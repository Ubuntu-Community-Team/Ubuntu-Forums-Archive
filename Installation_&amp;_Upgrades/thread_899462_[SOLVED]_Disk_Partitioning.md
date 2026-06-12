---
title: "[SOLVED] Disk Partitioning"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Armaron on 2008-08-24
I've installed ubuntu once on a machine and that time, it asked how much hard disk space I wanted to use to put the OS on. I found out that it took a part of that designated space for a "swap partition".

Now I'm buying a new pc, I'd like to know what this partition does and how big it has to be. Does it need a fixed size or is the size scalable with the size of the partition? In this PC I'm going to put a HD of 1 TB.

So it's a bit overkill to partition it all into one partition. That's why I want to know.

---

### Post by Pumalite on 2008-08-24
Get Gparted Live CD and make them 3 'new' partitions:
20 GB for '/'
The rest minus the amount of your RAM for /home
The amount of your RAM for /swap
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
When you finish, remove Gparted. Boot your Ubuntu Live CD, install, go 'Manual' and use the already prepared partitions.

---

### Post by kaibob on 2008-08-24
The following Ubuntu Swap FAQ provides some good information on your what does it do and how big does it need to be questions:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Armaron on 2008-08-24
Thank you very much guys. Both your replies were very helpfull and informative. Keep up the good work!

EDIT - Haha! I just got it. A swap partition is a dedicated part to store swap files. Man, sometimes I really need to just think a bit further than my nose is long (and I don't have a long nose ;)).

---

### Post by Rallg on 2008-08-24
Since you have such a large drive, you might consider making an extra partition for future use if you want to test-drive a different (or upgraded) Linux system. It won't need its own swap, since the single swap partition is common to various Linux, unless you have multiple Linux in action simultaneously. (Is that even possible?).

---

### Post by Armaron on 2008-08-26
> **Rallg said:**
> unless you have multiple Linux in action simultaneously. (Is that even possible?).

Yes, but then you'd have to work with virtual machines, Quam (I think) is the native Ubuntu virtualization way. But personally I prefer VMware Workstation or VirtualBox. Imo, Xen (from Citrix) just doesn't have the maturity to handle virtual machines properly.

If you want to run multiple OS' simultaniously without Windows, Linux or Mac as basis, you'd need to go for a server edition where the virtualization works as the OS. I'd recommend VMware VI server.

(I did my thesis on virtual machines.)

---

