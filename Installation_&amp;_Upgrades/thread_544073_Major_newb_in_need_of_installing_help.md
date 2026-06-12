---
title: "Major newb in need of installing help"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Itchmecho on 2007-09-05
ok now i am very new to this linux ubutu thing, and i seriously need help, i do not know any of the lingo!! i want to keep my windows, and everything without formatting, but it says somehting about formatting! i don't know


i just want a brand new partition with linux installed on it and no formatting, i wanna keep my windows, and linux at the same time, i have read you can do this, can anyone help me, like give me a step-by step tutorial!!! please i would appriciate it

---

### Post by Pumalite on 2007-09-05
No problem; we can take you by the hand but we need more details: specs?, XP?, Vista?, How many drives?, Laptop?, graphics?, Memory?

---

### Post by Itchmecho on 2007-09-05
ok no prob.

Manufacturer:	HP-Pavilion
Processor:	AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 CPUs), ~2.2GHz
Memory:	1022MB RAM/ 1GB RAM
Hard Drive:	400 GB Total; HD1: 250; HD2: 150
Video Card:	NVIDIA GeForce 7300 GT 
Monitor:	Dell E153FP
Sound Card:	Speakers (Realtek High Definition Audio)
Speakers/Headphones:	Speakers (Realtek High Definition Audio)
Keyboard:	Microsoft USB Digital Media Pro Keyboard (IntelliType Pro)
Mouse:	Logitech USB MX320 Laser Mouse
Mouse Surface:	Soft Pad
Operating System:	Windows Vista&#8482; Ultimate (6.0, Build 6000) (6000.vista_rtm.061101-2205)



is there anything else?

---

### Post by Pumalite on 2007-09-05
Are you using the same hard drive for Vista and Ubuntu or Ubuntu will go in different hard drive? If same hard drive; use Vista's partitioner, then Gparted and format new partition to ext3 and install.

---

### Post by Itchmecho on 2007-09-05
the same drive for both, but if you want me to, i can put it on my other one

---

### Post by Itchmecho on 2007-09-05
ok umm how do i get vistas partitioner, i never saw one, i know just a bit about computers, so i know where to look and stuff, but umm i must have missed it

---

### Post by Pumalite on 2007-09-05
It must be in 'Tools' or something like that.
(Giving you other drive to Ubuntu would be the easiest; use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), make one large partition of your hard drive, formatted ext3, install using>Guided>Use Entire Disk, let Grub install to MBR (by default) and you end up with Grub giving you a choice of booting either OS)

---

### Post by Itchmecho on 2007-09-05
what if it is in the other hard drive?

---

### Post by Itchmecho on 2007-09-05
and i don't have tools, like where to i go to put a partition on? Computer? or something?

---

### Post by merlinus on 2007-09-05
You might do well to look at the info here:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

-merlin

---

### Post by Itchmecho on 2007-09-05
ok thank you!

---

### Post by merlinus on 2007-09-05
You are most welcome.  Post back if you have further questions.

Good luck!

-merlin

---

