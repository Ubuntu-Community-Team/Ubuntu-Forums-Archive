---
title: "Installing Ubuntu on a new HP Pavilion a1726x"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by earlj on 2007-06-11
I am a reformed Windows user, now a Mac OSX user and fan, but have long supported the Open Software movement.  I have run across a very good deal on an HP Pavilion a1726x box for my wife who is not a techie, but needs the usual office and communications packages.  The Pavilion come with Windows Vista (both English and Spanish) loaded out of the box.  

I'd like to take this opportunity to get her started on Ubantu.  It would probably be a good idea to keep Vista loaded as a back up.  So ...

1.  Will Ubantu work well on this box?

What would you recommend I do to

2. Install Ubantu while keeping Vista as a fall back OS.

Please assume I am a complete neophyte regarding Ubantu.

---

### Post by dfreer on 2007-06-11
Can you provide more hardware details on the box, like video card information, processor, etc? This will be easier for us to figure out whether ubuntu will work well on the box.

You can install ubuntu so that it will dual-boot vista. There are some good how-to's around, but basically this is what you will need to do:
Defrag your vista partition.
Use the builtin computer management to resize the vista partition with enough space left for ubuntu.
Reboot and install ubuntu into the free space. It should automatically detect your Vista install and set up dual-boot for you.

---

### Post by earlj on 2007-06-12
Thanks for the reply.  I think this is a special box done by HP for chain retailers.  At $399. I'm willing to live with that!

Here is the tech info:(not sure why some was given in English and some in Spanish)

