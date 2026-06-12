---
title: "Asus P5LD2 Deluxe -- Nothing works?!"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by scwks on 2005-07-12
Hi there,

I had nothing but trouble trying to install ubuntu with this motherboard. Could someone help me if you had success with the same motherboard or these following chipsets:

ICH7R south bridge -- I hooked two WD SATA drives to it, set up in RAID0. Doesn't seem to be seen by the installer. Asked me for driver floppies which I don't have (how do I get/build one?), then told me that no suitable media can be found to install to.

ITE8211F ATA controller -- Doesn't seem to be detected either. I originally had the DVD drive and a PATA drive connected through it, but the installer refuses to proceed because it cannot identify the CD (which is pretty stupid because it can't see itself). I then moved the DVD drive to the onboard UDMA port.

Marvell Gigabit ethernet controller -- Doesn't work. Asked me for driver modules which I don't have.

This whole situation feels hopeless. Help me, please!

---

### Post by Dark79 on 2005-07-18
[QUOTE=scwks]Hi there,

I had nothing but trouble trying to install ubuntu with this motherboard. Could someone help me if you had success with the same motherboard or these following chipsets:

ICH7R south bridge -- I hooked two WD SATA drives to it, set up in RAID0. Doesn't seem to be seen by the installer. Asked me for driver floppies which I don't have (how do I get/build one?), then told me that no suitable media can be found to install to.

ITE8211F ATA controller -- Doesn't seem to be detected either. I originally had the DVD drive and a PATA drive connected through it, but the installer refuses to proceed because it cannot identify the CD (which is pretty stupid because it can't see itself). I then moved the DVD drive to the onboard UDMA port.

Marvell Gigabit ethernet controller -- Doesn't work. Asked me for driver modules which I don't have.

This whole situation feels hopeless. Help me, please![/QUOTE]

I have a P5WD2, so I also feel your pain. I had to use the non ITE IDE connector to get Ubuntu to recognize my hard drive for the install. Once I got hoary installed, I compiled 2.6.13-rc3 which included drivers for the ITE IDE connectors (the same as yours, I think), Intel HD audio, temp sensors, Intel Gigabit ethernet. 

The only problem I had was that ATI's 8.14.13 drivers are broken in 2.6.13 (and probably other earlier kernel versions) so I had trouble getting fglrx drivers installed for 3D acceleration with my X800XL. But once the drivers were patched, I got that fixed too. 

I don't know anything about SATA since I don't have a SATA drive as of yet, but I do know that to install on an IDE hard drive, you need it connected to a non ITE port. Does your board have that? On mine, the ITE connectors are for hard drives only. If I connect any ATAPI device (CD-ROM, etc) I get BSODs (in Windows, too) 

Now I just gotta figure out what Wifi drives will work with the Asus Wifi-TV card... EDIT: drivers on CD + ndiswrapper work so far.

Hope that helps.

---

### Post by ubuntu_demon on 2006-01-29
Did it ever got working ? / Does anyone have a P5LD2 working with Ubuntu ?

---

### Post by shmoolik on 2006-04-05
yeah i would like to know too

---

### Post by Meshigen on 2006-04-19
i have the same problem, and i dont understand
the allmighty linux cant handle with such a minor problem?

i want to install linux :cry: :cry: :cry:

---

