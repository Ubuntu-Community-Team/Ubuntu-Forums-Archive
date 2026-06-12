---
title: "Can Ubuntu Server be installed on Intel Hardware that has ESRT2/RSte raid controller?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by javadevmtl on 2012-12-05
The machine is an Intel R2000GZ/LZ family with supports ESRT2 and RSte RAID.


I searched around and some people suggested to use ACHI mode and then use software raid mdm something...

In the bios I set the controller to ACHI mode and the controller to RSTe. When the machine boots, the 5 drives show as non raided. Then Ubuntu setup begins and works all teh way to the part when it's time setup the volumes.

The setup wizard detects that there is RAID drives and asks if I want to initial them. I click yes and then it does some work and then the wizards prompts me to try using iSCI or to redo the partitions.

Other options I tried in the BIOS prompted the Ubuntu Setup wizard to set a location for disk drivers.

Any ideas?

Thanks

---

### Post by javadevmtl on 2012-12-05
Any ideas? Thanks

---

