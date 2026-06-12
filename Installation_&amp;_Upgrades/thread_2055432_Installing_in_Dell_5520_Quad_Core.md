---
title: "Installing in Dell 5520 Quad Core"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2012-09-09
So,
 
I wanted to step up to a quad core so I bought a Dell Inspiron 5520. I specifically asked Dell if I could install Ubuntu on the unit and they said yes.
 
I have a couple of questions. The bootloader crashed half-way through when I tried to load a year old verion of Kubuntu from a flash drive and this unit has Intel Centrino WiFi.
 
Am I going to have problems with either the installation or WiFi when I install?
 
Please Help.
 
 
 
Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2012-09-13
Bump!

---

### Post by oldfred on 2012-09-13
The install CD does not include all wireless drivers, did you install with Ethernet hard wired connection as recommended. It will then usually download added drivers if needed.

If you have issues booting after install, you can run this from LiveCD or download as a full repairCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by critin on 2012-09-13
> **coljohnhannibalsmith said:**
> So,
 
I wanted to step up to a quad core so I bought a Dell Inspiron 5520. I specifically asked Dell if I could install Ubuntu on the unit and they said yes.
 
I have a couple of questions. The bootloader crashed half-way through when** I tried to load a year old verion of Kubuntu** from a flash drive and this unit has Intel Centrino WiFi.
 [B]
Am I going to have problems with....\--- WiFi when I install?[/B]
 
Please Help.
 
Thanks Hannibal

New computer hardware mixing with year old wifi drivers?  Possibly.  The devs have to build the drivers after the hardware is released.    Most distributors don't share their sources so ubuntu devs will need to catch up; ***as far as I know***.
Still, posting your issues here will get you the right help.

You might have better success with the newest version of ubuntu, but you will still want to install using a wired internet for sure, as already mentioned.

---

### Post by coljohnhannibalsmith on 2012-09-17
critin,

I did as you suggested and ubuntu installed correctly and supplied the added drivers.

I did further research and discovered that my system is designated as "certified" by Canonical; boy was I lucky! And thanks for your help.

Hannibal

---

