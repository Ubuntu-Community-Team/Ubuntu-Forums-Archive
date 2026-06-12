---
title: "Ubuntu wont detect hard drives."
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by zachhill91 on 2008-07-27
I built a computer with:
AsRock K10N750SLI-WIFI motherboard
AMD Athlon X2 6400 @ 3.4GHz
nVidia 8600GT 512MB

Hard Drives:
Western Digital 300GB Velociraptor
Western Digital 250GB
Maxtor 150GB USB External Drive

When I try to install Ubuntu all it detects is my Maxtor USB hard drive, it does not detect my internal SATA hard drives.

I have the same issue when I try to install OS X on this comuter, a guy over at those forums told me it could be my chipset (nVidia nForce 750a Sli SPP) Could this be the same issue for Linux?

I have tried different distrobutions also just to check and it doesn't seem to work with any of them.

Windows is all that I can get to detect my hard drives.

Thanks in advance for help.

---

### Post by tamoneya on 2008-07-28
in ubuntu please open up terminal (applications -> accessories -> terminal) and run the following command:```
sudo fdisk -l
```Hopefully it just did not automount them in which case we can just add them to fstab but we will determine what needs to be done from the output.

---

### Post by zachhill91 on 2008-07-28
I am installing from Windows. I will know more after I boot. Hopefully it detects my SATA drives once its installed.

Thanks for the reply though. If they arn't detected for some reason still I will try your sudo fdisk -1 idea.

---

### Post by tamoneya on 2008-07-28
> **zachhill91 said:**
> I am installing from Windows. I will know more after I boot. Hopefully it detects my SATA drives once its installed.

Thanks for the reply though. If they arn't detected for some reason still I will try your sudo fdisk -1 idea.

it is a lower case "L" not the number "one"```
sudo fdisk -l
```

---

