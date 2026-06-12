---
title: "[Question]I can't using live CD to lunch X Server!"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by jixing_alex on 2006-10-06
When I boot from live CD, my computer shows following:
Failed to start the X Server (your graphical interface).
It is likely that it is not set up correctly. Would you like
to view the X Server output to diagnose the.....?
<Yes> <No> 

I don't know what happen. 
This is my first time to using live CD to install ubuntu 6.06 LTS.

My computer:
------CPU&#65306;AMD64 Sampron 2800
------RAM&#65306;1GB
------HD&#65306;SATA 160GB
------Video Card&#65306;ATI Radeon X700 SE&#65288;RV410&#65289;&#65288;PCIE&#65289;

I also can't found a solution from web.
Please, help me.

---

### Post by Fass on 2006-10-06
Choose to boot in safe graphics mode, or whatever it's called.

If that doesn't help, press ctrl+alt+F1, log in and edit /etc/X11/xorg.conf and in the device section replace "driver "ati"" (or whatever it says) with "driver "vesa"".

---

### Post by jixing_alex on 2006-10-07
Thank your advices.

I selected safe graphics mode, but screen can't received
signal and I can hear the sound to start X Server.

After edited /etc/X11/xorg.conf, I input:
$ sudo /etc/init.d/gdm restart
but GDM still failed.

So I directly input:
$ startx
I hear the sound to start X Desktop, but screen still can't
received signal.

Whatever, thank your replay again.
Have any other ways to solve this problem?

I notice a message, my computer told me 'no screen found'.

---

### Post by jixing_alex on 2006-10-08
Who can solves it?

---

### Post by Xgrind on 2006-10-09
Hi all,

I got this problem too... I'm very new to Linux (know nothing about linux language at all) but I like to learn and get it up and running on my PC. Can anyone help?

---

### Post by Ouchy on 2006-10-09
I also have this issue, patiently awaiting any possible fix.

CPU: A64 3200+ Sckt 939.
MB: DFI Lanparty Ultra-d.
RAM: OCZ 1GB Gold VX.
VC: ATI Radeon X800XL.

---

### Post by Xgrind on 2006-10-09
I found the solution
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)

If it still don't work,
I was advised by my friend to try the x86 version as it might be 64-bit version causing the issue

---

