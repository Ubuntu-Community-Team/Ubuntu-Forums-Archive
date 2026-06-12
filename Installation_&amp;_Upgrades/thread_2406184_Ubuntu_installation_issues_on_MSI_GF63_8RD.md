---
title: "Ubuntu installation issues on MSI GF63 8RD"
date: 2018-11-17
forum: Installation &amp; Upgrades
---

### Post by loch87 on 2018-11-17
Hi to everyone! :)

I'm trying to install Ubuntu 16.04 or 18.04 on my new laptop. I've made everythings, starting from the UEFI settings to GPT or MBR settings. 

At first nothings worked, till i've made an USB boot with a disk image (not ISO), so it start in live mode. I've checked that everythings worked and it seems like it. 

So i started with the installation, it worked good, but at the end of the installation (when ubuntu ask to reboot your pc) my laptop when freezed, so i forced the shut down and rebooted manually. The Grub worked good and so i tried to launch Ubuntu. Nothing the laptop when freezed another time. I tried to change the kernel from .39 to .29, also i tried the recovery mode but it didn't work.

After a long search i've found a thread - [https://gist.github.com/mari-linhares/cef4cb3440408e44963d1447a7db5ae0](https://gist.github.com/mari-linhares/cef4cb3440408e44963d1447a7db5ae0) - that gives the advice to find in the Ubuntu installation option to f[COLOR=#24292E][FONT=-apple-system]ind the line that starts with [/FONT][/COLOR]*linux*[COLOR=#24292E][FONT=-apple-system] then add [/FONT][/COLOR]*modprobe.blacklist=nouveau*[COLOR=#24292E][FONT=-apple-system] after [/FONT][/COLOR]*quiet splash*[COLOR=#24292E][FONT=-apple-system]. 

I've tried also this but nothing changed. 

So what's happening? I've been thinking that could be an issues of the chipset. But if Ubuntu start in the "live mode" why it doesn't work after the installation?

Thanks to everyone that could and would help me! 

Loch87[/FONT][/COLOR]

---

### Post by oldfred on 2018-11-17
Have you updated UEFI from MSI?

Other threads on similar models also have some different boot parameters:
       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues)
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by loch87 on 2018-11-17
I didn't try to update it. Now i'll do it! Thank you! :)

---

### Post by killfall on 2018-11-26
Did you have any luck with this?

I'm currently trying to install ubuntu 18.10 on my GF63 8RC. So far I cannot even get the installer to boot. I've tried disabling secure boot and everything no but luck. Could you point me towards the installer image you used?

---

### Post by mucelee on 2018-12-08
Hey there Loch87!
I am having exactly the same problem on this laptop and currently I am booting it with acpi=off and quiet splash enabled in grub. It allows me to boot but I cannot see battery, cannot use hotkeys.
I wonder if you tried updating the UEFI or anything else? If you have managed to get Ubuntu working properly on this laptop, can you share what you did? thanks

mucelee

---

### Post by realskorpion on 2018-12-24
Hi guys,

I have the same laptop.  Yesterday I tried to install Linux and had the same issue.
I'm not a Linux guru but after hours of pain, I was able to install Ubuntu (Linux Mint 19.1 that is based on Ubuntu 18.04).
"Live mode" works because it uses an open source driver but after installation it probably uses the nvidia drivers.

So I did something like this:
1. Secure boot disable (change this in BIOS, reboot the system and press delete a couple of times before the OS is loaded)
2.  Install Ubuntu "normally"
3.  Reboot and try to open a terminal:

  Possible problem: Screen freezing while installing/rebooting
-Reboot system
-Go to the Install Ubuntu option (BUT DONT PRESS ENTER)
-Press e
-Replace "quiet splash" with "nomodeset".

4.  Remove all the nvidia drivers and install the open source video drivers:
 
  $ sudo apt purge nvidia-driver*
  $ sudo apt autoremove
  $ ubuntu-drivers devices (this command will show you a list of nvidia drivers and one open source driver, use the name of the open source one in the next command)
  $ sudo apt install xserver-xorg-video-nouveau
  $ sudo reboot

After this, Ubuntu should start normally. Install something like timeshift (and create a snapshot of your system) before trying to install the nvidia drivers.

It seems other people are having a similar issue:
https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1767594
Please, go to the previous link and let them know the issue affects you.

For now, I'm using the open source video drivers, maybe in some days I 'll try to install the nvidia drivers or I'll wait until somebody with more knowledge could give us a better/permanent solution.

I hope this helps.

Thanks,
Oscar R

---

