---
title: "This should be simple: Boot doesn't find my Ubuntu."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2007-11-03
**Long story short,** a botched BIOS upgrade screwed up my drive order. I've got everything working again on the Windows side, but I can no longer launch my Ubuntu installation via the CD.

**More detail:** I installed Ubuntu to its own dedicated hard drive (160GB IDE). Rather than screw around with a boot menu app, I always just inserted the Ubuntu CD and selected the last option... "boot from hard drive"... to launch Ubuntu.

But now, when I try that, I get "NTLDR is missing. Press Alt-Ctrl-Delete to reboot", which is just a fancy way of telling me it doesn't know where Ubuntu is (technically, the Ubuntu boot sector code that tells it where to find the HDD with Ubuntu on it is missing).

My *primary* drive USED TO BE my SATA-RAID setup, but thanks to the disaster I mentioned above, my RAID is now "Disk 1" and *another* IDE HDD (I have two)  is "Disk 0". The Ubuntu CD is looking on the wrong drive for NTLDR.

My drives **are** arranged in the proper order in BIOS, but for some reason, I just can NOT force my SATA RAID set back to "Disk 0".

So I need some way to "repair" Ubuntu so finds my installation again. **Any ideas** *(short of reinstalling from scratch)*??? Thanx.

---

### Post by mrvertigo on 2007-11-03
interesting, i'll look it up

---

