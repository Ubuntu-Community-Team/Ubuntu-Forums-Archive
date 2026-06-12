---
title: "Huh?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by JESSU on 2007-05-20
Im a noob to Linux but want to see what the hype is about.
I burned the iso image, restarted and booted with the CD. I select to install Ubuntu. It looks like its working and thr progress bar is going back and forth then a CLI appears and I get this
/bin/sh:can't access tty;job control turned off
What do I do?

---

### Post by randell6564 on 2007-05-20
> **JESSU said:**
> Im a noob to Linux but want to see what the hype is about.
I burned the iso image, restarted and booted with the CD. I select to install Ubuntu. It looks like its working and thr progress bar is going back and forth then a CLI appears and I get this
/bin/sn:can't access tty;job control turned off
What do I do?
I'm googling your problem, but for now check out [this thread]("http://www.linuxquestions.org/questions/showthread.php?t=474493").

---

### Post by JESSU on 2007-05-20
After searching the forums I found this.
> 04/26/2007 After reading the MANY replies and posts in this thread so far, it's clear that the error message in the subject line can occur for MANY different specific reasons. What all of these reasons seem to have in common is that the new 2.6.20-15 kernel used by Fiesty chokes when it encounters hardware or combinations of hardware that its boot-up routines aren't coded to handle properly. When it chokes, it almost always spits out that error message at the end. Solving your particular issue or finding a workaround for it may require a lot of time and patience, if you ever solve it all. Many have posted solutions that worked for them and many haven't found an answer. It's probably a good idea to post your hardware and how it's connected when you add to the thread. That way if you find an answer for yourself, someone else with a similar set-up can try your solution. (I plan to edit this post with more specific hardware info later as well.)

I do have 2 hard drives. I want to install on the second one.
Heres my specs..the smiles are supposted to be an 8 and a )
Windows XP Home SP2
Browser MSIE 7.0; .NET CLR 1.1.4322; .NET CLR 2.0.50727
Brand/Model Intel Pentium 4
RAM installed 512 MB
Windows RAM 512 MB
Total RAM slots 2
Available RAM slots 0
Max RAM module size 1024 MB
Memory Type 256+256;DIMM,?18,|Synchronous;T16
Speed Rating 3587 MB/s
Brand/Model NVIDIA GeForce FX 5200 (Microsoft Corporation)
Bandwidth Down 5011 Kbits/sec 
Average Ping 52 ms 
Browser MSIE 7.0; .NET CLR 1.1.4322; .NET CLR 2.0.50727 
IE current cache 22 MB 
IE max cache 1192 MB 
Nominal Clock Speed  1800 MHz 
Measured Clock Speed  1800 MHz 
External Clock Speed  100 MHz 
CPU Load  89% 
Description  Results  
RAM installed 512 MB 
Resolution 1024x768 pixels 
Colors 65,636 
DirectX version 5.03.2600.2180 (xpsp_sp2_rtm.040803-2158) 
OpenGL version 5.1.2600.2180 (xpsp_sp2_rtm.040803-2158) 
Acceleration options Enabled 
Performance 177.55 MP/s 
Monitor Dell 50563 
Max. Resolution (HxV) 1600 x 1200 pixels 
Screen Size (HxV) 34 x 27 cm 
Viewable Diagonal Size 17.09 inch 
Manufacture Date February 2002

---

### Post by JESSU on 2007-05-21
bump

---

### Post by pebo on 2007-05-21
You may have more luck with the alternate CD which uses a text-based installer. You can try different boot options which disable some of the hardware detection routines which might help. IMO the alternate CD makes for a more reliable install.
Good luck!

---

