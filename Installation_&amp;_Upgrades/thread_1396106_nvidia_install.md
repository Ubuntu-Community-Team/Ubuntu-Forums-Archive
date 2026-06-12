---
title: "nvidia install"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by hcarothers on 2010-02-01
I have installed the nvidia gt 220 card driver.  I went into system/administration & hardware drivers and installed.  I got a message that said,  You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  I don't understand could someone help please....

---

### Post by Sean Brown on 2010-02-03
I got the same thing, but I removed and then rebooted, then reinstalled it, then restarted which got me going.  I'm still having issues but that one is fixed.

---

### Post by yogesh.girikumar on 2010-02-03
Hi,
You can type the following in the terminal for help with nvidia-xconfig command
```
$ man nvidia-xconfig
```To see the list of possible options you can use with this command, type:
```
$ nvidia-xconfig --help
```To restart x-server you press CTRL+ALT+BACKSPACE. Another way of doing this is going to the terminal and typing the following :  ```
$ sudo /etc/init.d/gdm restart
```      You might also like to see these links. They could be very helpful.
       
[LIST=1]
[*][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[*][http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)
[*][http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
[*][https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[/LIST]
HTH

---

