---
title: "Can't access mythbuntu after drive swapping."
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by FleshGordon on 2011-03-05
[FONT=Sans Serif]Hi,[/FONT]
[FONT=Sans Serif]On installing mythbuntu 8.10 I had to swap around my HDDs to make sure get the installation to work.
Originally, I had my SATA drive as the first drive (originally /dev/sda), which has the other distro's on, and the main grub menus
IDE HDD (originally /dev/sdb)and DVDRW
To solve the IDE conflict between the IDE HDD (set as a slave) and the DVDRW (set to Cable Select Auto) I had to make the IDE HDD the primary drive (/dev/sda). and set the DVDRW as a slave. The SATA drive now appears as /dev/sdb
This enables me to install on partition /dev/sda5 on the IDE drive. Not where I really wanted it, but the only place I could reach. the installer would not let me install on a particular partition of /dev/sdb without overwriting the whole disk.
This enables me to install mythbuntu, however, doesn't give m access to the other os's, since the drives /dev/sda and /dev/sdb have been reversed.
After a lot of frustration, I realise the problem is the disk sequencing, so I reset the SATA drive to /dev/sda, and the IDE HDD back to /dev/sdb, with the DVDRW set to CSA.
This allows the existing installations to run as before, but I can't get mythbuntu to boot at all.
my grub entry is;```

title mythbuntu                                                                                        
root (hd1,1)                                                                                            
kernel (hd1,1)/boot/vmlinuz-2.26.35-27-generic root=/dev/sdb5                                      initrd=/boot/initrd.img-2.6.35-27-generic                                                               

```[/FONT]
[FONT=Sans Serif]What is the correct way to call the mythbuntu grub2 loader from grub menu.lst from my other OS's?
[/FONT]

---

