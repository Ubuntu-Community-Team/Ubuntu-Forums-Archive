---
title: "Multiple Issues when installing 32 bit netboot installer"
date: 2018-12-10
forum: Installation &amp; Upgrades
---

### Post by diy2124 on 2018-12-10
I'm about 2 weeks into experiencing Ubuntu...and I've learned more than I thought I ever would so far.

I have an old Compaq mini-110 that I'm trying to install Ubuntu version 18.04/18.10 onto. So far I have successfully installed 17.04 (32-bit i386) from an .iso file from the website. This Release works perfectly fine on the mini, however, I would like to update to the latest release in order to download apps and have updates to security etc.. After watching youtube videos, I learned that in order to get the latest release, I would have to download the mini.iso from the netboot installer page. As soon as I choose the option to install I see ***undefined video mode:314. ***It lets you pick different resolutions (0-6) but I'm not sure if it's working due to the the next error that I will refer to soon (When installing from the iso, this message never appeared). I've also seen that you can change vga= something but I have no idea how to get to that. It lets me continue with the install. I follow the instructions throughout the install. It says it has installed successfully. I reboot and Instead of going to the GUI, I'm in ***tty1***(?). I sign in and only get a command prompt***. ***I've tried to do the ctrl+alt+F1-F12 but none of them got me out of this. I also saw on a forum that you could Check where display-manager.service is pointing  to and if it was pointing to an old lightdm version to switch it to the gdm version. I went to "ls -la /etc/systemd/system" and saw nothing that referred to a display-manager.service. So my questions are: Is the undefined video mode the reason why the I'm going to tty1 or are these separate errors? If they are separate instances: How do I get to change the vga so the undefiended video mode error goes away? Am I missing something in the install that is causing me to go straight to the tty1 instead of going to the GUI. Thanks in advance for your help.

---

### Post by wildmanne39 on 2018-12-10
18.04 does not come in a 32 bit it was discontinued.

---

### Post by Impavidus on 2018-12-10
The Ubuntu live installer for 32 bit has been discontinued, but the minimal installer and light flavours are still available as 32 bit. On an old computer I think you want one of the lighter flavours anyway. The Lubuntu live installer is probably easier than the minimal installer.

[https://lubuntu.net/downloads/](https://lubuntu.net/downloads/)
[https://www.ubuntu.com/download/alternative-downloads#network-installer](https://www.ubuntu.com/download/alternative-downloads#network-installer)

---

### Post by diy2124 on 2018-12-11
[http://cdimage.ubuntu.com/netboot/18.10/?_ga=2.43147809.584314978.1544553058-1173495117.1542215713](http://cdimage.ubuntu.com/netboot/18.10/?_ga=2.43147809.584314978.1544553058-1173495117.1542215713)

I understand they discontinued the live installer for 32 bit. That's why I was attempting to use the netboot installer (link above). From what I know, this netboot installer installs the bare minimum on to your pc to get you started so you don't have to worry about disc space\ram. I watched multiple videos of people installing this way but I'm sure the computers they are installing on are not as old. I installed a couple versions of Lubuntu successfully on to the computer but for some reason it wipes out the drivers for my network adapter. I could go to Software & updates in order to get them back on ubuntu. On lubuntu, there isn't a software & updates to get the drivers from.

---

