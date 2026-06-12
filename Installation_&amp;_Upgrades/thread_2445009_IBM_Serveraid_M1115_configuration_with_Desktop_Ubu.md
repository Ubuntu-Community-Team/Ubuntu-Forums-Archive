---
title: "IBM Serveraid M1115 configuration with Desktop Ubuntu 20.04 new RAID setup"
date: 2020-06-08
forum: Installation &amp; Upgrades
---

### Post by Marcus Aurelius on 2020-06-08
Hello,

I am trying to set up a mirroring RAID 1, using a "IBM Serveraid M1115 SAS/SATA Controller for System X (81Y4448)."  My desktop is currently setup as follows:
-  AMD Ryzen 9 3900X (12-core, 24-thread) on a Gigabyte X570 Aorus Master Motherboard with RAM (Corsair Vengeance LPX 16GB (2 X 8GB) DDR4 3600).
[FYI, this Motherboard comes with its own RAID as an option]

For Storage space I have:
-  Seagate FireCuda 2TB SSHD – 3.5 Inch SATA (ST2000DX002) - [I have two of these drives]
-  Seagate Barracuda 510 SSD Internal Solid State Drive [all in the M.2 Slot's] – PCIe Nvme (ZP1000CM30001)  - [I have two of these that are 1 TB; and one of these is 256GB]
-  Crucial MX500 2TB 3D NAND SATA 2.5 Inch Internal SSD - CT2000MX500SSD1 - [I have two of these drives]

Currently, I have the M.2A slot using a 1 TB Barracuda for my dual boot OS.  
-  I had Windows 10 installed (unencrypted) dual booted with...
-  Ubuntu 20.04 LTS with Full Disk EncryptVG (ext4)
-  & encrypted swap partition in between these OS's

I have the M.2B slot using a 1 TB Barracuda for my Games Data. (&etc)
I have the M.2C slot using a 256 GB Barracuda for my Virtual Machine Data (&etc)

I do not encrypt M.2B or M.2C.

Now I also want to use the [two] Seagate FireCuda 2TB SSHD – 3.5 Inch SATA (ST2000DX002) for the purpose of Genealogical Research using GRAMPS.  
I already have lots of GRAMPS data on another machine waiting to be migrated, but on this new machine, I will need RAID set so that GRAMPS will be backed up and updated on two drives always.
I will also purchase a third drive of same, to swap in occasionally..so that two drives are in the machine, while the third drive is in the safety deposit box at the bank.

The Crucial MX500 2TB 3D NAND SATA 2.5 Inch Internal SSD drives will hold video data (Genealogical video as well as other video).
I would like to set these up also as RAID 1.

I am not sure if I can use RAID in this manner, to have two 3.5" drives set to RAID 1 for their data, and an additional two 2.5" drives set to RAID 1 for their distinct data.
If this is possible, what would be the best order to go about setting things up.  

I already have the OS's installed, so should I wipe and start from scratch?
I have noticed that the operating system can not see the 2.5" disks in GParted, but I see them in the BIOS when they are attached to the controller.
If I remove the controller, I can not see those disks on the motherboards RAID in the BIOS (or Gparted).
It is possible the RAID drivers have not been installed properly on the new motherboard.

Finally, I have not succeeded installing the drivers for the new controller, either.  I believe I have to compile the driver into the kernel, but wanted to check here first before I started messing with things.
[http://manpages.ubuntu.com/manpages/xenial/man4/mfi.4freebsd.html](http://manpages.ubuntu.com/manpages/xenial/man4/mfi.4freebsd.html)

Thank you in advance for any assistance.

---

