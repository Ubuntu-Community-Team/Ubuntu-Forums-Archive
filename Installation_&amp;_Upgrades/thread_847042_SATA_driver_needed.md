---
title: "SATA driver needed?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by kevlar_t_hodgepodge on 2008-07-02
hello,

i'm attempting to install ubuntu on a new computer and having some problems.

first off i'm using 8.4 Desktop 64 bit and have both the standard and alternate desktop CDs burnt. when i use the standard CD i get to the partition screen and there do not appear to be any disks to choose from. when i use the alternate desktop CD i get to about the same point and it prompts me to install a driver for my disk drive. i have no idea which driver i need to choose.

hardware in question is:

moterboard is a:
ABIT IP35 Pro LGA 775 Intel P35 ATX Intel Motherboard 
[Manufacturer Page]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=381")
(i updated the BIOS to the newest version.)

hard drive is a:
Seagate Barracuda 7200.10 ST3250410AS 250GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive 
[Manufacturer Page]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Barracuda_7200.10_SATA_250.4_GB&vgnextoid=e73e27fc60322110VgnVCM100000f5ee0a0aRCRD&vgnextchannel=a32a2f290c5fb010VgnVCM100000dd04090aRCRD&reqPage=Model#")

as i side note i installed another OS on this system thinking i might not have set everything up right. the other OS did work, but i would really prefer to use ubuntu.

thanks,
kevlar

---

### Post by logos34 on 2008-07-02
try changing the Bios settings:

>Integrated Peripherals>On-Chip Sata device

try enabling sata mode 'IDE' instead of 'AHCI' (or vice-versa)

'RAID' mode should be disabled

---

