---
title: "Ubuntu 7.10 correctly installed can't start"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by mariollv on 2007-11-11
Hi,
I installed Ubuntu 7.10 on my Asus M3N and everything went fine. Now I cannot start the system. At the boot the systems stops at "Starting up...".
Previously I had installed Ubuntu 7.04 and it was working perfectly.
Any ideas
Thanks

---

### Post by zvacet on 2007-11-11
Did you chek CD for errors?Made md5 sum chek?Is the CD O.K.(scratches)?

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by don_crissti on 2007-11-11
I had the same problem some time ago on a PC with two harddisks. I had to edit the Grub line (hit "e" when Grub loads)
root (hd0,2) to 
root (hd0,1) 
Apparently Ubuntu has mistaken my root partition... check if yours is ok
also after 
root=UUID=623b05e4-10a3-4a73-8051-b9c7817b5e7e ro quiet splash
I had to add the option noapic so it looked like this 
root=UUID=623b05e4-10a3-4a73-8051-b9c7817b5e7e ro quiet splash noapic
After succesfully booting I also had to change my /boot/grub/device.map file:
instead (hd0) /dev/sda it was written (hd0) /dev/hda (don't know why, might be a bug)
and my menu.lst according to what my root partition was.
That worked for me....

---

