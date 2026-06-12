---
title: "Upgrade to 9.10 from 9.04"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by truckbytes on 2010-06-28
I am considering using the upgrade utility in the "Update Manager" however I am concerned that if I upgrade to 9.10 I could loose data. Especially all the data within my Virtual Box. I could use any suggestions, advice, experiences or recommendations.

Thank You
Joel

---

### Post by Paddy Landau on 2010-06-29
[LIST=1]
[*]Back up *all* your important data. There is always a small chance of data loss when upgrading.
[*]Before I upgrade, I back up my entire disk using [CloneZilla]("http://clonezilla.org/"). That way, if the upgrade messes up, I can restore the entire disk without having to reinstall.
[*]Double-check that you really have backed up safely.
[*]Go for it.
[/LIST]

---

### Post by howefield on 2010-06-29
> **truckbytes said:**
> I am considering using the upgrade utility in the "Update Manager" however I am concerned that if I upgrade to 9.10 I could loose data. Especially all the data within my Virtual Box.

Sounds like you need to revisit your backup strategy, irrespective of whether you are upgrading or not. Disks can die, mistakes can happen, data can be lost.

I'm with Paddy Landau re Clonezilla, but to specifically look at your point re virtualbox. You can backup your images with

```
vboxmanage clonevdi source destination
```

---

### Post by stlsaint on 2010-06-29
I use the Simple Backup/Restore Suite which comes in all releases. Its very effective and works fast.

---

### Post by truckbytes on 2010-07-01
Thanks guys! I appreciate it.

Joel

---

### Post by Paddy Landau on 2010-07-02
Please mark the thread as solved if you feel that this has solved your problem. ;)

---

