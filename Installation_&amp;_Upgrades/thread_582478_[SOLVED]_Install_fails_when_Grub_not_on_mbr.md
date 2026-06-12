---
title: "[SOLVED] Install fails when Grub not on mbr"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by flatwombat on 2007-10-19
I'm multi-booting 7 linux distros and prefer to keep my current grub (Mint) rather than overwrite the mbr yet again.  So, after booting the Gutsy Live CD and starting the install process, I go into Advanced and place grub on (hd1,0); the partition that will contain root.  Install proceeds until about 55% after which it fails on 'bad disk' comments.

I've verified the md5sum and the disk info and it's all correct.  With Feisty, the same errors occurred until I finally gave in and used the mbr for grub, then it installed perfectly.  Just wondering if anyone else has had this problem or if there's a workaround that I haven't thought of.

---

### Post by confused57 on 2007-10-20
> **flatwombat said:**
> I'm multi-booting 7 linux distros and prefer to keep my current grub (Mint) rather than overwrite the mbr yet again.  So, after booting the Gutsy Live CD and starting the install process, I go into Advanced and place grub on (hd1,0); the partition that will contain root.  Install proceeds until about 55% after which it fails on 'bad disk' comments.

I've verified the md5sum and the disk info and it's all correct.  With Feisty, the same errors occurred until I finally gave in and used the mbr for grub, then it installed perfectly.  Just wondering if anyone else has had this problem or if there's a workaround that I haven't thought of.
Instead of using (hd1,0), try /dev/sdb1(or however your root partition is designated).

---

### Post by flatwombat on 2007-10-20
Thanks for the reply.  Yes, I've tried that as well, just in case.  Same error message.  Of course, this is not a crisis situation.  I could have spent less time installing grub on the mbr and then making the few changes to get everything booting properly & in color.  It's just a quirk that has bothered me, since I've installed many Ubuntu variants and only have this problem with Ubuntu itself.

---

### Post by flatwombat on 2007-10-20
Well, let's mark this "solved"!  After downloading from a different source, confirming the md5sum, burning at 12X and confirming the data, the new CD handled the install just the way I wanted.  In reality, I also noticed that my Lite-On burner was taking excessively long to boot the CD's and changed over to my faithful ol' CD-Rom, which was much speedier and error-free.  Not sure which was the culprit, but all's okay now!.

---

