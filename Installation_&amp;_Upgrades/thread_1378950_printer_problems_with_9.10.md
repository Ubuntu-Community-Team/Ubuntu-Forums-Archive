---
title: "printer problems with 9.10"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by corrickm on 2010-01-12
After upgrading to 9.10 neither of my printers work - HP Deskjet D1560 and HP Deskjet F2280 All-in-one. The printer troubleshooter seems to stall and provides no clues. Both printers work fine on Windows. Can someone give me some ideas as to what to do? Thanks, Martin

---

### Post by PRC09 on 2010-01-12
You can check the HPLIP site and see if there is any info that helps....

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by corrickm on 2010-01-12
Thanks PRC09 - I ran dpkg and got rc hplip   3.9.8-lubuntu2 - I suppose this means that version 3.9.8 of hplip is installed? Both my printers appear to be supported. Anybody got any more ideas? Martin

---

### Post by corrickm on 2010-01-12
Ho hum - I tried hp-check -t and that resulted in 'program not installed', so I did sudo apt-get install hplip and the software was installed (or re-installed) and the HP Deskjet D1560 now works... Not sure what happened here, but thanks anyway. Martin

---

### Post by claudehopper on 2010-07-02
[QUOTE=PRC09;8651298]You can check the HPLIP site and see if there is any info that helps....

---

