---
title: "Webcams not recognized in Xubuntu 18.04"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by peyre on 2018-05-13
I upgraded to the latest version of Xubuntu 64-bit, but that trashed the way windows displayed--the bar at the top disappeared on all windows and I couldn't close things properly--I could fix it but I had to fix it every time I booted.  So no big deal, I backed up my data and reinstalled from scratch.  Now Xubuntu runs great on it, except I can't seem to use a webcam on it.  (I'd like to get this working today if possible, for Skyping with Mom this evening.)

My laptop is a Sony Vaio with a VGP-VCC6 [R5U870], and on my previous installations of Xubuntu I've successfully installed it by running this in a terminal:
```
sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 
```
So this time I ran all that and it worked fine.  The camera was working in Skype too.  But now a few days later it's not.  I reran the lines above, but still, Skype audio & video settings, under Camera, says No device found, and Cheese says No device found.  Last night we Skyped and I could see them and they could hear me, but couldn't see me.  I also tried plugging in a USB Creative webcam, but still neither program sees it.  If I run **lsusb** I get the following for the two webcams:
```
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd. Visual Communication Camera VGP-VCC6 [RSU870]
Bus 002 Device 003: ID 041e:4063 Creative Technology, Ltd. Live! Cam Video IM Pro
```
What's going on?  Anyone have a suggestion for how to fix this, for either or both cameras?

---

### Post by peyre on 2018-05-18
Uh...bump?  Anyone?

---

