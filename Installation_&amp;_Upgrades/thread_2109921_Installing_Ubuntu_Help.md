---
title: "Installing Ubuntu Help"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by Zyxer22 on 2013-01-28
I've been trying to install ubuntu 12.10 on my new Acer Aspire v5 laptop, but I can't seem to get anything to work.

I've burned a 12.10 disc, but it won't boot on restart. I went into my BIOS and changed the boot order for both instances with a CD drive to boot first. When it still wouldn't load, I enabled the boot menu. While the disc is recognized by my laptop, it won't load. The screen goes black for a minute and then loads normally into windows 8.

At this point, my thought was maybe it was the CD. So, I tried it in my Desktop and it loaded fine. I also tried some of my older 12.04 and 11.10 discs that have worked in the past, but neither loaded. Neither would a windows 7 disc for that matter.

My next course of action was to make a USB boot loader using the link on the Ubuntu download page. Which also failed. I again tried an older USB boot that wouldn't work.

My last attempt was to use the wubi download for it. But, that doesn't work either. Running ubuntu from that lead to an error
status: 0x1000007b Missing or corrupt file.

Sorry for the long topic. I just wanted to be thorough.
So, TL:DR. Help, please :|

---

### Post by arpanaut on 2013-01-28
Win 8 pre-installed?
Secure boot? UEFI?
GPT partitioning?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Zyxer22 on 2013-01-28
Yes, my computer did have windows 8 pre-installed. And, it does seem that my computer has UEFI and secureboot on it. The funny thing was that I'd heard a little about that (which is why I'd thought to try a windows install CD as well. But I guess that isn't considered a secure OS?)

Thanks for the link. I'll look over that and let everyone know if it worked out.

---

### Post by Zyxer22 on 2013-01-29
Everything worked fine. It seems that you have to use a 64 bit version of the operating system to run in the UEFI bios. And, in order to actually run Ubuntu, you have to turn off secure booting.

I really appreciate the quick help. I've been at my wits end on what else I could try here.

---

