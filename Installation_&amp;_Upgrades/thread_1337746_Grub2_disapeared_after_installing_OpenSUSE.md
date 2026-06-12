---
title: "Grub2 disapeared after installing OpenSUSE"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by ZacK.YoveL on 2009-11-25
Hi, I installed the last vertion of OpenSUSE on different partitions (aoutomatic option) next to Ubuntu 9.10. The Ubuntu Grub menu doe'snt show and the OpenSUSE don't give me any option to get to Ubuntu.

---

### Post by audiomick on 2009-11-25
Hi. Read about that the other day. The suse installation apparently writes over the grub installation, and doesn't include other systems. ( quite rude of them, if you ask me... )
Your Ubuntu should still be there, but you will have to re-build your grub. I'm not game to try and tell you how, because I am not that sure of it myself.

---

### Post by presence1960 on 2009-11-25
> **audiomick said:**
> Hi. Read about that the other day. The suse installation apparently writes over the grub installation, and doesn't include other systems. ( quite rude of them, if you ask me... )
Your Ubuntu should still be there, but you will have to re-build your grub. I'm not game to try and tell you how, because I am not that sure of it myself.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You will need your Ubuntu 9.10 Live CD/USB & follow the instructions. This will restore GRUB 2 to MBR.

---

