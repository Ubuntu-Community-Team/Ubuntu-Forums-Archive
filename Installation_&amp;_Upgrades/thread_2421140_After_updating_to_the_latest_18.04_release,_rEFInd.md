---
title: "After updating to the latest 18.04 release, rEFInd bypassed (boot coup)"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by mbenson2 on 2019-06-17
I'm using a 2007 iMac, dual boot with El Capitan and Ubuntu 18.04. rEFInd was installed through macOS. After the latest Ubuntu update, I experienced a boot coup in which rEFInd is bypassed and the computer goes straight to grub. I used the refind-mkdefault command to no avail. It reported that it worked, and I confirmed this through efibootmgr, but this has not solved my problem. I cannot use bless in macOS to restore rEFInd as the default boot program because of SIP (I can't start in recovery mode using normal commands. I was able to do it before through rEFInd). I also tried reinstalling rEFInd through Ubuntu, although this has not worked either. I was thinking it might be helpful to downgrade to a version of macOS that does not have SIP. Does this make sense? I would really appreciate any responses.

---

