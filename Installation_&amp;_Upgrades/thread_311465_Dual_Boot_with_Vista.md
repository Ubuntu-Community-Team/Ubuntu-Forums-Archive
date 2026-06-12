---
title: "Dual Boot with Vista"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by goldenatom on 2006-12-02
Is it possible to install Vista (RC2) if I already have linux installed? If so, can someone point me in the right direction?

---

### Post by pestilence4hr on 2006-12-02
I would think the procedure would be no different than for any other version of windows.  The main steps are:  resize your partitions to make room for a windows partition (if you don't have one already).  Install windows on that partition.  Boot off a livecd and re-install grub on the MBR.

---

### Post by jdhore on 2006-12-02
yeah, i installed Vista RTM then Ubuntu 6.10 and it worked perfectly.

IMPORTANT: DO NOT use any apps to resize your Vista NTFS partition to make room for Ubuntu or you will screw up your Vista partition. if you don't have unpartitioned space on the HD already, reformat and resize your Vista partition...you and your computer will thank you for it

---

### Post by goldenatom on 2006-12-03
I already have edgy installed on the system that I want to put RC2 on, do I have to do something different?

---

### Post by jdhore on 2006-12-03
> **goldenatom said:**
> I already have edgy installed on the system that I want to put RC2 on, do I have to do something different?

OK, i apologize...i thought Vista was installed first...then you'll be fine as long as you know that after you install Vista, you will have to reinstall GRUB to the MBR

---

