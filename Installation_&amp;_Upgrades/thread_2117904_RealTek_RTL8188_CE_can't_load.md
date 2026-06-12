---
title: "RealTek RTL8188 CE can't load"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by Patrick White on 2013-02-19
I do not know how to load the driver for this. First, I am new to Ubuntu, and second the only driver I can find is a tar.Bz2 file. I understand that when I figure out where to put the file I will have to use sudo to be able to put it where I want but the file is on my Windows partition. I have figured out where I can find the file but am just getting into Ubuntu so don't even know where it needs to go so the GUI can find it. Any and all help will be greatly appreciated. This is for my wireless device.

---

### Post by zFish on 2013-02-19
Going to try my best at helping cause I had problems with this and had to do research on getting it going. I'm sorry if leave something out, I'm learning linux as we speak but I hope I can help you out.    1. Make sure you ```
sudo apt-get install linux-headers-generic build-essential
```  2. Download your driver from realktek. Extract to your home directory for easy finding. Go into your terminal CD to the extracted directory.While in the directory ```
sudo make
``` ```
sudo make install
``` ```
sudo reboot
```

---

