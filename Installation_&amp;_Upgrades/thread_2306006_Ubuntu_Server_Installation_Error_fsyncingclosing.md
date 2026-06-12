---
title: "Ubuntu Server Installation: Error fsyncing/closing"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by gamelife on 2015-12-11
My system:
- HDD1 at SATA 1, GPT, Windows installed
- HDD2 at SATA 2, GPT, Ubuntu Desktop installed <-- I want to install Ubuntu Server 15.10 here
- HDD3 at USB (external), MBR
- HDD4 at USB (external), MBR <-- Ubuntu Server 15.10 ISO burned here

I booted to HDD4 and started installation. When entering disk partition, I got "Error fsyncing/closing" on sda (HDD1) and sdb (HDD2).
I clicked Retry, the same; I clicked Ignore, then got this disk layout: sda (HDD3), sdb (HDD4), sdc (HDD1), sdd (HDD2). That seems wrong, so I aborted installation there.

Strange, I have just installed Ubuntu Desktop 15.10 successfully. I got "Error fsyncing/closing" too, but on sdc (HDD3). Since HDD3 is irrelevant, I just clicked Ignore and continued.
Now the same error happened again - this time on HDD1 and HDD2.
Any idea?

---

### Post by ptn107 on 2015-12-11
Make sure the GPT on /dev/sdd (your hdd2) is wiped.  Gparted used to give me that error on some of my GPT disks.

[https://www.bfccomputing.com/zero-a-gpt-label-using-dd/]("https://www.bfccomputing.com/zero-a-gpt-label-using-dd/")

Most of what I read online says that error is indicative of drive failure but I don't believe that.

---

### Post by gamelife on 2015-12-12
I just installed again, this time those "Error fsyncing/closing" errors didn't happen.
What I did: installed Ubuntu Server ISO to a newly bought USB memory stick, unplugged HDD3, and replaced HDD4 by the new USB memory stick.

Nevertheless, I still could not get the installation done. After the step "Choose software to install", the screen showed "Retrieving file 1 of 238" and froze forever.
Suggestions?

---

