---
title: "Problem with upgrade from 9.10 to 10.04"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by SoftTaco on 2010-07-08
I recently tried to upgrade to 10.04 and it failed somewhere on the installation process. I managed to get the machine to boot and go into gnome but now very few programs will actually launch (terminal, nautilus and firefox is about it) and the install/update software reports al sorts of dependency issues

i.e. 
> E: libpango1.0-common: subprocess installed post-installation script returned error exit status 1
E: libpango1.0-0: dependency problems - leaving unconfigured
E: libglade2-0: dependency problems - leaving unconfigured
E: libgnomecanvas2-0: dependency problems - leaving unconfigured
E: libbonoboui2-0: dependency problems - leaving unconfigured
E: libgucharmap7: dependency problems - leaving unconfigured
E: libpanel-applet2-0: dependency problems - leaving unconfigured
E: libwnck22: dependency problems - leaving unconfigured
E: libcanberra-gtk0: dependency problems - leaving unconfigured
E: libedataserverui1.2-8: dependency problems - leaving unconfigured
E: librsvg2-2: dependency problems - leaving unconfigured
E: libgnomekbd4: dependency problems - leaving unconfigured
E: libmetacity-private0: dependency problems - leaving unconfigured
E: gnome-settings-daemon: dependency problems - leaving unconfigured
E: python-gtk2: dependency problems - leaving unconfigured
E: python-gmenu: dependency problems - leaving unconfigured
E: gnome-menus: dependency problems - leaving unconfigured
E: librsvg2-common: dependency problems - leaving unconfigured
E: gnome-icon-theme: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: python-gnomecanvas: dependency problems - leaving unconfigured
E: libgnomeui-0: dependency problems - leaving unconfigured
E: python-gnome2: dependency problems - leaving unconfigured
E: gnome-about: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: google-chrome-beta: dependency problems - leaving unconfigured
E: ttf-sazanami-gothic: subprocess installed post-installation script returned error exit status 1
E: ttf-sazanami-mincho: subprocess installed post-installation script returned error exit status 1
E: gnome-games-common: dependency problems - leaving unconfigured
E: aisleriot: dependency problems - leaving unconfigured
E: alacarte: dependency problems - leaving unconfigured
E: apport-gtk: dependency problems - leaving unconfigured
E: libgksu2-0: dependency problems - leaving unconfigured
E: libgcr0: dependency problems - leaving unconfigured
E: gnome-keyring: dependency problems - leaving unconfigured
E: gksu: dependency problems - leaving unconfigured
E: python-glade2: dependency problems - leaving unconfigured
E: libwebkit-1.0-2: dependency problems - leaving unconfigured
E: python-webkit: dependency problems - leaving unconfigured
E: libvte9: dependency problems - leaving unconfigured
E: python-vte: dependency problems - leaving unconfigured
E: synaptic: dependency problems - leaving unconfigured
E: software-properties-gtk: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
E: at-spi: dependency problems - leaving unconfigured
E: avidemux: dependency problems - leaving unconfigured
E: libaccess-bridge-java-jni: dependency problems - leaving unconfigured
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: libaccess-bridge-java: dependency problems - leaving unconfigured
E: azureus: dependency problems - leaving unconfigured



---

### Post by SoftTaco on 2010-07-08
wow got lucky, I tried something and it worked...mostly
(here the story for other in this situation)

Ok so I figure just reinstall the stuff right

I did all this from the terminal
First i removed the first item on the list: libpango
> sudo apt-get purge libpango1.0-0

That uninstall told that i could remove unneeded stuff with:
> sudo apt-get autoremove -f
so it did that

Then i ran:
> sudo defoma-reconfigure -f

Then I rebooted
> sudo reboot
this gave me terminal screen (i.e. no gnome)

reinstalled gdm and ubuntu-desktop
> sudo apt-get install gdm
sudo apt-get install ubuntu-desktop 


Then i just rebooted and reinstalled all the programs i wanted with synaptic 

Now i just need to fix the power and sound buttons on the pannel

---

### Post by SoftTaco on 2010-07-08
Fixed my last two issues too

Power button was just a simple matter of right click and add to panel

Sound fix is here:
[http://richs-lxh.linux-hardcore.com/2010/06/ubuntu-10-04-panel-volume-control-and-other-annoyances/]("http://richs-lxh.linux-hardcore.com/2010/06/ubuntu-10-04-panel-volume-control-and-other-annoyances/")

Lastly moved the window control buttons back to the right. (why the hell is that left by default :confused:)
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")

---

