---
title: "Installation problem: raid 0 SSD not showing up"
date: 2022-03-25
forum: Installation &amp; Upgrades
---

### Post by adamhff on 2022-03-25
Hey! So hopefully I can get some help here. I am trying to install the latest kubuntu and am getting to the partition management area. My PC is kind of old but I have 2 SSD's in RAID 0 and a 3 TB hard drive as well. I want to dual boot and the RAID drive is not showing up in the first drop down menu, but the 3TB is. It (RAID) appears in the other drop down menus but not the one I need for dual booting. If I was more familiar I may be able to go the manual route, but that's beyond me. 

Maybe I am just not seeing something or maybe it's the RAID? 

Thanks!

---

### Post by CharlesA on 2022-03-25
Is this RAID 0 set up in Windows or through the BIOS? Assuming Windows, since you said you wanted to dual boot.

---

### Post by adamhff on 2022-03-25
It's in the BIOS I have windows installed already but yes, BIOS.

---

### Post by CharlesA on 2022-03-25
Are you able to open a terminal and run these commands?

```
sudo fdisk -l
```

```
ls -l /dev/disk/by-id/
```

---

### Post by adamhff on 2022-03-26
In the live USB?

---

### Post by CharlesA on 2022-03-26
Yes, that's correct. You should be able to hit the Windows key to bring up the search bar when booting from the live cd.

Do a search for Terminal and see if anything shows up.

---

### Post by adamhff on 2022-03-26
Sorry about the late response. I really do appreciate this. - Yes those commands work.

---

### Post by CharlesA on 2022-03-26
If the drive it showing up, it should show in the GUI as well.

I don't have much experience with trying to dual boot Ubuntu and Windows, but this might be helpful:
[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

---

