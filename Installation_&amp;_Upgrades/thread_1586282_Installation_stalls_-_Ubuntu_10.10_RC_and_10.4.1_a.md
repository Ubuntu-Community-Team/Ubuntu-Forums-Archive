---
title: "Installation stalls - Ubuntu 10.10 RC and 10.4.1 and NVIDIA problem"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by Kvignola on 2010-10-01
Installation stalls on my computer after choosing language and keyboard. 
I tried 10 times. Happened  every time with 10.10 RC and 10.4.1.
Happened with two different HDD'S (WD and Seagate).
Happened in IDE AND AHCI mode.

I went around the problem by plugging my HDD in another computer for the installation wich went fine. Afterwards, plugged the HDD back in my computer and it boots fine.

Also, once NVIDIA driver is installed, computer boots into command line. Had to remove the driver.

Computer is:
AMD Phenom II X4 965
Gigabyte 890FXA-UD5 (latest bios)
4 gb corsair memory
Asus EN9600GT silent
HDD: Seagate Barracuda 7200.12 500gb

---

### Post by Kvignola on 2010-10-02
It seems that the problem lies with Ubuntu's support of the SB850 Chipset, since Installation of Fedora 14 beta went fine. 
I found a workaround: Unplug all other drives and plug the target drive in port 0 of the AMD controller. The motherboard also has a gigabyte controller wich works, but it is slower (3gb/s). You can then reconnect all your drives. Workaround is OK in IDE or AHCI mode.

The nvidia driver never worked in Ubuntu; it may also be related to the amd chipset.

---

### Post by Kvignola on 2010-10-11
For the Nvidia problem it isn't related to the chipset support (not directly). Removal of an Hauppauge Wintv-HVR 1600 corrected the problem.

---

