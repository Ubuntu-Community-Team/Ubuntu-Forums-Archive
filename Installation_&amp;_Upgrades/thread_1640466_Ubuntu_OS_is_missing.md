---
title: "Ubuntu OS is missing"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by hussainv1 on 2010-12-07
Hi friends,

I was using windows XP and UBUNTU 10.04 lucid linux Operating systems on my computer. I had my Ubuntu installed on (f:) directory and C,D,E directories were used by Windows XP. Usually i used to get option for selecting the OS while starting the computer(Here in my case XP or Ubuntu). Since my XP got corrupted, i formatted my C: drive and again installed windows XP in the same directory where it was previously installed. Having done that, windows XP is working fine. But to my great shock, i'm not getting the option for selecting the OS at boot time and windows XP starts automatically. Can somebody please help me fix this? Thanks in advance :)


Best regards,
Hussain

---

### Post by tommcd on 2010-12-07
> **hussainv1 said:**
>  Since my XP got corrupted, i formatted my C: drive and again installed windows XP in the same directory where it was previously installed. Having done that, windows XP is working fine. But to my great shock, i'm not getting the option for selecting the OS at boot time and windows XP starts automatically.
How did you install Ubuntu?
If you installed using Wubi (inside Windows) then your Ubuntu was obliterated when you reinstalled XP.
If you did a real linux install and installed Ubuntu properly to a dedicated linux partition, then XP took control of your master boot record (MBR), and you will need to reinstall grub2 to the MBR to get Ubuntu back.
See this tutorial on reinstalling grub2  after installing Windows:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Also, if you did a real linux install to a dedicated linux partition, post the output of:
```
sudo fdisk -l
```
This is to make sure that you still have a linux partition to boot.

And welcome to the Ubuntu forums!

---

