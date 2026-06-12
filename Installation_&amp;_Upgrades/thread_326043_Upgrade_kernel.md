---
title: "Upgrade kernel?"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by hhhjr on 2006-12-26
Hello, I am trying to get my nexus-s DVB card to work. I am trying to set up mythtv. I have successfully set it up with a Happauge PVR 500 and wanted to get my DVB card up and running. After countless hours and reading many post it appears that the Nexus-s support is broken in the 2.6.17 kernel. Ok no problem I did my research and attempted to upgrade my kernel to 2.6.19-1. I followed all the steps and sucessfully compiled the kernel. When I attempted to reboot I got errors, so after some more research I was told that sometimes a kernel build will build sucessfuly but will not compile correctly. I then tried it again with the same results. I then tried again fooling around in the menuconfig to try to get it to run with my Sata drive thinking maybe it was the issue and I still get the same errors. This is what I get:
Starting up...
uncompressing linux.... Ok, booting kernel
[    35.481858]intel_rng; FWH not detected
[    36.087085]ACPI: Getting cpuindex for acpiid 0x1
ALERT!    /dev/sda1 does ot exist.
Dropping To A Shell
 I am running a intel cerlon 2.8ghz  and the mother board sata controller is a ICH5 on a 865g chipset. The kernel I was trying to compile was from [www.linux.org](www.linux.org)

From what I understand I need either kernel 2.6.15 or 2.6.18 or above to get my Nexus running. I actually had it installed in the 2.6.17 kernel and it was recogonized and the firmware seemed to load corectly just that I could not get it to open, Ie "Failed to open device". Any help would be greatly appreaciated. Thanks

---

### Post by pay on 2006-12-27
What steps did you use to compile the kernel.

---

### Post by hhhjr on 2006-12-27
Hope links are ok here [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) this is the guide I used. Thanks for the reply.

---

### Post by pay on 2006-12-27
Do you have a separate /boot partition? What lines did you use in your /boot/grub/menu.lst?

---

### Post by hhhjr on 2006-12-27
Sorry newbie here, I have 3 partitions 1 is ext3, 2nd is a swap and the third is xfs. this is the guide I used for the install [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)   , although I previously did the complete install, I am only working with the base system at the moment because I have to compile the nvidia and ttpci drivers with the new kernel at least that is what I am assuming. Thanks again.

---

### Post by hhhjr on 2006-12-27
deleted

---

### Post by hhhjr on 2006-12-31
I had the same results with the 2.6.18.6 kernel. Any ideas?

---

### Post by hhhjr on 2007-01-02
bump

---

### Post by hhhjr on 2007-01-06
bump

---

### Post by hhhjr on 2007-01-16
So I guess I am the only person with this issue?

---

