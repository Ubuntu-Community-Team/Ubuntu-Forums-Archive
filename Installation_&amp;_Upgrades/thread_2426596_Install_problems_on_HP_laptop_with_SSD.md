---
title: "Install problems on HP laptop with SSD"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by kajoky on 2019-09-11
I have an HP 14-cf1051od laptop with an SSD that currently has Windows 10.
I would like to make Linux the only operating system.
I have disabled fast start up in Control Panel.
I have been in the BIOS and tried different combinations of Secure Boot and Legacy Support.
I have tried Ubuntu, Xubuntu and Linux Mint.
The Long Term Support versions of Ubuntu and Xubuntu will lock up before getting to the desktop.
The most recent releases of Xubuntu and Linux Mint will get to the desktop and lock up at different times.
The farthest I have gotten in installation is to choose language then at keyboard, when I click Continue it will always lock up.
In searching, I have come across references that suggest changing SATA to AHCI.
I cannot find anywhere on this laptop that will allow me to change SATA.
That seems to be the problem and maybe it is not possible to install Linux on this laptop but I hope that someone here could help me or suggest a different Linux that might install.

---

### Post by mastablasta on 2019-09-11
what does lockup mean? are there any messages? if only blank screen can you get into console or see messages with esc? what is the GPU? have you tried nomodeset ?

Make sure the image is good. try it on another known good PC if you can. otherwise there are verification tools you could use on it (MD5SUm, various disk checks & file checks). when i was installing i couldnt' get any USb image to work, so i used DVD in the end. only later i found otu the error is in the implementation of image burning programs. hopefully they corrected those errors.

i am a bit interested how this will play out. they have some nice and interesting 15 models over here at a descent price. however it seems best is to use the G models. they are the business versions and should support linux. They do run SUSE on some models that i saw. this could be an option here as well - to try OpenSUSE. it's a solid distro and might be interesting to try it if nothing else to see if it can boot. i also hope you gave 19.04 a try, if this is a very new machine then 19.10 beta might also be an idea.

---

### Post by kajoky on 2019-09-11
With the long term support versions, the screen will show the name and either a spinner or dots that change color. When it locks up the spinner or dots become static. I have let it sit there for 20 to 30  minutes and nothing further happens. I tried nomodeset once but no difference.

The image is good. I followed the instructions in Ubuntu's verify tutorial. I was able to install to a different computer that has a HDD.

I tried 19.04 and it sometimes gets to the keyboard question but always locks up when I click Continue. The mouse cursor becomes a spinner, then a static image and then nothing happens until I press and hold the power button to turn the laptop off.

I have not seen 19.10 or OpenSUSE. I will look for them and give them a try.

Thank you for the suggestions.

---

### Post by oldfred on 2019-09-11
Have you updated UEFI and if SSD, SSD firmware.

Some with HP have said it works or works better after UEFI update.

HP historically was not good at UEFI boot of anything other than "Windows Boot Manager" by description. Use of description is specifically NOT allowed by UEFI standard.
If only booting Ubuntu one of the work arounds was change "ubuntu" UEFI entry to have Windows description. Another was to boot the hard drive or fallback boot entry at /EFI/Boot/bootx64.efi which often is just a copy of Windows .efi boot file. If a copy of Ubuntu's grub/shim boot file then you can boot Ubuntu and Windows.

---

### Post by kajoky on 2019-09-11
Thank you.

I will see what I can find about updating UEFI and SSD firmware.

---

### Post by mastablasta on 2019-09-12
> **oldfred said:**
> 
HP historically was not good at UEFI boot of anything other than "Windows Boot Manager" by description..

i found the linux now website from australia which confirmed my suspicion. the Probook G models (business laptops) seem to have very good linux compatibility. in the past the business models were sold here with SUSE preloaded. but now they come with freeDOS or win10.

---

