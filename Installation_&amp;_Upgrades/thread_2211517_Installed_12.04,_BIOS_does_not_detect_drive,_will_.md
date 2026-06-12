---
title: "Installed 12.04, BIOS does not detect drive, will not boot"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by paultksakamoto on 2014-03-16
Hello,

I have installed Ubuntu 12.04.4 on a drive. Now the BIOS does not detect the drive and I cannot boot into Ubuntu. I have run Boot Repair ([http://paste.ubuntu.com/7103063/](http://paste.ubuntu.com/7103063/)) to no effect. 

Specs:
AMD Phenom X2 840
ASUS M4A87TD
4gigs RAM
R7 240
2TB HDD

I am quite unable to fix this issue. I've spent hours trawling these forums and the internet to find a solution. Something something MBR something something partition BIOS something

Please send help :)

---

### Post by Mark Phelps on 2014-03-16
> Now the BIOS does not detect the drive

That's confusing -- because the Boot-Repair log clearly shows that it sees the drive and the partitions on it.

So, HOW are you determining that the BIOS is not seeing the drive?

---

### Post by paultksakamoto on 2014-03-16
> **Mark Phelps said:**
> So, HOW are you determining that the BIOS is not seeing the drive?

When I go into the BIOS it lists 6 possible SATA connections. All of them are [Not Detected].

---

### Post by oldfred on 2014-03-17
Some older BIOS will not boot from large partitions or they have a limit of 137GB. So / (root) must be fully inside the first 137GB with rest of drive as /home. Or you need a separate /boot fully inside the first 137GB.

If system is older it may not even see a new very large 2TB drive. Is BIOS up to date, sometimes they have fixes for those issues. Did BIOS show drive before?

---

