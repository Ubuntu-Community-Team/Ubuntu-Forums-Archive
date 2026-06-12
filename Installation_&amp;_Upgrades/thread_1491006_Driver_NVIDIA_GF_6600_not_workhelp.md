---
title: "Driver NVIDIA GF 6600 not work??help"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Gilankzz on 2010-05-23
i have GF 6600..when i have install Karmic i was install driver NVIDIA for my GF6600 then finish n restart..

but when my CPU booting to Ubuntu..Its Blank..the Driver its not work(Make my Ubuntu Error).. 

Then i Install New Ubuntu Lucid..then i Install the Driver again(i think its will work)...But when i restart n Booting to Ubuntu...Same Error again, The Driver make Blank Screen??:mad:

Why??? AnyBody can help me to solve the Problem???

---

### Post by DoricMan on 2010-05-24
I had the same problem as you describe.
 
My system is a dual boot Ubuntu 10.04 LTS - the Lucid Lynx and XP. In view of the problems that were happening on NVIDIA graphics cards I decided to replace the NVIDIA 6600 video card with a Radeon 4550.

Now my system has adequate video performance for my dual boot needs.

---

### Post by alterpinguin on 2010-05-24
have an sparkle AGP GeForce 6600 in my older computer running since years with 8.04 and shorter time with ubuntu 9.04 until i swapped it against an GeForce 6800 passive cooled. Now i have the old card in an older 32-bit computer and if it would help, i can try it with the 32-bit-ubuntu-10.04 version to check the lspci output of the hardware (but i need to download the install-cd first, cause i use only the 64bit version till today).
And you should post the lspci output for this hardware part to check against other hardware settings/combinations (the mainboard-type may be usefull too)

---

### Post by gradinaruvasile on 2010-05-24
You have to disable KMS + blacklist the nouveau driver.

---

### Post by alterpinguin on 2010-05-24
> **gradinaruvasile said:**
> You have to disable KMS + blacklist the nouveau driver.

KMS is using "nomodeset" now?
and blacklisting a module
means ?-?-?(pls. correct if false) to enter it
into /etc/modprobe.d/
like in, for example:
/etc/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
---
i wonder, why this is already in my configuration...
running the nvidia-current (version 195.36.15) for graphics

---

### Post by Gilankzz on 2010-05-26
Thaks..i will try it...:popcorn:

---

