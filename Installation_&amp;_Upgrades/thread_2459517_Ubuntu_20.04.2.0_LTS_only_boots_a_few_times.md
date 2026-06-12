---
title: "Ubuntu 20.04.2.0 LTS only boots a few times"
date: 2021-03-20
forum: Installation &amp; Upgrades
---

### Post by jasonpheral on 2021-03-20
I have a Dell G5 laptop that I want to dual boot Windows 10 and Ubuntu. The SSD the laptop came with was around 100 gigs and Windows was using most of it. So I installed a new 500 gig SSD. Initially I had lots of problems getting anything to install on the new SSD. I was finally able to get Ubuntu to install first using the whole drive and then I shrank down the largest partition in Ubuntu and installed Windows in there. This obviously deleted linux's boot up menu. I got that fixed and everything working fine for about 5 reboots and then I was no longer able to boot Ubuntu. I select it at the boot menu, press enter and I end up with a flashing courser in the top left corner and nothing else happens. I installed Ubuntu two more times trying to fix this. The same thing keeps happening, it will boot fine for several times and then Ubuntu stops booting. I haven't installed any new software, all I have done is upgraded installed software. This doesn't affect windows at all. It will boot fine every time.

---

### Post by blackbird34 on 2021-03-20
Have you checked the UEFI (BIOS) settings? My laptop UEFI can tell the difference between Linux and Windows, but maybe Windows might have changed something and caused Ubuntu to not boot for some reason.

---

### Post by CelticWarrior on 2021-03-20
As above.

It's fundamental to understand [UEFI and its boot process]("https://help.ubuntu.com/community/UEFI"). Then familiarize yourself with your vendor specific UEFI settings and how to set both drive and OS boot order. Windows feature updates often change the OS boot order to Windows. Users then must change it back to Ubuntu (Grub) at UEFI settings. 
Unless you understand this, perfectly and inequivocally, you'll always have such problems.

---

