---
title: "Upgrading from Meerkat to Narwhal, will it harm Windows?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by mclizardman on 2011-05-08
I installed Maverick Meerkat using Wubi inside of Windows 7, so it's not a dedicated partition, and now I want to upgrade to the latest version. If I upgrade, will it override windows 7? maybe a little paranoid, but I spent 200 dollars for 7 and I don't want to see it gone. Also, I did read something where this one guy while upgrading lost the windows part of his machine. I just want to be sure that my Windows is safe, so will upgrading harm anything?

---

### Post by Quackers on 2011-05-08
I'm not sure where wubi is concerned. It could certainly have an effect on grub. Maybe if you take a look in the Wubi Megathread Sticky at the top of the page you will find something.
On a different note, you should make backups of your system (maybe with clonezilla or similar) so that a disaster can be averted :-)
I presume that if you've spent $200 on Windows 7, you will have an installation disc? That is some comfort - but not for your data :wink:

---

### Post by bcbc on 2011-05-08
It's safe. I've tested a number of wubi upgrades to Natty Narwhal. The worst thing that is likely to happen is that the upgrade will fail - maybe if you are low on space, or you have some ppa's or some custom setup... so to be safe, backup your virtual disks prior to upgrading. They can be found in c:\ubuntu\disks\*.disk (change drive designation from c:\ as appropriate). The wubi upgrade issues with grub2 that we've seen in 10.04 and 10.10 have now been fixed for Natty.

However, I agree with Quackers - if you're running a dual boot (or even if you're not) it's a good precaution to have a system image and current backups so you can recover from disaster. Even on a single OS setup it's important as e.g. the drive could fail.

---

### Post by Quackers on 2011-05-08
Thanks bcbc for the info re upgrading wubi. I'm always unsure where wubi is concerned. I haven't used it as I'm unsure of its impact on an already dual-booted, twin hard drive system. It's a lot to risk :-) (even with clonezilla images!)

---

### Post by bcbc on 2011-05-08
> **Quackers said:**
> Thanks bcbc for the info re upgrading wubi. I'm always unsure where wubi is concerned. I haven't used it as I'm unsure of its impact on an already dual-booted, twin hard drive system. It's a lot to risk :-) (even with clonezilla images!)

No prob :)
Wubi's safe to install on an existing dual boot. There is no conflict.

---

### Post by mclizardman on 2011-05-08
Okay thanks for the reply, but I'm not using Wubi to upgrade, I just used that to install the meerkat version, I am not doing a fresh install. I was just wondering if upgrading from the update manager would harm anything on windows.

---

### Post by Quackers on 2011-05-08
It appears not :-)
Thanks again bcbc.

---

