---
title: "Live Ubuntu 22.04 on USB will not boot on a specific laptop"
date: 2022-11-20
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2022-11-20
I have been running Ubuntu 22.04 on a HP Probook 4540s. Originally I had installed 20.04 and I upgraded later to 22.04. Recently, during a reboot, the laptop showed an error message "UVD not responding, trying to reset the VCPU". It would not go further and it froze while booting. Googling a bit for help, I tried editing Grub (version 2.04) by adding "nomodeset" just before "quiet splash". It goes further in booting, and I get the login screen but my keyboard and touchpad does not work.


Not wanting to waste time, I decided to do a complete fresh install of Ubuntu 22.04. I downloaded the ISO, loaded it onto a USB. But the live version would also not boot, freezing just before I reach the desktop. I noticed that the Grub version on the USB is 2.06. I checked if the USB is good and it works on my other laptops (Lenovo, Toshiba). No problem on getting live Ubuntu running on these.


So does anyone have any advice on what to do to get the fresh install working on my HP?

---

### Post by oldfred on 2022-11-20
It looks like an old bug, but fixed several versions ago. Sometimes bugs re-appear?
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1865130](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1865130)

I do not know AMD based video cards, but others may need to know exactly what card/chip your system has.

---

### Post by srope01 on 2022-11-20
Looking at HP documentation, the laptop has

Processor: Intel Core i7-3612QM (2.1 GHz, 6MB L3 cache, 4 cores)
Chipset: Mobile Intel HM76
Graphics Adapter: AMD Radeon HD 7650M (not exactly sure, there is a Radeon graphics label on the laptop)

I noticed that the launchpad bug report is rather old (they refer to Bionic 18.04). Supposedly it was solved back then and now it has come back probably in the latest version of 22.04. I had just downloaded the ISO a few hours ago, so it is the latest version.

Any advice on what I should do? I can't even install Ubuntu.

---

### Post by oldfred on 2022-11-20
Can you in UEFI settings turn off the AMD chip/card.
Most have some sort of graphics settings.
Some users have posted they could install with video card disabled using internal video. Then with working system installed correct driver & enabled video card. But I think that was with nVidia.

---

### Post by tea for one on 2022-11-20
> **srope01 said:**
> Any advice on what I should do? I can't even install Ubuntu.
Originally, you installed Ubuntu 20.04, perhaps try that version again?

---

### Post by #&amp;thj^% on 2022-11-20
> **oldfred said:**
> Can you in UEFI settings turn off the AMD chip/card.
Most have some sort of graphics settings.
Some users have posted they could install with video card disabled using internal video. Then with working system installed correct driver & enabled video card. But I think that was with nVidia.

I can confirm on legion 5 AMD/Nvidia, disabled Nvidia at install or transplant drive to different machine.

---

### Post by srope01 on 2022-11-20
> **oldfred said:**
> Can you in UEFI settings turn off the AMD chip/card.
Most have some sort of graphics settings.
Some users have posted they could install with video card disabled using internal video. Then with working system installed correct driver & enabled video card. But I think that was with nVidia.

I am using Legacy BIOS. I will see what I can do to turn off radeon and then install. If it works and then I manage to install the driver, that would be workaround, but I think it would be better if the developers were to find a fix and put it in the installation ISO.

---

### Post by srope01 on 2022-11-20
> **tea for one said:**
> Originally, you installed Ubuntu 20.04, perhaps try that version again?

Interesting. I downloaded both the 20.04 and 18.04 ISO and tried to install them one after the other. In both cases I managed to boot into Live Ubuntu. But in 20.04 case, when I clicked on the install icon, it didn't do anything. In 18.04, the first dialog box concerning the language appeared. Then when I clicked continue, it froze. I think I need to try an older release of 20.04, ideally the same one that I used to install Ubuntu the first time.

---

### Post by ne29914 on 2022-11-20
The Hps of that age with legacy BIOS are normally unproblematic.
You'll need to go into the BIOS setup again for the settings. Turn off any "optimizations" and make sure it will boot from something other than the HDD.
Take some pictures of the BIOS screens/menus.

---

### Post by C.S.Cameron on 2022-11-20
On my old (BIOS only) HP EliteBook I press F9 immediately after pressing the power switch. A screen comes up to allow me to select the disk I want to boot from.
I have not been able to get 22.04 to run very well. 
The mouse and keyboard do not work once it has booted.

Edit:
So far **mkusb** has worked best for me creating the 22.04 Live/Persistent flash drive.
I use the GRUB 2.02 option.

---

### Post by srope01 on 2022-11-21
> **srope01 said:**
> Interesting. I downloaded both the 20.04 and 18.04 ISO and tried to install them one after the other. In both cases I managed to boot into Live Ubuntu. But in 20.04 case, when I clicked on the install icon, it didn't do anything. In 18.04, the first dialog box concerning the language appeared. Then when I clicked continue, it froze. I think I need to try an older release of 20.04, ideally the same one that I used to install Ubuntu the first time.

I downloaded an early point release, 20.04.01, and this time not only did I get the Live Ubuntu, but it also installed! However, when I tried to login to my account, I got a blank purple screen and it froze.

So I have tried to installing the following. Only with the last one did I manage to get Ubuntu installed.

ubuntu-22.04.1
ubuntu-20.04.5
ubuntu-18.04.6
ubuntu-20.04.1

My only hope now is to turn off the radeon card in BIOS and see what happens. In any case, I would like to submit a bug report to the developers. How do I go about doing that?

---

### Post by srope01 on 2022-11-21
> **srope01 said:**
> Interesting. I downloaded both the 20.04 and 18.04 ISO and tried to install them one after the other. In both cases I managed to boot into Live Ubuntu. But in 20.04 case, when I clicked on the install icon, it didn't do anything. In 18.04, the first dialog box concerning the language appeared. Then when I clicked continue, it froze. I think I need to try an older release of 20.04, ideally the same one that I used to install Ubuntu the first time.

I downloaded an early point release, 20.04.01, and this time not only did I get the Live Ubuntu, but it also installed! However, when I tried to login to my account, I got a blank purple screen and it froze.

So I have tried to installing the following. Only with the last one did I manage to get Ubuntu installed.

ubuntu-22.04.1
ubuntu-20.04.5
ubuntu-18.04.6
ubuntu-20.04.1

My only hope now is to turn off the radeon card in BIOS and see what happens. In any case, I would like to submit a bug report to the developers. How do I go about doing that?

---

### Post by srope01 on 2022-11-21
> **srope01 said:**
> 
My only hope now is to turn off the radeon card in BIOS and see what happens. In any case, I would like to submit a bug report to the developers. How do I go about doing that?


I was able to turn off the card by toggling a device option "Switchable Graphics" in BIOS (no indication that this is related to the radeon card). With this done, I installed 20.04.1 and this time I finally managed to logon. Having a working Ubuntu, even if it is the previous LTS version, is a big success. 

I then tried installing the 22.04.1 ISO again with the graphics card still turned off. Unlike previously, I was able to install 22.04, seemingly another step forward. But the bad news is that when I tried to boot after installation, the laptop did not recognise that there was an operating system on the hard drive (got the black page with error message asking to install an OS)!!! So there is something still seriously wrong with the 22.04.1 ISO. I went back to 20.04.1 and I upgraded from there to 22.04. I am finally back to where I started from when I had a working version 22.04 for several months.

So in summary the solution is 1) Turn off the graphics card in BIOS, 2) Install using 20.04.1 ISO, 3) Upgrade from there to 22.04 rather than using the 22.04 ISO.

Many thanks to the community for your help.

---

