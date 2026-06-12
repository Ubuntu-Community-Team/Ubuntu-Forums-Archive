---
title: "Installing Kubuntu with software RAID"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by CopaceticOpus on 2008-05-19
I'm planning to do a fresh install with Kubuntu Hardy Heron. I will be reformatting two drives and creating a RAID 1 setup using software RAID.

In the past (around 6.10 or so) I had to do this using the server install CD, since the regular Kubuntu installer didn't support RAID partitioning. Is that still the case, or is it possible to use my Kubuntu 8.04 CD for this installation?

---

### Post by Marco7 on 2008-05-19
There is still no soft/fake RAID support, however, as I understand it Linux has excellent native support for "real" raid, so If your not running a dual boot system with, for example, a windows operating system that requires a soft raid, I believe it may be simpler to do it the Linux way.

Or check the [FakeRAIDHowto...]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by CopaceticOpus on 2008-06-11
Actually, Ubuntu has supported software RAID back to at least 6.06. I know because I use it. I was just wondering if I can use the Kubuntu install disc rather than the Ubuntu server install disc to set it up.

From the limited options I am seeing on the Kubuntu install disc, it appears I do need the server install disc.

EDIT: In fact what is needed is the "Alternate" install CD. See the following:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

EDIT 2: After further review, the text-based installer on the Alternate CD is also an option from the Kubuntu 8.04 install DVD. I don't know if it's an option on the 8.04 CD or not. The Kubuntu download page could do a better job of explaining all this...

---

