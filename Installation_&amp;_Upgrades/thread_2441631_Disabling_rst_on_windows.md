---
title: "Disabling rst on windows"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by YBcPttm on 2020-04-25
I'm trying to install Ubuntu on my laptop. As I was installing it said that I had to disable the rst. When I went to the help page it says that I need to go to my Device Manager and check the controller mode. The issue I'm having at the moment is that I can't find that controller mode to find out if it's set to [FONT=Ubuntu]Standard SATA AHCI Controller. I have a windows 10 dell laptop.[/FONT]

---

### Post by oldfred on 2020-04-25
My old Haswell based Dell had it under Advanced.

Some older Dell seemed to need Legacy enabled, but set boot to UEFI. Newer systems need legacy turned off.
My old Haswell based Dell. has these settings.
Under Advanced: USB enable, On board device, AHCI.
Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode UEFI.
But then every USB installer has two boot modes UEFI:flash or flash where flash is name or label of flash drive. And one with just name is the BIOS/legacy/CSM boot mode.

If dual booting with Windows, you must first install the AHCI drivers into Windows.

What model Dell?
But the changes in UEFI settings for Dell are common across most models. Bigger difference if AMD or Intel based.

Dell XPS 16 9570 experience of installing Ubuntu 18.04 LTS
[https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe](https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe)
[https://ubuntuforums.org/showthread.php?t=2408749](https://ubuntuforums.org/showthread.php?t=2408749) & 
[https://ubuntuforums.org/showthread.php?t=2408585](https://ubuntuforums.org/showthread.php?t=2408585)
XPS 13 [SOLVED] dock Dell TB16 does not work  - needed Firmware updates & UEFI setting
[https://ubuntuforums.org/showthread.php?t=2431141](https://ubuntuforums.org/showthread.php?t=2431141)
[https://ubuntuforums.org/showthread.php?t=2433026](https://ubuntuforums.org/showthread.php?t=2433026)

---

