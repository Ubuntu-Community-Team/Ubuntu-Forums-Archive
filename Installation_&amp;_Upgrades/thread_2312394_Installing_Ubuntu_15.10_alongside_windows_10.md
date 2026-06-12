---
title: "Installing Ubuntu 15.10 alongside windows 10"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by ranit2 on 2016-02-04
hi,
I need help installing ubuntu 15.10 (64). When I try to install or run ubuntu it stucks at UBUNTU animation. I have made a efi usb with unetbootin. And the specification of my laptop is as under (If it may help):

Lenovo-y50-70
processor- i7-4720hq
Gpu- nvidia 960m (2GB)
Ram- 4GB

---

### Post by sandyd on 2016-02-04
Hi,

The graphics card may not be compatible with the open source drivers.

Give the following a try.

When starting up from USB, hit the tab key.

You should get a menu, choose F6, and then choose 'nomodeset'. press ESC, and then ENTER.

Does it boot up now?

---

### Post by ranit2 on 2016-02-05
Thanks Sandyd, after pressing 'e' and replacing a string in by 'nomodeset' I am able to boot into Ubuntu. I am able install Ubuntu successfully. But now after installation when I try to boot into Ubuntu laptop hangs at pink-purple screen and restarts into grub. I have searched the forums and till now what I have got is only that if I want to use Ubuntu then every time I have to press 'e' and then replace a character with nomodeset. Isn't there a permanent solution for it. Please help I am new to this Ubuntu.

---

### Post by Vladlenin5000 on 2016-02-05
You need to do the same procedure so you can have video just like during the installation, then install the recommended proprietary drivers.

---

### Post by ranit2 on 2016-02-06
I have installed the nvidia drivers for 960 m ver:352.79 by downloading .run from nvidia but now I can't boot even by ’quiet nomodeset splash' and it stucks at the purple screen permanently .

---

### Post by Bucky Ball on 2016-02-06
*Thread moved to **Installation & Upgrades**.*

How did you intall the Nvidia driver? Are we to believe you have Ubuntu installed? If that is the case, you shouldn't be installing them manually via a terminal. That driver should appear when you click 'Additional Drivers'.

If you do have Ubuntu installed and are now getting a log in loop it might pay to post another thread as you're original problem, can't install Ubuntu, has changed to 'login loop when trying to boot Ubuntu'. If you are trying nomodeset and that is not working, graphics probably isn't your issue (although installing the driver from the nvidia website manually may have muddied the waters there). 

Please give us a clear indication of where you are at with it now. Have you successfully installed or not yet?

---

### Post by ranit2 on 2016-02-06
Earlier when I was trying to install or try Ubuntu system was  freezing on purple screen. Then I have posted this thread. After that sandyd helped me and by using nomodeset I was able to install Ubuntu on my laptop. After Installation when I tried to reboot it again stuck at purple screen.After that  I was able to use or login by adding nomodeset at the grub menu. I have searched the web and what I understand is that I have to install nvidia drivers for getting it work without using nomodeset. I have downloaded the nvidia .run file from nvidia support site. Then I have installed it by using terminal. Now Ubuntu only boots to purple screen even after using nomodeset.

---

### Post by Vladlenin5000 on 2016-02-06
Sorry, that was partially my fault. In post#4 I merely alluded to the need for nomodeset again in order to be able to install the drivers and finally enjoy your hardware's full potential.
Perhaps I should have mentioned that the drivers you should have installed are already available in the official repositories and that you can easily install by using the Additional Drivers (System Settings > Software Properties), a process which is also entirely graphical.

In order to (try to) correct the mess the nvidia installer seems to have made I suggest the following:

1. As before, press CTRL+ALT+F1, and login.
2. ```
sudo apt-get purge nvidia*
``` This should get back the open source driver that doesn't work.
3. Boot with [I]nomodeset.
[/I]4. Install the proprietary drivers _as described above_.

Good luck.

---

### Post by Bucky Ball on 2016-02-06
If nomodeset worked first time and you just need to know how to make it permanent and that is all, easy, read on.

Open a terminal and open this file:

```
sudo /etc/default/grub
```

Look for this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

You know what to do:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Hit control+x, 'y' and enter then when back at the terminal cursor:

```
sudo update-grub
```

Reboot and should be fixed. ;)

---

### Post by ranit2 on 2016-02-07
@Vladlenin5000, I can't login because as soon as Ubuntu starts it freezes at purple screen. Nomodeset doesn't work
@Bucky, now nomodeset is not working laptop only shows purple screen.

---

