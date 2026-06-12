---
title: "Clean Update On A Dual Boot"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by Sushi Dude on 2010-03-20
Hi, I have Ubuntu 9.10 and as we all know Ubuntu Lucid Lynx is coming soon. I was wondering if I could do a clean install, when I update to Lucid Lynx, that would not affect my other OS(I have a dual boot).

Is this possible?

-Sushi Dude

---

### Post by gordintoronto on 2010-03-20
Yes, you can do that.

---

### Post by 98cwitr on 2010-03-21
coming soon? I'm running it now ;) It will not affect your other OS, you might (but probably won't) have to reconfigure grub if you have some customized settings.

---

### Post by Sushi Dude on 2010-03-21
> **gordintoronto said:**
> Yes, you can do that.

Thank you!

---

### Post by Sushi Dude on 2010-03-21
> **98cwitr said:**
> coming soon? I'm running it now ;) It will not affect your other OS, you might (but probably won't) have to reconfigure grub if you have some customized settings.

I mean the stable release not the beta or alpha release. I think the stable is coming out on April 29.

- Sushi Dude

---

### Post by raymondh on 2010-03-21
Clean install .... just identify, note and install unto the appropriate linux hd or partition.  Usually requires selecting MANUAL in the installation method.

If you have a separate /home .... remember to mount (by selecting the proper mountpoint) but DO NOT CHECK the format box.

If you DO NOT have a separate /home and everything is within root (/), you select the mountpoint from the drop-box and click/check the format bow.

GRUB2 will install, by default, to the MBR of the HD set to boot first in BIOS.  If you only have one HD, then there should be no worry where to install GRUB2 ..... likewise if you have 2 hd's but choose to retain GRUB2 in whatever HD.  But, if you have 2 hd's but choose to have the other OS' bootloader in one HD while GRUB2 in another, just make sure that the hd you plan to install GRUB2 should be set to boot first in BIOS.

After installing, remember to update your system ... as well as GRUB2, if needed.

Like always, before doing any clean install, have a working/tested back-up of your files.

Best,

Raymond

---