Tech Specs for 
HP Pavilion a1726x Minitower
(Based on manufacturer's information)
Processor Brand:	Intel
Processor Class:	Pentium D Processor
Processor Number:	915
Processor Speed:	2.8 GHz
Front Side Bus:	800 MHz
L2 Cache Size:	2 x 2 MB
System Chipset:	Intel 945G Express
Memory Speed:	PC2-4200 (533MHz)
Memory Type:	DDR2-SDRAM
Installed Memory:	1 GB
Maximum Memory:	4 GB
Memory Slots Total:	4
Memory Slots Available:	2
Hard Drive Capacity:	320 GB
Drive Controllers:	SATA-150
Rotational Speed:	7200 RPM
Optical Drives:	LightScribe DVD+/-RW SuperMulti Drive:
Create a DVD+R DL at a maximum 8X Write speed
Create a DVD-R DL at a maximum 4X Write speed
Create a DVD+R at a maximum 16X Write speed or a maximum 8X Rewrite speed
Create a DVD-R at a maximum 16X Write speed or a maximum 6X Rewrite speed
Create a DVD-RAM at a maximum 5X Write speed
Play a DVD-Rom at a maximum 16X Read speed
Create a CD-Rom at a maximum 40X Write speed
Create a CD-RW at a maximum 32X Rewrite speed
Play a CD-Rom at a maximum 40X Read speed
DVD-Rom Drive:
Play a DVD-Rom at a maximum 16X Read speed
Card Slots:	1 x CompactFlash 
1 x MicroDrive
1 x Memory Stick
1 x Memory Stick Duo
1 x Memory Stick PRO
1 x MiniSD
1 x SmartMedia Card
1 x Secure Digital(SD)/MMC
1 x xD-Picture Card
Audio Channels:	High Definition Audio, 8 speaker configurable
Video Chipset Brand:	Intel
Video Chipset:	Graphics Media Accelerator (GMA) 950
Video Bus:	PCI Express x16
Video Integration:	Motherboard
Installed Video Memory:	32 MB
Total Available Graphics Memory (Vista):	224 MB
Monitor Included:	No
Port Connectors:	
7 x puertos USB 2.0 (3 en la parte frontal y 4 en la parte posterior)
2 x puertos FireWire (IEEE 1394) (1 en la parte frontal y 1 en la parte posterior)
Micrófono/Auriculares/Entrada de línea (ubicados en la parte frontal)
1 x puerto paralelo (ubicada en la parte posterior)
2 x puertos PS/2 (ubicada en la parte posterior)
entrada y salida de audio digital (ubicada en la parte posterior)
salida de altavoz trasero/altavoz lateral/altavoz central (subwoofer) (ubicada en la parte posterior)
micrófono/entrada de línea/salida de línea (ubicada en la parte posterior)
1 x salida VGA (ubicada en la parte posterior)
1 x RJ-11 Módem (ubicada en la parte posterior)
1 x RJ-45 Ethernet LAN red (ubicada en la parte posterior)
PCI Slots:	3
PCI Express x16 Slots:	1
Slots Notes:	
2 x PCI disponibles
1 x PCI Express x16 disponible
External 3.5 Bays:	1
External 5.25 Bays:	2
External Bays Notes:	
1 x 3.5-inch disponible
Internal 3.5 Bays:	1
Internal Bays Notes:	
Internal Bays (Notes):	
ningunos disponible
Expansion Bays:	
Network Support:	Ethernet (10/100 Mbps)
Modem Speed:	56 Kbps
Input Devices:	Keyboard 
Wheel Mouse
Installed Operating System:	Windows Vista Home Premium
Special Feature:	MS Windows Vista Home Premium Espanol
Included Software:	Fotografías y videos:
Roxio Creator (funciona con Tecnología LightScribe): edite, grabe y guarde información en DVD y CD
muvee autoProducer: cree videos caseros con calidad profesional en forma automática y cópielos a DVD
Productividad:
Microsoft® Works 8: incluye un procesador de texto, hojas de cálculo, bases de datos y calendario.
Adobe® Reader 7.0: Lea e imprima archivos PDF
HP Total Care Advisor: herramienta que se puede personalizar y se encuentra en el escritorio. Ofrece información sobre el estado del sistema y las compras y brinda soporte técnico.
Seguridad para la computadora:
Norton Internet Security 2007: protege la computadora en forma inmediata (actualizaciones sin cargo durante 60 días)
Chassis Style:	Tower (Mini)
Height:	15.0 in
Width:	7.2 in
Depth:	17.0 in
Weight:	24.0 lbs
Limited Warranty:	1 Year (12 Months)

---

### Post by shijirou on 2007-06-12
Yes t will work with Ubuntu. Glad to see a fellow HP user. I'm also on an HP that has Vista and dual-booted with Ubuntu. Ubuntu is my main OS though. Vista is just a backup for my dad who has no time to try to learn Ubuntu.

---

### Post by earlj on 2007-06-12
Great!

Can anyone direct me to step by step directions for the dual boot installation?

---

### Post by kornelix on 2007-06-12
Earl, here is a link to online Ubuntu docs about dual booting:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
(there is also info there about dual booting both ppc and i86 Macs)

With windows XP I have always done this:
1. I assume you start with windows installed and using 100% of the disk
2. Use gparted (booted from CD) to downsize windows partition to make space for Ubuntu.
    (gparted can be downloaded from the web and burned to CD in a few minutes)
3. Install Ubuntu from live CD in resulting empty space (5 GB is enough)
4. Ubuntu will set up grub bootloader to dual-boot
5. You can also use gparted to make a small fat-32 partition which both systems can read and write to, in case you need to move files both ways. I did this at first but never used it.

We need someone to confirm or deny that this works with Vista.

Mike C.

---

### Post by kornelix on 2007-06-12
I see from the online docs that it works with Vista. You can use the Ubuntu installer to downsize windows, so you don't need the extra tool gparted.

---

### Post by earlj on 2007-06-12
Thanks Mike.  Sounds like something I can handle. Am ordering the box right now.

---

### Post by dfreer on 2007-06-12
I dunno about the docs, but it seems the general recommended way of resizing vista is to use the builtin computer management tool. Why risk corruption when vista does the resizing for you? 

Oh wait, that's right... Vista is teh suckage. Still, I'd recommend using it to resize itself.

---

