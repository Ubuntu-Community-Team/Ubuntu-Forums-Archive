---
title: "Installing 11.10 on a small HD"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by julian.irwin on 2011-10-14
My netbook has an 8GB SSD and a 4GB SSD. I have run every version of Ubuntu since 10.04 on it without a problem. This morning I tried to install 11.10 after formatting both drives. The installer won't let me hit the 'continue' button on the second pre-installation screen because I don't have 8.6GB of free space on a single drive. I usually mount root on one drive and /home on the other. I have never had a problem like this before.

EDIT: I noticed that on all of the installation screenshots that I found on the web the minimum recommended HD size was just 4.4GB. Why is mine different?

Is ubuntu turning into windows? Why doesn't the installer trust my judgement!!
Thanks,
Julian

---

### Post by Rille_lkp on 2011-11-10
I ran into the same problem trying to install 11.10 to an 8GB USB.
All information i could find pointed to that the CD-install should fit on less then 8GB while the DVD-install requires 8.6GB.

After some testing i found something strange:
- Put downloaded ISO on a 8GB USB-stick and try to install Ubuntu from that: Installation requires 8.6GB HDD
- Put downloaded ISO on a 1GB USB-stick and try to install Ubuntu from that: Installation requires 4-5GB (can't remember exactly) HDD

So it seems that if you put your downloaded ISO on a large medium it thinks you have the DVD-install even though you don't and the installation requires 8.6GB HDD.

---

