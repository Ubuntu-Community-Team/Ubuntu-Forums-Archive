---
title: "No partitioning"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by QNo on 2008-03-03
Hi all,

I just tried to install Kubuntu 7.10 on a FEF's computer. Hardware: Athlon X2 2200Mhz on an Asus M2V Motherboard (VIA K8T890/VIA VT8237A).

I tried several installation CDs, all burnt from the same ISO (32bit), before i found one that the CDROM device liked to boot.

Then, everything went fine. Boot, Start of Installation program, local settings, partitioning, start of installation. Sudden end, error, could not read the CD (i did a complete install from that CD 20 mins ago).

Ok, shutdown, other CDROM device. Boot, Start of Installation program, local settings, partitioning did not work. There was free space, i could make a swap partition, but when i made an ext3 partition with mount point /, after an ok the new partition was not found, there was free space again, and no button except "cancel" gave any reaction.

Hardware failure? But Windows runs under heavy game load without errors ... Inkompatibilities? Would i need additional drivers? Any other hints?

TIA
Chris

---

### Post by Pumalite on 2008-03-03
Did you do md5sum on your iso? Burn at 4x or less? Check for CD integrity before install?
Maybe you need to clean the lens of your burner?
Your specs would help.

---

### Post by QNo on 2008-03-03
CD burnt at 20x, no MD5sum check, but test from boot menu without any errors.

---

### Post by Pumalite on 2008-03-03
You need to do md5sum (it's vital if you want a good CD). Burn a new CD if md5sum is OK.

---

### Post by QNo on 2008-03-03
md5sum is ok. After burning 4 different CDs with that specific CD burner, i'll try another one tomorrow. Now it's midnight here. Thank you for your help, i will continue to ask another day.

---

### Post by Pumalite on 2008-03-03
Don't forget to try your CD's on a different computer to rule your burner out.

---

