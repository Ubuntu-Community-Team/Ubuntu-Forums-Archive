---
title: "Problems with Ubuntu 19.10 on Dell E6500"
date: 2019-12-03
forum: Installation &amp; Upgrades
---

### Post by captaincyril on 2019-12-03
I have a Dell E6500 (4GB RAM, NVIDIA 256MB VGA, Core 2) and it has an original Windows Vista running on its hard disk and there is no problem with the hardware.

I installed Ubuntu 18.04, 18.10 and 19.04 on a USB stick and did not have major problems. My main problem with 18.04 is that it had CPU usage 100% on boot which I solved by running the below right after booting:

[COLOR=#C5C8C6]sudo systemctl stop systemd-udevd systemd-udevd-control.socket systemd-udevd-kernel.socket
sudo systemctl start systemd-udevd systemd-udevd-control.socket systemd-udevd-kernel.socket
[/COLOR]
18.10 and 19.04 did not have any major problems but I preferred to stick with 18.04 until 19.10 was released.

I tried installing 19.10 three times and I had the exact same problems in all three times after the installing the very first update:
1) I have funny pixels that keep blinking on an off. These pixels never show when I "Try Ubuntu". See picture below (pixels in below screenshot have been drawn and are not the original). The originals come in three colors: Purple, Red and White pixels. They look more like the Alien in Space Invaders lying on its side. [COLOR=#000000]The blinking pixels did not go away when I switched from NVIDIA to Nouveau driver. I noticed that on certain sessions, they are more frequent than others. When the pixels are persistent and during shutdown I get a black screen instead of the Ubuntu Purple color and the 5 red/white dots are in purple squares.[/COLOR]
[ATTACH=CONFIG]284544[/ATTACH]
2) After the first update, the grub gets damaged and I get "Bad Environment Block" and I have to clear it and also reset the "GRUB".
3) In all versions of Ubuntu (18.04, 18.10, 19.04, 19.10) on that Dell, it hangs every few minutes anywhere from 3 to 10 seconds which makes it unbearable to use. Example I click on Maximize or Scroll the Page and I have to wait for around 10 seconds for it to do so. In System Monitor it shows 1.6 GB out of 3.9 GB used and CPU usage is around 4%. Then it works normally for a couple of minutes and then it hangs again.

I never had any of above problems when I installed Mint 18.1 on the same USB stick.

I only install Chrome, Visual Studio Code and FileZilla using Ubuntu Software. During installation I set the timezone to Beirut/Lebanon and use the Full Installation with Installation of Third Party Drivers and Update while installing.

I wish to use Ubuntu 19.10 because of its speed and fluidity. I would appreciate it if anyone can advise on fixing these issues.

---

### Post by captaincyril on 2019-12-03
I installed the same Ubuntu 19.10 ISO on VirtualBox and had no problems.

---

### Post by mörgæs on 2019-12-04
Do you get the same problems if you try one of the lighter Buntus?

---

### Post by captaincyril on 2019-12-04
I installed Mint which is based on Ubuntu and had no problem whatsoever. What Buntus do you recommend? I have 8 flavors of Linux on my VirtualBox on my newer laptop but I wish to have 19.10 running flawlessly on my Dell. Do you recommend I wait for 20.04?

---

### Post by mörgæs on 2019-12-04
You could try L/Xubuntu 19.10.

---

### Post by captaincyril on 2019-12-04
Thank you. I am downloading Lubuntu now and will give it a try on Sunday and revert back.

---

### Post by captaincyril on 2019-12-06
I downloaded Lubuntu and Zubuntu and tried them on VirtuaBox and I did not really like them. They lack a lot of features eventhough they are very light on the system.

Nevertheless, I downloaded the plasma desktop on the Ubuntu 19.10 and the funny pixels and hanging are gone now. Moreover, the system is much smoother with less memory usage. I tried the plasma and ubuntu (unity) desktop versions and the problem does not exist any longer.

---

### Post by mörgæs on 2019-12-06
Good, please mark the thread solved.

---

### Post by captaincyril on 2019-12-13
After a few days the laptop started to act funny again. The blinking pixels and hanging have resumed. This is not happening when I boot on Windows Vista from the hard disk. It is happening only when I book on Linux from the USB. However, the hanging is not as bad as before but the bad pixels are in the exact same place when I ran Unity. Now using KDE Plasma.

---

### Post by mörgæs on 2019-12-14
Your thread is still marked 'solved'. If you want to attract people's attention better to remove the mark.

Also providing the full hardware specifications might help people diagnose the problem. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by captaincyril on 2019-12-16
Thanks for you help, Mörgæs. Anyway I formatted the USB and installed Kubuntu this time and it is running great so far. Actually it is taking much less memory (0.8 GB) than installing Ubuntu and then installing the KDE Plasma interface (1.2 GB). However, I could not find Chrome, Visual Studio Code and Thunderbird easily in Kubuntu's Discover but I managed to install them.

I just wanted to add this note to the thread in case anyone else had the same problem.

---

