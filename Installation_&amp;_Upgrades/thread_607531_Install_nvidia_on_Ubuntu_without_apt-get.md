---
title: "Install nvidia on Ubuntu without apt-get"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by mul14 on 2007-11-09
I want to install nvidia driver on Ubuntu 7.10. But I don't have internet connection or Repository DVD. So I can't use any command like apt-get, wget, deb, bla.. bla..

I already download NVIDIA-Linux-x86-100.14.19-pkg1.run from nvidia website.

I use this command in recovery mode.
```
runlevel --set=3
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```
but it doesn't work.

Anyone can help me?


Hm, sorry if my english is bad.

---

### Post by forestpixie on 2007-11-09
what error do you get

---

### Post by mul14 on 2007-11-09
This the error message. > Ubuntu is running in low-graphics mode.

Your screen and graphics card could not be detected correctly....


Almost forgot. If after install nvidia, run startx command (not restart pc or use reboot command), ubuntu can detect my graphic card and  I can use the desktop effect.

---

### Post by Fire_Chief on 2007-11-09
After you run the NVidia installer and it completes, try running```
sudo nvidia-settings
```

---

### Post by Pumalite on 2007-11-09
The driver will not complete installing because it needs the net.

---

### Post by mul14 on 2007-11-12
Problem solved.
first, when ubuntu has been loaded. open terminal by press ctrl+alt+f1 and login.
enter this ```

sudo /etc/init.d/gdm stop
sudo killall gdm
```
make sure gdm has been killed by press ctrl+alt+f7.
enter this```
runlevel --set=3
sudo -H sh NVidia-xxx.pkgx.run -a
```
after installation completed restart, gdm.
```
sudo /etc/init.d/gdm restart
```
nvidia logo should appear.

---

