---
title: "Help, how do I find/install my drivers on ubuntu?"
date: 2019-08-02
forum: Installation &amp; Upgrades
---

### Post by katiegrayx3 on 2019-08-02
I just built my new computer and got ubuntu 18.04 on a flash drive and did the iso thing and booted it from that but the screen just goes black like 2 seconds into the ubuntu desktop and I assume it's because I don't have the drivers on the pc and I have no idea how to get them on there because just sticking the CDs in the CD drives didn't do the trick

Motherboard: Ax470-10 "Version 1.0"

GFX Card: Strix Rx Vega 64 "V1388"

---

### Post by ubfan1 on 2019-08-03
Take a look at [https://askubuntu.com/questions/1130050/vega-64-amdgpu-driver-unloading](https://askubuntu.com/questions/1130050/vega-64-amdgpu-driver-unloading)
Maybe try 19.04 to see if that works any better.

---

### Post by katiegrayx3 on 2019-08-03
I can't even get into the desktop, I have to do everything from the recovery terminal, and I have no idea how to even find my drivers in the first place

---

### Post by Autodave on 2019-08-03
Normally in Ubuntu, all the drivers you will need are in the OS already.  However, some bleeding edge new hardware may have issues.  That is why it was suggested to you that you try 19.04. 19.04 is a newer, short term release. 

With either your 18.04 or 19.04, can you boot from the install medium and run anything?  (After booting to the medium, choose to "try" and see if things work that way and report back.

---

### Post by oldfred on 2019-08-03
Do not know AMD systems.
But generally have you updated UEFI, many new systems still have an update available.
Also if SSD have you updated SSD firmware?

Have not seen your new card, but some slightly older versions had some issues that probably are the same.
       Vega GPU is built into the CPU, then the M.2_2 socket cannot be used. 
[https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199](https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199)
Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)
Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247)
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)
Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)

---

