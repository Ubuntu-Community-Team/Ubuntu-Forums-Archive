---
title: "Install Network Manager"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by spandey on 2010-02-26
Hi,
I am newbie to Linux. Network Manager was giving me real pain after recent update. It was not connecting to Lan.  So I tought I will uninstall it and reinstall. 
I went to synaptic and uninstalled. But unable to install now.

How can I install Network Manager now?

---

### Post by Steven_B on 2010-02-26
Why can't you install it?

If you don't have a network connection (or Ubuntu CD), you're not going to be able to download NetworkManager.  In this case, it's probably easiest to use another computer to download the files and copy them to your computer with a flash drive.  From there, you should be able to double-click on the packages to install them, or use
```
sudo dpkg -i nameOfTheFile.deb
```

[http://packages.ubuntu.com/karmic/network-manager]("http://packages.ubuntu.com/karmic/network-manager")
[http://packages.ubuntu.com/karmic/network-manager-gnome]("http://packages.ubuntu.com/karmic/network-manager-gnome")

---

### Post by n0dix on 2010-02-27
You always can to connect manually. 
Try with:
```
$ sudo dhcpcd eth0 
```
or 
```
$ sudo dhclient eth0 
```
and then
ping to google.com

---

### Post by spandey on 2010-02-27
Thanks. But in Synaptic i have selected all option but Network Manager is not shown in the right.

---

### Post by spandey on 2010-02-27
Strange Today it's available under Synaptic. I have installed it.

---

