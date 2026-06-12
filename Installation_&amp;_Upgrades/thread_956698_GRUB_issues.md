---
title: "GRUB issues"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by chrismorris730 on 2008-10-23
Hi,
I talked about this briefly in a hardware related post, but I "broke" an install of Kubuntu when I installed the drivers (using adept) for my ATI radeon X1650. The drivers made my maximum resolution 640x480, making it virtually impossible to accomplish most tasks. I could also not figure out how to uninstall the drivers, which was very frustrating. This install happens to be on my main 500GB SATA drive which also contains my install of Vista. I would just format the partition that this install of Kubuntu is on, but a friend of mine did format the partition and lost his MBR for Vista and had problems fixing it. I would like to know the "correct" way to remove the "broken" install of Kubuntu from my hard drive without messing up Vista booting.

I probably should have mentioned this earlier in the post but right now my install of Linux is off an old 80GB IDE drive, and when GRUB loads up I have two Linux options. I don't know that since GRUB is on the IDE drive as well (I guess...) if I can just partition the one on the SATA drive without any problems.

Thanks in advance!

---

### Post by caljohnsmith on 2008-10-23
If you have your Vista Install CD, you can install a Windows MBR (Master Boot Record) on your Vista drive so that it will boot directly into Vista and not Grub; just boot the CD, go to the command line and run:
```
bootrec /fixmbr
```
Then it will be safe to remove Linux from that drive. :)

---

### Post by chrismorris730 on 2008-10-23
I bought my computer from Best Buy and do not have my Vista disk =[

---

### Post by caljohnsmith on 2008-10-23
You can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes.

---

### Post by chrismorris730 on 2008-10-23
unforunately I do not have any blank CDs at the moment. I do not get paid until tomorrow so that will be when you hear from me about this

---

### Post by WWSmith36 on 2008-10-23
You should request a copy of Vista CD.  Although they don´t give you the CD when you purchase your computer, they will if you request it.  It is definitely a good thing to have it on hand, if you ever have problems.

---

