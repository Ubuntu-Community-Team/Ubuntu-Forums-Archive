---
title: "Installs but does not save"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by wavynelson on 2016-09-12
Hello! My problem is that once I install ubuntu, it does not save it or make any changes to the boot menu. Also when installing it already says it has installed ubuntu twice! If I wanted to I can keep on installing forever and nothing saves! Please help! Here are some links to what I see:

[http://imgur.com/a/wd4AK](http://imgur.com/a/wd4AK) (This is the full album of screenshots that I have taken. They go in order from what I did during the beginning and end of installation.)

---

### Post by ubfan1 on 2016-09-12
A UEFI mode installation requires that you have an EFI partition to hold the bootloaders.  sdb does not have an EFI partition, which you probably should have (definitely if sdb is an USB or other removable).  Does sda have an EFI partition?  If not, and you are dual booting, your installation is not in UEFI mode, and you should install UBuntu in legacy mode.

---

### Post by wavynelson on 2016-09-12
Thanks for the info, but can you explain how to do this? Im new to it and dont want to mess up anything or have any problems trying to figure it out.

---

### Post by oldos2er on 2016-09-12
> **wavynelson said:**
> dont want to mess up anything or have any problems trying to figure it out.

In that case I hope you multiple tested backups.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

