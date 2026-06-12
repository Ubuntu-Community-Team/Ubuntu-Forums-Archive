---
title: "So, How can I install Ubuntu - Core 2 Duo, Abit AB9"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by v8YKxgHe on 2006-12-07
Hey,

I was up first thing on the Edgy release day, waiting patiently (ok not that patiently hehe) to download my copy of Edgy! I heard some talk about Edgy not working on Core 2 Duo setups, but I was hopeful that it would work. 

But, after waiting for the download to finished I found out that Edgy would not install on my PC, here are the specs:

Intel Core 2 Duo E6600
Abit AB9
1GB GeIL PC 5300
2x SATA 2 Wester Digital hard drives ( 1 for Windows, one for Ubuntu )
1x IDE 80GB Maxtor hard drive as a storage hard drive ( keep my music and other files on there )
ATI X800XT
1x IDE DVD/RW - which I _think_ is slave to the IDE 80GB Maxtor - I'll have to check.

I played around with getting Edgy to install a few times, and I did infact manage to install it. But when I restarted my PC to boot into Edgy, it just hung at the boot screen after 1 tiny tiny little bit of progress bar had gone. 

I haven't been on Ubuntu, or any Linux distro actually for 3 months, I need my Ubuntu back!

If someone could help me install Ubuntu Edgy, I'd be so happy.

---

### Post by drtvasudevan on 2006-12-08
hmmm.
it is a problem.
see [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
it is a 965 chipset problem.
even the current feisty alpha is not working.
tested today.

---

### Post by v8YKxgHe on 2006-12-08
What I can't understand is why the latest and greatest Kernel doesn't work - yet a 5 year old OS ( WinXP ) installs and works flawlessly, with no additional drivers.

---

### Post by Sowe on 2006-12-08
> **AlexC_ said:**
> What I can't understand is why the latest and greatest Kernel doesn't work - yet a 5 year old OS ( WinXP ) installs and works flawlessly, with no additional drivers.

Probably because the motherboard developer tested the motherboard with Windows and not with Linux. The 965 is a new chipset designed for Core 2 Duo from what I understand. This is still a world where hardware developers assume that everyone in the universe is using Windows. It's so bad in fact that the label on the hard drive I bought the other day has instructions on it for configuring with Windows XP. :rolleyes:

---

### Post by pasuuna on 2006-12-13
I have the following setup:

Abit AB9 (non-Pro)
Core 2 Duo E6600
Seagate SATA hard drive connected to the Intel ICH8-controller
IDE DVD+-RW connected to the IDE controller as the master drive

I downloaded the 64-bit version of Ubuntu Edgy and booted the computer from it. The install went without a hitch and all hardware works perfectly out of the box (audio, gigabit ethernet...)

The only problem is that GRUB will not recognize my USB keyboard. If I go to the BIOS setup and set "USB Keyboard support" from "OS" to "BIOS", GRUB will work fine but Ubuntu will not boot. Windows will not boot either if legacy keyboard support is on (?). I solved this by using my old PS/2 keyboard.

---

