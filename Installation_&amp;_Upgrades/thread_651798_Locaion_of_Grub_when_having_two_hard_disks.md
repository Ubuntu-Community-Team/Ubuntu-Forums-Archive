---
title: "Locaion of Grub when having two hard disks"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by karthik_jce on 2007-12-27
Hi,

I have two sata harddisks one with windows (250 GB ) and the other with ubuntu (80 GB). with the command "sudo fdisk -l " it shows my windows hard disk (250 GB) as sda1,sda2.. etc and the ubuntu hard disk (80GB) as sdb1, sdb2. ... etc.

Now ubuntu has installed Grub and shows the boot option menus with windows XP and ubuntu( i.e it has ditected my windows on the other hard disk automatically). please let me know where is this Grub installed, is it on the 250 GB hard's MBR or the 80 GB hard disks MBR.

I tried the command "find /boot/grub/stage1" on the grub shell and it shows as (hd1,0). I am not able to identify were this GRUB is installed. Please help.

Karthigeyan

---

### Post by logos34 on 2007-12-28
> **karthik_jce said:**
> 
I tried the command "find /boot/grub/stage1" on the grub shell and it shows as (hd1,0). I am not able to identify were this GRUB is installed. Please help.

Grub is on the MBR of the 250 Gb drive, /dev/sda.  It installs by default to (hd0)--the first Bios boot disk.  (Strictly speaking, it installs the Grub IPL--Initial program loader--to the first 446 bytes of the hard disk/i.e. mbr portion).  But it is pointing to menu.lst on the linux root partition (hd1,0)--that's what you're seeing when the grub boot screen loads.

---

### Post by karthik_jce on 2007-12-28
Hi,

Thanks for clarifying this. 

But I remember chanigng the boot sequence in CMOS as below before installing ubuntu,
1. cdrom
2. 80GB 
3. 250 GB

After installation and some time later I changed the boot sequence to 
1.cdrom
2. 250GB
3. 80GB
i.e which I have currently.

Is it possible to remove grub from the MBR of the 250 GB harddisk and move it to the 80GB disk (without reinstalling windows) ?

Karthigeyan

---

### Post by erfahren on 2007-12-28
some excellent info on GRUB: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
he also has good info on the MBR [http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

as for moving the MBR I don't know if you could, Windows is picky about that. GRUB is very configurable though, so why would you want to (or need to)?

---

### Post by meierfra on 2007-12-28
> Is it possible to remove grub from the MBR of the 250 GB harddisk and move it to the 80GB disk (without reinstalling windows) ?



Yes. Click on "DualTwo" in my signature. It will show you how to to  install  grub to the  80GB drive, fix  the MBR of the 250 GB drive and edit "menu.lst" accordingly. The HowTo assumes that Ubuntu is an external drive, but that is irrelevant. Just substitute external drive by "80GB drive and "internal drive" by "250GB" drive.

---

