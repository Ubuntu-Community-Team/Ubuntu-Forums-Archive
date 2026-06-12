---
title: "moving boot hd to new hardware, would be better to resintall?"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by michelino802 on 2018-08-02
Hi,
I've ubuntu 16.04 desktop installed on amd A8 ddr3 asrock motherboard, all bought 3-4 years ago. 
now I need to purchase new hardware, I', going to get amd ryzen 5  with AM4 socket ddr4 and different motherboard and video card than the one I've now;
 I'm planning to insert my ssd hdd with ubuntu 16.04 into new pc, is it going to bring issues? shall I reinstall ubuntu on new hardware and reconfigure everything?
thanks in advance
Michele

---

### Post by 1clue on 2018-08-02
Any special drivers you had on your old setup will not apply now, but the system should boot. The window manager might not run, you may need to get other drivers.

Try it, see what happens. Get a good idea what hardware is in the new system before you start (boot off the installer or maybe system rescue cd) so you know what to install. You might install some of that before you switch drives.

---

### Post by michelino802 on 2018-08-02
ok I'll try and let you know as soon as I'll receive my new hardware
thanks

---

### Post by monkeybrain20122 on 2018-08-02
If you use a proprietary graphic driver in the old setup, uninstall it first  and revert to the open driver (unless your new setup uses the same driver). Otherwise it shouldn't be a problem, I have been cloning the same OS and restore to different machines or booting the same hard drive off different machines for a while. Oh you may need to fool around with grup if your new setup is uefi but the old one was not.

---

### Post by 1clue on 2018-08-02
while you're booted on the new system using system rescue cd, open a terminal (or just boot to command line) and type 'lspci -k' to get a list of what drivers are being used by what pci device. On your old hardware, try to make sure those modules are available before you switch drives.

---

