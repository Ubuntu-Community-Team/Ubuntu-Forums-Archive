---
title: "Two HDs: Windows and Ubuntu 6.10"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by Techman010 on 2007-01-27
OK, This is how it is.  I have two identical Western Digital HDs.   I want to put Windows XP on one and Ubuntu on the other.  I have tried this before but ran into problems.  I think that those problems were just because of GRUB.  Now.  Where would I install grub to?  I know its the MBR.  I want to know what I put in at the end of the ubuntu installation(when it asks me where to install GRUB).  I know I have to install windows first. 

I'm guessing Windows is going to be installed to HD0 and Ubuntu to HD1...

I hoped to finish this today, because it has been far too long without Ubuntu on my main computer (about 2 months).   

Thank you.

---

### Post by taurus on 2007-01-27
I believe you will get three options to install GRUB (at least on the alternate CD anyway).  the first option is to install it to MBR which is (hd0).  That's where you want to install GRUB.

---

### Post by Techman010 on 2007-01-27
Thanks for the quick reply.
ok.  Hopefully that will work.  I thought I tried that last time though...

Should I install with the alternate CD? or just the normal one?

Would that make a difference?  (Last time I used the normal one.)

---

### Post by osseotech on 2007-01-27
I've been using the setup you want for a couple of months. I installed Window to HD0 and then changed my boot order in BIOS to boot HD1 first. Then I installed Ubuntu to HD1 and let Grub install to MBR which was the default. Grub found Windows on HD0 and added it to the boot menu. I left HD1 as the first drive in BIOS boot order.  Everything has worked. If you run into a problem you can change the boot order back to HD0 and Windows should boot normally.

---

### Post by Techman010 on 2007-01-27
ok.  The only problem with that is in my BIOS the HDs are identical when picking which one to boot first.  Their names are exactly the same.

---

### Post by Techman010 on 2007-02-03
Nice.  Everything worked.  Thanks all.

---

