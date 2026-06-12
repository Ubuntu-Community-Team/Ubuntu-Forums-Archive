---
title: "After Important HW and Security update I have black screen 14.04.1"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2016-08-27
A[ while back]("https://ubuntuforums.org/showthread.php?t=2332177") I upgraded to 16.04.1 but couldn't get the monitor to work so I gave up and reinstalled 14.04.1
Tonight I installed an "Important Hardware and Security update". On restart i lost the monitor.
I tried to enter grub. I held down the shift key when AMD flashed but it booted to an ubuntu login with a different resolution.
I see the log in but then nothing.
Firstly I have to enter grub? But first I have to slow grub down? I can run 14.04.1 off DVD.
If I can access grub I can load an older kernal
Then what?
I can connect to the TV by HDMI/

---

### Post by MadMax2 on 2016-08-27
From syslog
Aug 28 12:43:24 P kernel: [  275.617907] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery reached max voltage 
Aug 28 12:43:24 P kernel: [  275.617940] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery failed

I have bought a new monitor (with  HDMI slot)  and it works.
[Solved by upgrading Hardware]

---

