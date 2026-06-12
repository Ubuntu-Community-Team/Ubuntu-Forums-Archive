---
title: "Ubuntu 20.04 heating problems, graphic cards nvidia"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by radimvana on 2020-05-14
Hello everyone,

I made clear installation of Ubuntu 20.04 on my two laptops dell m6500 workstation. One computer have nvidia quadro fx 3800 and is hot - gpu 74-75 degrees and not cooling down (no problems with Ubuntu 18.04). I tried both nvidia and xorg drivers). Other computer with nvidia quadro fx 2800 looks ok with temperature but after few minuts the display go black - can help this [https://www.dell.com/community/Laptops-General-Read-Only/Screen-going-black-but-still-running/td-p/4654576?](https://www.dell.com/community/Laptops-General-Read-Only/Screen-going-black-but-still-running/td-p/4654576?) Have anyone similar problems or can you help. Both laptops works perfect with ubuntu 18.04. Thank you very much in advance.

---

### Post by CelticWarrior on 2020-05-14
Welcome.

Have you selected the option to install drivers/firmware during the installation? If not, it didn't, and those cards really need Nvidia proprietary drivers.

---

### Post by radimvana on 2020-05-14
I must look at home, but I am nearly sure, that I selected this option. In software&drivers - additional drivers I have to choose between nvidia driver (proprietary) or xorg.

---

### Post by Perfect Storm on 2020-05-14
I have experienced that the nvidia driver wasn't enabled even that I choose third party under installation once. If nvidia-settings comes up empty that means the driver is disable.

---

### Post by radimvana on 2020-05-14
Driver should be OK, I added screen. 

Nvidia settings looks OK, added sreenshot to.

---

### Post by radimvana on 2020-05-16
Still cant fix that problem.

Laptop with nvidia 3800 is to hot and not cooling down. Second laptop with nvidia 2800 - I reinstall ubuntu 20.04 again with option to install drivers/firmware, but after few minutes using display went black again. I instaled Debian 10 and there is no problem so there is no problem with bad hardware. I am thankful for every help. I will search for help through internet, if I found somethink helpful, I will post it here.

---

### Post by Perfect Storm on 2020-05-16
Hope they fix it. Until I stay with 18.04 because I have a Nvidia card as well.

---

### Post by radimvana on 2020-05-16
One observation with PC with nvidia 3800 - is overheating only when is in power. When runs only in battery, temperature fell fast 20 degrees down.

---

