---
title: "[SOLVED] Xp OVER Ubuntu 8.04"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by swankish on 2008-10-19
I currently have Ubuntu 8.04 and love it.  However, I would like windows for certain programs that do not run well in Wine.  Am I able to somehow make a 15-20 gig partition over Ubuntu without having to reinstall Ubuntu?  I dont want to reinstall if I don't have to.

---

### Post by Idefix82 on 2008-10-19
You won't need to reinstall Ubuntu. You can use GParted from the liveCD to create a new partition and format it as NTFS, then install Windows into this partition. After that you will need to restore GRUB. For that there are numerous howtos around, eg here:
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11")

---

### Post by swankish on 2008-10-19
GParted. Is that on the Windows XP live CD you mean?  or the Ubuntu one?  I'm pretty sure I know what you mean but I want to make sure haha

---

### Post by fikelfikel on 2008-10-19
> **swankish said:**
> GParted. Is that on the Windows XP live CD you mean?  or the Ubuntu one?  I'm pretty sure I know what you mean but I want to make sure haha

He means the Ubuntu live CD. There is no such thing as a live CD with Windows.

There is another way. Have the XP disc in your PC and in the BIOS (Boot Menu. Usually contained at startup) select boot from CD. When the Windows Installation has loaded, you can manage partitions, add one. Sometimes it dosn't work, so you'll need the Vista disc, or trial.

---

### Post by swankish on 2008-10-19
ok so I can put the liveCD in and create the partition, tehn put the windows CD in and install?  I do have both CDs

---

### Post by Idefix82 on 2008-10-19
Yep.
Remember that you won't be able to boot into Ubuntu after that until you restore GRUB into the MBR. This is easily done, though.

And also, while the whole procedure **should** work, resizing partitions is always a risk. So doing a backup of important data is highly recommended.

---

### Post by swankish on 2008-10-19
thanks a bunch

---

