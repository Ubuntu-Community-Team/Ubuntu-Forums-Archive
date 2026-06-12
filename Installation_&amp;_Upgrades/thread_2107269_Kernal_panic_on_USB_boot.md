---
title: "Kernal panic on USB boot"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by CodeRedxBG on 2013-01-21
Trying to install Ubuntu 12.10 from USB stick(s). Kernal panic or crash everytime. Tried two USB sticks, using LiLi and UUI. Here's a couple screen shots.

Is there any way to correct this, other than updating BIOS? I wanted to install Ubuntu because Windows Vista and 7 have been giving me issues, but if I need to install them anyways, I'll just stick with them.

One USB gets to "Using MCRYPT for buffer copies" then restarts the laptop.
One USB shows me the kernal panic error and the 30 second count.

HP Pavilion dv9843cl
T8100
4GB Ram (which is fine btw, passed memtest)
Nvidia 8600GS

Edit: The CPU/GPU fan/heatsink are installed properly, clean, with AS5 paste. Also, I checked MD5 and it matched.

---

### Post by gordintoronto on 2013-01-21
One of your screen shots made me go to this page:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

where it describes disabling APIC.

If Windows is giving you blue screens, and Ubuntu doesn't boot, that indicates hardware issues with your computer.

---

### Post by kibosh81 on 2013-01-21
agreed. 

Its no coincidence that regardless of the OS, you are having problems. I suggest getting your machine checked out. I am no pro with Linux, but I am a regular MAC user. Every time I have had a kernel panic, its been hardware related.:cry:

---

