---
title: "Gutsy upgrade issues?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by kfealz on 2007-10-18
I can't wait to upgrade from feisty to gutsy, but my roommate tried to upgrade to with the RC the other night and it caused a whole mess of problems for him, so I just wanted to find out a few things before i upgrade.

If I have compiz installed with restricted drivers via envy (NVIDIA 8800 GTX), upgrading will automatically remove my drivers and install the new ones?  It will successfully replace all of my compiz files?

Also, has anyone tried upgrading with any of this hardware?

Motherboard: ASUS P5B Deluxe WiFi-AP Edition
CPU: Intel® Core™2 Duo Desktop Processor E6600
Memory: CORSAIR Dominator 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1111 (PC2 8888) Dual Channel
Storage: Seagate Barracuda 500GB 7200 RPM SATA 3.0Gb/s x 2 = 1 TB :D
Graphics Card: EVGA GeForce 8800GTX 768MB GDDR3 PCI Express x16
Sound Card: Creative Sound Blaster X-Fi XtremeGamer 7.1 Channels
PhysX Card: BFG Tech PhysX Processing Unit 128MB GDDR3
Optical Drives: HP 20X DVD±R DVD Burner with LightScribe IDE Model dvd1040i
Generic DVD-ROM drive

(I am aware that my PhysX card and Sound Card are not supported yet)

Finally, I've seen a few things about people saying to disable automatix.  Is this necessary for me?

Thanks a lot,
Fealz

---

### Post by linuxwizard on 2007-10-18
[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade. If you have used EasyUbuntu or Automatix (neither of which is recommended nor supported), you may have problems upgrading to a newer version that requires a fresh install.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by kfealz on 2007-10-18
Awesome, thanks a lot.

The only repositories I've added are:

#compiz
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

#irssi
deb [http://www.davidpashley.com/debian/irssi-sarge/](http://www.davidpashley.com/debian/irssi-sarge/) ./

These should not cause a problem when upgrading, right?

Thanks in advance -- can't wait to hit that update button :)

---

