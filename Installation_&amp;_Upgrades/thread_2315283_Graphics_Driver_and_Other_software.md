---
title: "Graphics Driver and Other software"
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by Angrry on 2016-02-27
Hello! I'm a fan of Ubuntu since a long time and now, I want to make my Laptop Dual-Boot (Windows 7 & Ubuntu 15.10). Ok, after this I installed Ubuntu 15.10 OS and other software inside the clean operating system like TeamSpeak, Steam, Skype. But I don't know how to use my graphics card. I have some in Additional Drivers but I've found some run file on Nvidia site and also some terminal commands. Which one I should use? In Additional Drivers I have 3 options and The checked one is X Server or something like that, I tried to swich but at System Settings -> Details, Graphic Card is: Intel Haswell Mobile. I tried their run file because it's their driver and it should work, but to install it I had to stop X server, so I followed first answer of this [http://askubuntu.com/questions/149206/how-to-install-nvidia-run](http://askubuntu.com/questions/149206/how-to-install-nvidia-run)  but then my screen was showing some text: [ok] start light display manager and that was all. Now I reinstalled the Ubuntu operating system again and tried to install the driver from terminal, so i followed this: [http://ubuntuhandbook.org/index.php/2015/04/install-nvidia-driver-346-59-in-ubuntu-from-ppa/](http://ubuntuhandbook.org/index.php/2015/04/install-nvidia-driver-346-59-in-ubuntu-from-ppa/) But now when I start it i have a back screen, and I only hear the sound of login screen. I don't know what to do. I need something new and good, I waste a lot of hours for reinstalling Ubuntu for ~10 times in one month and I had a lot of problems, now with 15.10 they are gone but I don't know how to proper install my graphics because it's diffrent from every machine.
My Laptop is:
Acer Aspire E5-572G
- Intel Core i5-4210M 2.6 GHz - 3.2 GHz (Turbo) with Intel HD Graphics 4600
- Nvidia GeForce 940M - 2 GB VRAM
- 4 GB RAM
- 1 TB HDD

I used 64 bit Ubuntu and maybe I missed some libaries or something, the HDD is split like this: -~800 GB Windows 7 & ~200GB Unused Space (There is Ubuntu Installed when I installed it). 
I don't know so many about commands and Ubuntu, because I can't used it so far, I didn't had a powerfull machine. But know I have and I want to use it, but so far I can't. I've searched a lot and didn't fixed anything.
And if there is any other software to install like 32 bit libraries or I don't know. Thank you for your attention!

---

### Post by grahammechanical on 2016-02-27
I have not read all or your post. I find it difficult to see what is important when there is a large block of text.

When we install Ubuntu we are invited to tick a box that says Install third party software. If we tick that box we get some proprietary but free audio & video codecs and also a proprietary video driver. So, you may already being running on a proprietary video driver from when Ubuntu was first installed.

The Additional Drivers does a very good job of finding proprietary video drivers. It will offer 2 drivers and each version will have 2 variant versions (updates & tested). It should not be necessary to download and install a driver from the manufacturer's web site. And we certainly need to know what we are doing and how to remove the driver should something go wrong.

At the Grub boot menu we can select Advance option for Ubuntu. Selecting that will open a sub menu and we can select a Linux kernel to load that has a recovery mode. When we load a recovery mode Linux we get a recovery menu. Select Resume. That may get us to a working desktop by not using the proprietary video driver. Then we came use System Settings>Software & Updates>Additional Drivers tab and try to activate a video driver that works.

You have hybrid graphics. An Intel graphic adapter and a Nvidia graphic adapter. It is called Nvidia Optimus technology. But Nvidia does not provide a driver for Linux that does automatic switching between Intel & Nvidia graphic adapters. But the Nvidia driver provided through Additional Drivers should also provide a manual means of switching through the Nvidia settings utility.

And if you are going to play games (Steam) you may certainly need to switch from the Intel adapter to the Nvidia adapter.

Regards.

---

