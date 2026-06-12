---
title: "URGENT PLEASE HELP! Grub took me over!"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Junior Varsity on 2008-11-02
Okay So i tried installing an 8.10 beta onto a USB drive. During installation the USB drive was all i selected. Now for some reason the USB drive wouldn't boot so I just tried to boot back into my HD which was running Vista Home Premium. Whenever I try to do that it gives me a GRUB loader which then errors and does absolutely nothing.

So I popped my 8.10 disc in and i booted off of it. I looked at my hard drive and ALL my files are there including the WINDOWS folder. I don't know what is preventing my computer from booting to windows but i desperately need it fixed for school.

I've run the Windows Vista Upgrade tool from the disc that came with it and i did a system restore, which did nothing since i only did it from a restore point. I also tried running command prompt and doing "Bootrec /rebuildcd" and that showed me a list of options and none of them worked.

I REALLY need my old windows OS back. PLEASE help me get rid of Grub but still keep files.

---

### Post by tommcd on 2008-11-02
If you have a Vista install disc, you can boot from it and fix the master boot record. See these links:
[http://freemangoestech.blogspot.com/2007/12/fixing-mbr-master-boot-record-using.html](http://freemangoestech.blogspot.com/2007/12/fixing-mbr-master-boot-record-using.html)
[http://www.besttechie.net/forums/index.php?showtopic=12691](http://www.besttechie.net/forums/index.php?showtopic=12691)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html)
I don't have Vista, so I cannot verify any of those myself.
If you don't have a Vista disc, here is a Vista recovery disc. The web page says it can fix Vista's master boot record:
[http://members.rushmore.com/~jsky/id39.html](http://members.rushmore.com/~jsky/id39.html)
I know nothing about that particular recovery tool. I just found it with a quick search. Use it at your own risk.

---

### Post by caljohnsmith on 2008-11-02
The solution to your problem should be as simple as running:
```
bootrec /fixmbr
```
From your Vista CD. That's because Grub was installed to the MBR (Master Boot Record) of your Vista drive, so you need to restore your Windows MBR in order to boot directly into Vista; give that a shot and let me know how it goes.

---

