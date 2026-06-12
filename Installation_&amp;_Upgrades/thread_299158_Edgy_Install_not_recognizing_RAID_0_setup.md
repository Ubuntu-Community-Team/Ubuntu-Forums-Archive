---
title: "Edgy: Install not recognizing RAID 0 setup"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by acascianelli on 2006-11-13
I'm trying to setup Edgy on my main desktop at home.  I'm running a Abit IC7-Max3 with 2x160gb SATA drives.  At first I tried connecting them to the onchip Intel RAID controller.  But this RAID controller is software driven and does not work in Linux, I've been told this by many people.  Now I tried to connect the hard drives to the Sil3114 RAID controller, think that being a hardware based controller it would work no problem.  However, the install does not recognize the RAID 0 array on that controller and instead sees two separate drives.

Is there anything else that needs to be done in order for the Ubuntu install to be able to work with the RAID controller I'm using?

Hopefully someone can help me with this, I'm ditching Windows XP once and for all.  If I can get Ubuntu working ok on this system then I'll be completely free of any Microsoft and non-free software.

UPDATE:

After doing a little research into my problem I think I have to mess around with DMRaid.

---

