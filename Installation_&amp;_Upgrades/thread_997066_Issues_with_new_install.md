---
title: "Issues with new install"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by jon.uk on 2008-11-29
I'm just setting up a new build and was having a few problems and wondered if anyone could help, or point me in the right direction (had a search on web and docs and couldn't find).

I've got 4 HDs (0.5TB each) in a RAID 01 configuration. In the RAID BIOS (onboard the P45 chipset MB I have) I partitioned into 700GB for one and the rest in another. I installed Windows (Vista, 64bit) on the larger one, and as I expected it was all transparent as it only saw a generic 700GB disk and a ~250GB one.

Now I was planning to install Ubuntu in a dual boot config. using the other area. I can boot into the latest install CD but when I come to install it gives me the option to partition one of my 4 HDs (which would destroy my existing setup) - is there any way to get it to see my existing RAID partitions as HDs and install on the ~250GB one?

I'm a fan of this distro. since I recently setup a file/dns/web server which was very straight-forward despite being quite new to Linux.

(edit: ironically, my issue looks quite similar to the previous thread! 'Can not see existing windows partition during installation')

Ta, 
 Jon.

---

### Post by lemming465 on 2008-12-01
The Intel "fakeraid" with the ICH10R chip isn't well supported by Ubuntu yet.  9.04 next spring may be better; or maybe try OpenSuSE if you are in a hurry.  Or redo the disk system with at least one non-RAID disk for Ubuntu.  Or buy an external disk and put Ubuntu on that.

---

