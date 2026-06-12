---
title: "2 Windows + Ubu 9.10"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Buckethead90 on 2010-02-25
I have Windows 7 and Windows XP already set up as a dual boot.

With partitions in the order:
[Windows XP] [Windows 7] [    Free space    ]

If I set up Ubuntu in the free space partition, will GRUB recognise that I have two Windows operating systems? will it be be able to load all three OSs?

If no are there any preliminary measures I should take?

---

### Post by Mark Phelps on 2010-02-25
> **Buckethead90 said:**
> I have Windows 7 and Windows XP already set up as a dual boot.

With partitions in the order:
[Windows XP] [Windows 7] [    Free space    ]

If I set up Ubuntu in the free space partition, will GRUB recognise that I have two Windows operating systems? will it be be able to load all three OSs?

Yes ... it should.  If you're installing 9.10 and it doesn't recognize them, after install, open a terminal and run "sudo update-grub".  Realize that you will get a menu entry to the MS Windows selection menu, not to each individual MS Windows OS.

> If no are there any preliminary measures I should take?

If you want to preserve the ability to boot into Win7, should anything go wrong during the Ubuntu install, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  You will need that later to restore your MS Windows MBR -- should you ever decide to remove Ubuntu.

---

### Post by Buckethead90 on 2010-02-25
Ok thanks a lot! I'll give it a try!

---

