---
title: "dual boot"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by icodious24 on 2012-12-22
I have two laptops and sort of know my way around gpart how do I set up my partitions to accomplish dual boot or am I doing it all wrong .I have all the software needed just need to know the exact order of installing them cause I love this Ubuntu

---

### Post by searchfgold6789 on 2012-12-23
The easiest way to set up a dual boot is to boot from your Live CD or USB disk, select "Install Ubuntu" (or "Try Ubuntu" and then click the desktop shortcut for it), and then when the installer program gives you the option to, just select "Install Ubuntu alongside Windows". That's all. It does it automatically.

---

### Post by oldfred on 2012-12-23
If you have an available primary partition, so the installer can create the extended auto install works well for newer users.

But most Windows 7 systems use all 4 primary partitions. So then you have to decide what to do.

Post this from terminal of install ISO installed to  flash or DVD.

sudo fdisk -lu

---

### Post by icodious24 on 2012-12-24
thank you both, I dont know if I did it perfectly but its working on both my hp laptop and my acer. I just used gpart to create Three Partitions equal in size.Installed Windows first, named the second Linux swap  and then used live cd to install Ubuntu. I am prompted two choose witch system on startup and am very happy to finaly have windows on my laptop to only for my windows phone witch I actualy love. so thank you all again

---

