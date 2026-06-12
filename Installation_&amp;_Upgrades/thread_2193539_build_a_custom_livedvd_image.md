---
title: "build a custom livedvd image"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by fabritrento on 2013-12-13
I followed [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) to build a custom dvd image (from xubuntu 13.10 i386 livecd)

The problem is that if i boot the new livecd, the boot hangs after bonjour/cups service is started, wothout errors. How i can increase the boot logging?

Someone can help me fix this problem?

thankyou very much

the things i've done in chroot is:


sudo sh -c 'echo "deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main" >> /etc/apt/sources.list.d/
google-talkplugin.list'
wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-talkplugin

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update
sudo apt-get install skype

sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra-cv

apt-get install vim mc firefox chromium-browser flashplugin-installer libreoffice ardesia vlc mplayer gnome-mplayer xine-ui musescore spotlighter cellwriter florence cheese gtk-recordmydesktop python-whiteboard xournal nautilus nautilus-dropbox audacity celestia-gnome collatinus curtain dasher dia easystroke fotowall freeplane gbrainy gcompris gelemental geogebra-gnome guayadeque guvcview imagination inkscape edubuntu-desktop edubuntu-artwork edubuntu-wallpapers ubuntu-edu-preschool ubuntu-edu-primary ubuntu-edu-secondary ubuntu-edu-tertiary virtualbox

dpkg -i jitsi-stable.deb
dpkg -i Open-Sankore-2.2.3_i386.deb

sudo /usr/share/doc/libdvdread4/install-css.sh



i tryed to leave 8.8.8.8 in resolv.conf and also delete resolv.conf.

nothing changes the cd won't boot. i don't understand when i do a mistake.

i need it in the school, please help me.

---

### Post by Bucky Ball on 2013-12-13
Are you booting this on the same machine you created it on? Also this:

> The architecture (Amd64 or i386) to be stored on the LiveCD should be the same as the architecture used to perform the customization, or the LiveCD may not run. It is not trivial to customize an AMD64 LiveCD using an i386 operating system, for example. 

You're building a 32bit image probably on a 64bit machine. That probably won't work according to the quote from your link above.

---

### Post by fabritrento on 2013-12-13
yes, same arch, i386

---

### Post by fabritrento on 2013-12-16
i solved following this different howto: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by Bucky Ball on 2013-12-17
Nice one. I am going to follow that guide and see how I go myself. 

Please mark thread as solved using instructions in my signature. Thanks. ;)

---

