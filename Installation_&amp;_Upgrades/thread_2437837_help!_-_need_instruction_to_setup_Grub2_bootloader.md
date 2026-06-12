---
title: "help! - need instruction to setup Grub2 bootloader on existing ubuntu/win10 disk"
date: 2020-03-01
forum: Installation &amp; Upgrades
---

### Post by mrsean on 2020-03-01
Hi Everyone, please can you provide instruction to setup grub1 bootloader on existing install of windows10 and ubuntu.
BIOS eufi will let me choose, but would like to setup Grub2 for better interface and functionality.

Here is my current boot-load info:  [http://paste.ubuntu.com/p/6wZZQ7rBnF/](http://paste.ubuntu.com/p/6wZZQ7rBnF/)

My partitions info is attached

thanks, Sean

---

### Post by Impavidus on 2020-03-02
Your Windows is installed in UEFI mode, but your Ubuntu appears to be installed in legacy mode. There's no Ubuntu entry in your EFI partition, grub is installed in the MBR and there's a separate bios_grub partition. There's a lot of poor advice on the internet that may have tricked you into installing it this way. Both have to be installed in the same mode to allow grub to boot both of them. Once you fixed that and Windows isn't hibernated, os-prober (running as part of update-grub) should automatically pick up Windows.

Furthermore, your swap partition is ridiculously large.

It is possible to convert a legacy install of Ubuntu into a UEFI install. I've never done it myself, but this may help: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (scroll down to "Converting Ubuntu into UEFI mode"). I don't know how well that works.

Some sources in the internet suggest it's easier to do a fresh install.

---

### Post by mrsean on 2020-03-02
Thanks Impavidus!
I think its because I set up ubuntu ages ago in earlier version, then recently found the partition and and upgraded to latest version. Plus my AMD BIOS has legacy mode compatability support mode.
Tried to use boot-repair as it seemed an easy option but from within legacy mode its not going to work. In this instance I think a clean install of ubuntu is going to be best option.
Re-installing also deals with large swap issue, and I will disable csm in BIOS too to disable re-occurance, better to keep UEFI all the way!

---

### Post by CelticWarrior on 2020-03-02
You need to boot the UDB in UEFI mode. With UEFI + Legacy enabled you should see two entries for the same device, choose the one mentioning "UEFI".

A clean install of Ubuntu is certainly a good solution but may not be the "best", it depends on how much time you want to spend on it. Converting to UEFI mode should be easy and painless and takes just a couple of minutes.

---

### Post by yancek on 2020-03-02
Reading through the official Ubuntu documentation at the link below on dual booting with windows 10 UEFI will save you a lot of future problems.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mrsean on 2020-03-02
Thanks all, I did clean install and boot loader working perfect. Was best solution to get me set up right quickly.

---

