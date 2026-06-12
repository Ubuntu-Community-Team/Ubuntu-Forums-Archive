---
title: "Installation hangs..."
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by haocheng on 2004-11-02
Hi~~~

My installation hangs everytime...  :-( 
When I am installing Ubuntu, the installation process hangs in the step:
"Detecting hardware to find CD-ROM drive"
It hangs at 92% and the status bar showed "Loading sd_mod to..."
I've tried for all night but cannot find the solution~~~

I have Windows XP on my first IBM HD and I would like to install Ubuntu on my new Seagate 160G SATA HD.

BTW, I think the CD is OK because I have successfully installed Ubuntu on another computer with this CD. 
I tried to boot with my TEAC 540E and CyQVE CD-RW, but both hangs at the same place...

Does anyone know how this could happen?
Is there anything wrong with my hardware? :-| 

Any help is appreciated and many thanks in advance!  :smile: 

My Computer:
CPU: P4 Prescott 3.2EG
MB: ASUS P4S800D (SIS 655FX)
RAM: Transcend DDR400 512MB*2
HD: IBM 30G*2 / Seagate 160G*1(SATA)
CD-ROM: TEAC 540E
CD-RW: CyQve 48X
VGA: TNT2
Power: Delta 350W

---

### Post by haocheng on 2004-11-02
I tried again tonight and I found that if I don't load sd_mod module, 
the installation won't hang there....

However, it cannot detect my new SATA HD without the module  :-( 

So, is it because SIS 655FX doesn't support installing Ubuntu on SATA HD?
Did anyone successfully install Ubuntu on Motherboard of SIS 655FX?

Any help is appreciated and many thanks in advance! :)

---

### Post by psylvester on 2006-06-26
ok. here we go,
check if you are using any USB devices, like USB mouse. I have seen this problem before while installing Redhat ES 4. The installation just hangs, its because when it fails to detect the hardware, it dies.
I had Issue with SATA disks as well, however when i installed ubuntu, it went fine. the problem was with redhat. 
Anyway, let me know If i can help you in anyway.
Sata disk detection wont be a problem in latest kernels. Just make sure If the same thing is avialable in the BIOS,.

---

