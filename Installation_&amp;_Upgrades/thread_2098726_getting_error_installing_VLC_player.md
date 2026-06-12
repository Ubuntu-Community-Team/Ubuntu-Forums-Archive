---
title: "getting error installing VLC player"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by howhy on 2012-12-27
So yesterday I successfully got Ubuntu runing after some GRUB problems ..

how ever I am getting an error while installing VLC player, since I am new to Linux world, I am not able to figure how to fix it...

when I try to install VLC i get errror saying required dependencies 

```
liba52-0.7.4 libaacs0 libass4 libbluray1 libcddb2 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9 libdvbpsi7 libdvdnav4 libdvdread4 libebml3 libenca0 libfaad2 libgsm1 libiso9660-8 libkate1 libmad0 libmatroska5 libmodplug1 libmpcdec6 libmpeg2-4 libresid-builder0c2a libschroedinger-1.0-0 libsdl-image1.2 libsidplay2 libtar0 libts-0.0-0 libtwolame0 libupnp3 libva-x11-1 libva1 libvcdinfo0 libvpx1 libx264-120 libxcb-keysyms1 libzvbi-common libzvbi0 tsconf 
```I click on repair still after repair installing vlc i get the same error again and again...

---

### Post by Laiquendi on 2012-12-27
Clearly you have some unmet dependencies which your Linux is unable to solve by itself. Do you have proper software sources enabled? (check it under "software sources").

---

### Post by howhy on 2012-12-27
> **Laiquendi said:**
> Clearly you have some unmet dependencies which your Linux is unable to solve by itself. Do you have proper software sources enabled? (check it under "software sources").
under software sources how do I know what are the proper sources , I have unchecked CDROM because it have taken the cd out from the drive...

---

### Post by howhy on 2012-12-27
so I tested for best download server and autometic update and now i can neither getting GNOME from Software center nor getting vlc
howw ever vlc message has changed 
The following packages have unmet dependencies:

> vlc: Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but 2.0.3-0ubuntu0.12.04.1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
     Depends: libva1 (> 1.0.15~) but it is not going to be installed
     Depends: libxcb-composite0 but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed
     Depends: libxcb-randr0 (>= 1.1) but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

---

### Post by iMac71 on 2012-12-27
You might try this way:
1) open a Terminal window and type:
```
sudo apt-add-repository -y ppa:videolan/stable-daily
sudo apt-get update -y
sudo apt-get upgrade -y
```(you've to press [ENTER} after each line).
2) launch the Ubuntu Software Center and type "vlc" without quotes in the search field;
3) when the product's page is loaded, click on "Install" button and type your password.
This should solve your problem.

---

### Post by pardalet on 2012-12-27
Maybe the following command will help you with the broken dependencies:

```
$ sudo apt-get -f install vlc
```


If not, the other obvious answer is: have you tried manually installing all the dependencies?

```
$ sudo apt-get install liba52-0.7.4 libaacs0 libass4 libbluray1 libcddb2 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9 libdvbpsi7 libdvdnav4 libdvdread4 libebml3 libenca0 libfaad2 libgsm1 libiso9660-8 libkate1 libmad0 libmatroska5 libmodplug1 libmpcdec6 libmpeg2-4 libresid-builder0c2a libschroedinger-1.0-0 libsdl-image1.2 libsidplay2 libtar0 libts-0.0-0 libtwolame0 libupnp3 libva-x11-1 libva1 libvcdinfo0 libvpx1 libx264-120 libxcb-keysyms1 libzvbi-common libzvbi0 tsconf
```

---

### Post by howhy on 2012-12-28
thanks

---

