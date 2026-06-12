---
title: "&quot;Try hd(0,0): NTFS5: No wubildr&quot; 2 minute hang"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by arrowhead on 2010-05-02
I'm having a bit of a problem with the new Ubuntu 10.04 installed on my Windows 7 based machine via Wubi. I see the error message "Try hd(0,0): NTFS5: No wubildr" on my screen for around two minutes, then "Try hd(0,1)" shows on the next line briefly, then Grub loads and I can boot normally.
All the time the error message is on the screen there is lots of hard drive activity. 
Is there anything I can do to fix this delay in my booting up sequence?

---

### Post by Cuba71 on 2010-05-04
I installed 10.04 Lynx using Wubi on my Vista Premium Toshiba laptop, and get the exact same messages, and then everything works fine.

Any ideas any one?

---

### Post by sapa2ler on 2010-05-05
You can take a look here:
 
[http://nizam-online.blogspot.com](http://nizam-online.blogspot.com)
 
 
It might helps...
 
:KS

---

### Post by Cuba71 on 2010-05-05
> **sapa2ler said:**
> You can take a look here:
 
[http://nizam-online.blogspot.com](http://nizam-online.blogspot.com)
 
 
It might helps...
 
:KS

Thank you for the reply.  Unfortunately I'm running Wubi on Windows Vista Premium, and don't have the specified directory, this is what I have

---

### Post by sapa2ler on 2010-05-06
Hi,
 
The solution is only for Win 7.
 
For Win Vista. u need to set the Wubi to Win XP SP2 Compatible and then run as administrator.
 
Hope it help...
 
:KS

---

### Post by arrowhead on 2010-05-07
> **sapa2ler said:**
> You can take a look here:
 
[http://nizam-online.blogspot.com](http://nizam-online.blogspot.com)
 
 
It might helps...
 
:KS

Thank you very much, sapa2ler. That worked for me :D

---

### Post by sapa2ler on 2010-05-12
> **arrowhead said:**
> Thank you very much, sapa2ler. That worked for me :D
 
No Problem. Glad it helped...
 
:KS

---

### Post by ghendric on 2010-05-21
That copy thing didn't work for me. I'm running Windows 7 Ultimate 64 bit. It never does boot into Kubuntu. My pc just hangs at that message.. I used the WUBI installer to install KUbuntu.. I don't have this problem on another PC running Windows 7 ultimate 64 bit.. 

The problem pc is an AMD 4000 processor with 4 gigs of ram and a 340 gig SATA drive.

---

### Post by ghendric on 2010-05-28
> **ghendric said:**
> That copy thing didn't work for me. I'm running Windows 7 Ultimate 64 bit. It never does boot into Kubuntu. My pc just hangs at that message.. I used the WUBI installer to install KUbuntu.. I don't have this problem on another PC running Windows 7 ultimate 64 bit.. 
 
The problem pc is an AMD 4000 processor with 4 gigs of ram and a 340 gig SATA drive.
 
 
Ok, I think I know what's going on. My Windows 7 install created a 100 meg hidden system partition when I installed it so when I select KUbuntu from the boot menu, I think it thinks that the hidden partition is the main partition. That's why it can't find the wubildr. How can I make it point to the correct partition? Any help is greatly appreciated.
 
... the first partition on the drive is the hidden system partition and the second partition thats NOT hidden contains Windows 7.

---

