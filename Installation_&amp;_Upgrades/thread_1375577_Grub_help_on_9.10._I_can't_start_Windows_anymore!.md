---
title: "Grub help on 9.10. I can't start Windows anymore!"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by fparri on 2010-01-08
Hi guys, anyone can suggest me how to modify my grub configuration in order to have my windows OS appear at boot time. Windows is on /dev/sda2, but at boot time I am only shown its setup, on /dev/sda1.

> 
Disco /dev/sda: 120.0 GB, 120034123776 byte
255 testine, 63 settori/tracce, 14593 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x7ab852fc

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2098176   27  Sconosciuto
/dev/sda2   *         263       11024    86438286+   7  HPFS/NTFS
/dev/sda3           11025       14593    28667992+   5  Esteso
/dev/sda5           14229       14593     2931831   82  Linux swap / Solaris
/dev/sda6           11025       14228    25736067   83  Linux

---

### Post by varangian on 2010-01-08
Not certain what your situation is here but I've just had to set up Grub2 again after adding Windows 7 into the mix - naturally it doesn't deign to recognise any of the OS's on the machine other than Microsoft ones. The article [_here_]("https://help.ubuntu.com/community/Grub2") should give you the info you need. I'd imagine, since you've obviously got grub launching, that you'll only need to do the:

sudo update-grub

bit to get grub to scan the system and update the menu with whatever OS's it finds on the system but it also covers how to edit the config manually if needed.

---

### Post by fparri on 2010-01-08
Luckily, all I needed to do, to solve my problem, was to launch an update with apt-get upgrade. The updated grub package rescanned my sistem and, this time, found the correct Windows partition.

Thanks for the link, though. I'll do read it with particular attention :)

---

