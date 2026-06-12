---
title: "Can't boot ubuntu after automatic install on lenovo ideapd 320"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by moda20 on 2018-10-18
hey i just installed ubuntu 18.04 LTS and had a big problem booting to it .

The installation was easy and it worked like charm, i did choose to delete everything and install ubuntu.
but then it didn't boot, when i turn on my computer it just stays at a black screen with white text.

I did try to fix Grub, create custom boot paths, change from UEFI to legacy and back to UEFI but with no use. 

help ! 

Note: this also happened on my second lenovo Ideapad which i unwrapped today.

---

### Post by ajgreeny on 2018-10-18
Some idea of the specification of the computer will help us to help you more than we can at the moment. It could be one of many problems so we need this info to have any real idea where to point you.

Show us the output of command ```
inxi -F
``` which will give us a lot for a start.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by oldfred on 2018-10-18
What video card/chip?
UEFI or BIOS install?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

