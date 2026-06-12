---
title: "Booted to BusyBox"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by zujenbe on 2008-06-26
ok, so ive looked at all the stuff on other threads but im still having problems, most probably cause i dont understand the jargon everyone uses...shows my linux capabilities but im new to it and ready to learn.

ok, so u sing wubi, i installed ubuntu 8,04 and when i boot, i get sent straight to the busybox hell where i get stuck. How do i get started with this?

---

### Post by avtolle on 2008-06-26
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623) may provide some help to you.

---

### Post by zujenbe on 2008-06-26
> **avtolle said:**
> [https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623) may provide some help to you.

ive already checked that and to no avail :(
thanks tho

---

### Post by Midwest-Linux on 2008-06-26
Let me share a experience. I have a Vista laptop Compaq 762NR. I tried the live CD and just ran it everything worked fine...except wireless. I tried to install using Wubi, Vista did not seem to like Wubi at all..I had the busy box problem too. I scratched the installation.

 I read some windows forums, I found out Vista has a excellent shrink partitioner program. You shrink your Vista partition by some 20 GB or so. This is now called freed space. You can install Ubuntu directly on this freed space and the install should go rather well. it also install grub so that you can boot in the other OS as well.

 You might have to configure wireless (if this is a laptop) but that can be taken care of with a couple of command lines.

---

### Post by zujenbe on 2008-06-26
> **Midwest-Linux said:**
> Let me share a experience. I have a Vista laptop Compaq 762NR. I tried the live CD and just ran it everything worked fine...except wireless. I tried to install using Wubi, Vista did not seem to like Wubi at all..I had the busy box problem too. I scratched the installation.

 I read some windows forums, I found out Vista has a excellent shrink partitioner program. You shrink your Vista partition by some 20 GB or so. This is now called freed space. You can install Ubuntu directly on this freed space and the install should go rather well. it also install grub so that you can boot in the other OS as well.

 You might have to configure wireless (if this is a laptop) but that can be taken care of with a couple of command lines.



hmm.. well, ive installed ubuntu on a seperate partition so im not sure, but il look into it. Also this is not a laptop, its a custom pc i built. it might have been wiser to give the specs first.

System Specification---6/26/2008 8:24:18 PM


Windows 		Windows XP5.1 (Build 2600) Service Pack 2

Internet Explorer 		6.0.2900.2180

Memory (RAM) 		2048 MB

CPU Info 		AMD Athlon(tm) 64 X2 Dual Core Processor 5200+

CPU Speed 		2602.6 MHz

Sound card 		SoundMAX HD Audio

Display Adapters 		Radeon X1600 Pro / X1300XT | Radeon X1600 Pro / X1300XT Secondary | NetMeeting driver | RDPDD Chained DD

Screen Resolution 		1024 X 768 - 32 bit

Network 		Network Present

Network Adapters 		Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller - Packet Scheduler Miniport | Bluetooth Device (Personal Area Network)

CD / DVD Drives 		F: _NEC CD-RW NR-9100A

COM Ports 		COM1

LPT Ports 		

Mouse 		16 Button Wheel Mouse Present

Hard Disks 		C: 48.8GB | D: 48.8GB | E: 0.0MB

Hard Disks - Free 		C: 42.4GB | D: 19.4GB | E: 0.0MB

USB Controllers 		6 host controllers.

Firewire (1394) 		1 host controllers.

PCMCIA (Laptops) 		Not Installed

Manufacturer 		American Megatrends Inc.

Product Make 		System Product Name

AC Power Status 		OnLine

BIOS Info 		AT/AT COMPATIBLE | 08/22/06 | A M I - 8000622

Time Zone 		W. Europe Standard Time

Battery 		No Battery

Motherboard 		ASUSTeK Computer INC. M2R32-MVP

Modem 		Not detected

hope this helps, and just in case, I have Sata drives which ive noticed cause quite a few problems

---

### Post by Evil_Genius_Todd on 2008-07-28
I'm a pretty green n00B myself so this may be a bit of the blind leading the blind. 
But I had very similar problems to what you describe above just trying to install a normal desktop version ubuntu 8.04 on my system. 
After quite a bit of looking around I discovered the problem was likely my Asus M2R32-MVP motherboard. 
You seem to have the same kit. 

I eventually got it working just fine. 
When you begin the install process remove the statement 'quite splash' from the initialization script. 
Then Add 'apci=off' and 'pci=nomsi' 

With any luck you will make it all the way through the installation procedure. 
during the following reboot you will need to add the pci=nomsi to the init script manually. 
Once you get it booted up properly the first time you can add it to grub and then she will at least boot.

---

### Post by Kayma on 2008-08-17
> **Evil_Genius_Todd said:**
> I'm a pretty green n00B myself so this may be a bit of the blind leading the blind. 
But I had very similar problems to what you describe above just trying to install a normal desktop version ubuntu 8.04 on my system. 
After quite a bit of looking around I discovered the problem was likely my Asus M2R32-MVP motherboard. 
You seem to have the same kit. 

I eventually got it working just fine. 
When you begin the install process remove the statement 'quite splash' from the initialization script. 
Then Add 'apci=off' and 'pci=nomsi' 

With any luck you will make it all the way through the installation procedure. 
during the following reboot you will need to add the pci=nomsi to the init script manually. 
Once you get it booted up properly the first time you can add it to grub and then she will at least boot.

I've also got a M2R32-MVP MoBo, and have been trying to install Kubuntu with Wubi on and off for about a month and a half now, only to get saddled with that busybox nonsense.

Evil_Genius_Todd, THANK YOU. After much clawing and gnashing of teeth and reboots, your instructions above enabled me to FINALLY get the Wubi/Kubuntu install to work. Gracias.

---

### Post by mcnux on 2008-11-01
> I eventually got it working just fine. 
When you begin the install process remove the statement 'quite splash' from the initialization script. 
Then Add 'apci=off' and 'pci=nomsi' 

I too am having the same issue and believe these options will fix the problem but I don't understand where during the installation process I am supposed to add them! 

I am using Wubi 8.04.1 installer from within Vista (also tried Wubi option on Ubuntu 8.10 ISO) both giving me the BusyBox console after installation. I tried adding the options to the boot line of /install/boot/grub/menu.lst file but this made no difference. 

From what you said it sounds like I should be able to add these options during installation but I don't see how/where?

Please please help. I'm so close!!!

---

