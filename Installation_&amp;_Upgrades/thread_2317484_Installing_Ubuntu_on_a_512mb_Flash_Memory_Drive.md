---
title: "Installing Ubuntu on a 512mb Flash Memory Drive"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by gennaro4 on 2016-03-16
Im attempting to install Ubuntu [Ubuntu 15.10 "Wily Werewolf"]("http://archive.ubuntu.com/ubuntu/dists/wily/main/installer-i386/current/images/netboot/mini.iso") 32bit on one of the following machines: [http://store.disklessworkstations.com/200301.html](http://store.disklessworkstations.com/200301.html) 


This machine has 512mb of storage, and 2gb ddr2 memory/ram. Is it even possible to install the command line version of ubuntu on a system with drive space that small?



also my goal with this machine is to basically have a firefox kiosk.

---

### Post by sudodus on 2016-03-17
Welcome to the Ubuntu Forums :-)

You cannot install standard Ubuntu in a drive so small. You cannot even install the light-weight flavour Lubuntu into such a small drive. I don't think you can store any current Ubuntu based system in such small drive space - not as an installed system. But if you can consider a live system (which has the main part of it stored in a compressed file) there are options, for example ***Tiny Core***, which can boot from a 15 MB image of an iso file.

From the specification in the link:

> Network Boot Protocol	PXE
Thin Client Software	LTSP 5.x

Are you not happy with that system? Is there any particular feature you want?

> I/O Connectors: 	

. (1) Mic-In
. (1) Line-Out
. (1) Digital DVI-I video output
. (1) PS/2 (for KB or Y cable)
[COLOR="#0000FF"]. (4) USB 2.0 ports (6 external, 2 internal)[/COLOR]
. (1) RJ-45 connector, 10/100/1000 Mbps, 

I see that there are USB ports. Please test If you can boot from USB :-)

If it works, you can connect 

- a small USB drive and run a live-only system
- a larger USB drive and run a persistent live system
- an even larger USB drive (16 GB or larger) and run an installed system.

See these links:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by kc1di on 2016-03-17
These are the minimum needed specs. for Ubuntu install.```
700 MHz processor (about Intel Celeron or better)
512 MiB RAM (system memory)
**5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)**
VGA capable of 1024x768 screen resolution
Either a CD/DVD drive or a USB port for the installer media
Internet access is helpful
```

You'll notice you need at least 5 GB of H.D. Space.  512mb isn't even close to that.  Get a bigger usb stick if you can. 

You may be able to run Tiny Core Linux or even Puppy linux on that machine.  
good luck.

---

### Post by RobGoss on 2016-03-17
Hello and welcome, Ubuntu requires less to run but even whit that said you should have enough Ram and hard drive space on your machine if you really want to enjoy a great desktop experience   

Installation / SystemRequirements Ubuntu
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by grahammechanical on 2016-03-17
> [h=2][SIZE=2]Ubuntu Server (CLI) Installation[/SIZE][/h] 
[LIST]
[*]300 MHz x86 processor 
[*]192 MiB of system memory (RAM) 
[*]1 GB of disk space 
[*]Graphics card and monitor capable of 640x480 
[*][CD drive]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD")

[/LIST]


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I recently installed the Mini ISO image with Xubuntu core (Xfce). I did not add Xubuntu Desktop only Firefox and that has taken up 2.8 GB of disk space. 

Regards.

---

