---
title: "I can`t isntall ubuntu 9.10"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by game fever on 2009-11-30
Hi all, I ordered the Ubuntu 9.10 and tried to isntall it. Here is the problem, when I try to install ubuntu 9.10 the computer is working something and than it`s just goes to sleep. I have try almost everything. USB installation, older version7.10(also an ordered CD), also I tried all the options from the f6 menu(acpi off etc.), safe mode. This happens when I need to chose a language or the time zones. I have no more ideas please help

---

### Post by phillw on 2009-11-30
> **game fever said:**
> Hi all, I ordered the Ubuntu 9.10 and tried to isntall it. Here is the problem, when I try to install ubuntu 9.10 the computer is working something and than it`s just goes to sleep. I have try almost everything. USB installation, older version7.10(also an ordered CD), also I tried all the options from the f6 menu(acpi off etc.), safe mode. This happens when I need to chose a language or the time zones. I have no more ideas please help

Hi, try the text based version (alternate install) - I'm hoping it won't have the ahcpi sleep part in it !!

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Regards,

Phill.

---

### Post by oldos2er on 2009-11-30
What are your hardware specs?

---

### Post by game fever on 2009-11-30
AMD sempron 1800 MHz, 768 mb of RAM, Foxcon nForce 3 motherboard and ati radeon 9550

---

### Post by game fever on 2009-12-01
Sorry for the double posting but here is the update I successful installed ubuntu with the alternate version. The install vent without any problems, but when I try to entered it just freezes  after I enter mu user name and pass, I see the desktop and then nothing happens some icons load and that is the end. Please help, thanks

---

### Post by darkod on 2009-12-01
The CPU and RAM seem enough. Can the video driver be an issue? You could try installing another driver if you select Recovery Mode in the grub menu. It will be text based recovery mode but the installation of the driver is easy. When asked select root with networking, so you will have internet access.
Then in the prompt just do:
sudo apt-get install envyng-core envyng-qt

You can run EnvyNG in text mode with:
envyng -t

The rest is easy. There will be option to remove current driver but I didn't do that. I just selected ATI, it downloads it automatically and installs it. That helped me but my problem was slightly different then yours.

---

### Post by game fever on 2009-12-01
I also google it that it might be the graphic card, but there is a problem, I have an ADSL connection through an USB I am guessing that setup in the  text mode is not easy for the USB modem. Is there a possibility that ubuntu does not now how to install the driver and I need to do it manually.

---

### Post by darkod on 2009-12-01
Try it, the modem might be recognized if that's what you are worried about.
There is the possibility for the current driver not to work ok. I have integrated HD3200 and it should be supported but ubuntu was restarting the computer just before it shows the login screen. I did the above mentioned procedure and worked straight away. It took me days to suspect the video driver. :)

---

