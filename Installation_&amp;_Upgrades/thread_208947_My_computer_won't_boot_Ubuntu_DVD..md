---
title: "My computer won't boot Ubuntu DVD."
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by GreenLantern33 on 2006-07-04
Hello, first time poster here.

I'm almost embarassed to ask this question, but it seems as though my computer won't boot from the copy of Ubuntu that I burnt?  I have a Windows setup DVD, and it will boot from that fine, but it just doesn't seem to even attempt to boot from the Ubuntu disk.

Thanks,
GL

---

### Post by bvucinic on 2006-07-04
Have you verified the DVD has been burnt correctly?

---

### Post by atoponce on 2006-07-04
[quote=GreenLantern33]Hello, first time poster here.

I'm almost embarassed to ask this question, but it seems as though my computer won't boot from the copy of Ubuntu that I burnt?  I have a Windows setup DVD, and it will boot from that fine, but it just doesn't seem to even attempt to boot from the Ubuntu disk.

Thanks,
GL[/quote]
Have you checked the MD5 checksum?  You might have a bad burn on the DVD.

---

### Post by GreenLantern33 on 2006-07-04
How do I do that?

The DVD works fine when I run it from Windows.  I can run through the tour and everything.

---

### Post by atoponce on 2006-07-04
[quote=GreenLantern33]How do I do that?

The DVD works fine when I run it from Windows.  I can run through the tour and everything.[/quote]
Pull up a terminal, and type:

```
md5sum DVD_name.iso
```

Check the resulting 32-bit string with the one on the website where you downloaded the *.iso.  If they match, your disc is uncorrupted.

---

### Post by GreenLantern33 on 2006-07-05
Well I ended up burning the CD version and trying that.  It worked just fine.

Is there a major difference between the CD version and the DVD version?

---

### Post by Nottawa Newbie on 2008-02-18
How do I do a checksum in Windows?  I can't boot from the the cd I donloaded and burned, so I want to make sure I have a good burn before I have to go back and download it again.

---

