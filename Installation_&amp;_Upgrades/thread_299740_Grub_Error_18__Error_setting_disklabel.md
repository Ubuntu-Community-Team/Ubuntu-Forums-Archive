---
title: "Grub Error 18 / Error setting disklabel"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by obdurate1974 on 2006-11-14
i have a maxtor 6y250p0 (250gig) drive.. when i install ubuntu using the live cd everything seems to work fine until it reboots and then i get a grub error 18.. :( 

when i try to manually partition it using gparted to put a /boot partition at the beginning it reads that it is a 233 gig drive and it will not allow me to partition it giving me an error during the disklabel part ](*,) 

i have tried setting the bios to what grub says the drive is and this didnt seems to work either giving me a harddisk failure error on boot.. i also tried setting the bios to some other c/h/s settings that came up with other partitioners.. only one allowed me to boot the machine but i was not sucessful in getting ubuntu on there.. :-k

i also booted with the xubuntu alternate disk and the partitioner in there reads the disk as 251gb but it still gives me an error setting the disklabel.. :confused: 

it was painful for me but i have sucessfully installed winXP with no problems.. i would rather use ubuntu.. :mad: 

please help if you can..

---

### Post by 1st_johnnymac on 2006-11-20
Was hoping someone would have answered by now, I got the same problem :-?

---

### Post by 1st_johnnymac on 2007-01-23
Finally got time to investigate this, embarrisingly it was due to the jumpers on a 300 GB Hard dive set to a limit of 300 mb :redface: 

Don't ask how it got set like that, or even what use that setting is for 'cos I havn't got a clue.:confused: 

Anyway, up and running seamlessly at last :rolleyes: 

1st_johnnymac

---

