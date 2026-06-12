---
title: "Newbie question: Using Alpha 6 right now, how would I upgrade to Beta?"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-09-24
So I'm using Alpha 6 right now and I like it because of the improved Intel graphics drivers. Beta comes out in a week or so, so I wanted to know what would be the most painless way of upgrading to Beta, and then the final RC when it is out at the end of October? My linux partitions are split into 2 from a extended partition. I have a "/" logical partition and a /root partition. 

Thanks.

---

### Post by Longinus00 on 2009-09-24
You don't have to do anything. Just keep upgrading and you'll always have the newest version.

---

### Post by rburkartjo on 2009-09-24
bridge ujst keep updating and as long as nothing crashes you will have the beta, rc and final

---

### Post by bridgetothesun on 2009-09-25
thanks!

---

### Post by Sophont on 2009-09-25
> **bridgetothesun said:**
> So I'm using Alpha 6 right now and I like it because of the improved Intel graphics drivers. Beta comes out in a week or so, so I wanted to know what would be the most painless way of upgrading to Beta, and then the final RC when it is out at the end of October? My linux partitions are split into 2 from a extended partition. I have a "/" logical partition and a /root partition. 

Thanks.

The others already explained that by updating you'll eventually will have beta/RC and then final. The Alpha 1-6 releases are just snapshots. They aren't special versions. There's no upgrades to Alpha 6 that are different from updates to Alpha 5. Except for your individual cconfigurations the Beta snapshot will be the same version as initially installing Alpha 6 and then getting all updates to the day Beta is made.

Regarding the "most painless way" - well - that means avoiding major breakage.
You can have a relatively high chance (but still not 100% safe) of avoiding a broken system by
1) check this forum before upgrading - if suddenly threads show up that mention major breakage wait until the "solved" messages come in - or look at the mentioned bug reports.
2) Avoid Partial upgrades in UpdateManager
3) Install VirtualBox (VB OSE is in the repo), install another Karmic in a VM - always upgrade that first - check if anything important to you is broken and if it still ca restart - then do the upgrades on metal right after the tests in the VM.

---

