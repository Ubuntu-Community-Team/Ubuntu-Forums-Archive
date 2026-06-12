---
title: "xubuntu to ubuntu !! need help"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by hydroparasite on 2008-02-08
[B]hi[B]
 i just installed the Xubuntu flavour , and luckily i also received the ubuntu shipped CD just after xubuntu was done ! well upon checking out the Gnome thing , i liked it a lot better than the XFCE environment . So i need to remove and install ubuntu 7.10 over it and do not wanna ruin up my windows installation , as my pc i dual boot . So i would like some help in in doing the above described task while not ruining the boot loader . 
thanks in advance ... :popcorn:

---

### Post by Rocket2DMn on 2008-02-08
Hey, welcome to Ubuntu, you can convert your installation to Gnome from Xfce.  Have a look here - you will want the last command listed (remove Xfce and install Gnome): [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

If you want to keep Xfce alongside Gnome, you can just run
```
sudo apt-get install ubuntu-desktop
```
Then at the login screen you can choose between Gnome and Xfce.

---

### Post by hydroparasite on 2008-02-08
hey thanks a lot bro for the prompt reply , but i was just wondering what sequence should i follow remove xfce first and then insatll gnome coz my base environment is XFCE ?

> **Rocket2DMn said:**
> Hey, welcome to Ubuntu, you can convert your installation to Gnome from Xfce.  Have a look here - you will want the last command listed (remove Xfce and install Gnome): [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

If you want to keep Xfce alongside Gnome, you can just run
```
sudo apt-get install ubuntu-desktop
```
Then at the login screen you can choose between Gnome and Xfce.

---

### Post by Rocket2DMn on 2008-02-08
It doesn't quite work like that.  Xubuntu is essentially Ubuntu with the Xfce desktop environment.  The link I gave you will remove all the Xfce stuff and install the Gnome stuff (that's what ubuntu-desktop is at the end of the command).  You don't have to reinstall the base system.
```
sudo apt-get remove abiword abiword-common abiword-plugins brasero dbus-x11 gnumeric-common gnumeric-gtk gqview gtk2-engines-murrine gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-4 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmodplug0c2 libmpcdec3 libots0 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage python-exo tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird totem-xine vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

---

### Post by hydroparasite on 2008-02-08
thanks bro i ll try that n get back to you ! :mad:


> **Rocket2DMn said:**
> It doesn't quite work like that.  Xubuntu is essentially Ubuntu with the Xfce desktop environment.  The link I gave you will remove all the Xfce stuff and install the Gnome stuff (that's what ubuntu-desktop is at the end of the command).  You don't have to reinstall the base system.
```
sudo apt-get remove abiword abiword-common abiword-plugins brasero dbus-x11 gnumeric-common gnumeric-gtk gqview gtk2-engines-murrine gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-4 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmodplug0c2 libmpcdec3 libots0 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage python-exo tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird totem-xine vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

---

