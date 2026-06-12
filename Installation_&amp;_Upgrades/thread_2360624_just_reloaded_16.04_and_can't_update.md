---
title: "just reloaded 16.04 and can't update"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by Vic_Paine on 2017-05-06
I've tried via software update and terminal but it just hangs and nothing loads, how can this happen on a new instal and how to correct please?

---

### Post by RobGoss on 2017-05-06
Hello and welcome to the forum,  This may be a silly question but what command are you using?

Have you tried changing the download source?

If that doesn't work try running the following command

```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by litlesam on 2017-05-06
Have you tried a different mirror for the server? Noticed a few hours a go that one of them were really hanging.
Usually it's just short lived and returns to normal after a few hours.

---

### Post by Vic_Paine on 2017-05-07
Sorry only just got back, yes I tried that but not the bit after the double &.  Don't really want to upgrade I prefer using the LTS and I presume that command will update to a newer version?  Thank you for your interest.

---

### Post by #&amp;thj^% on 2017-05-07
> **Vic_Paine said:**
> Sorry only just got back, yes I tried that but not the bit after the double &.  Don't really want to upgrade I prefer using the LTS and I presume that command will update to a newer version?  Thank you for your interest.

Nope it won't upgrade to a newer version....just upgrades the LTS packages.> IE: 16.04.
sudo apt update=refreshes the package manger to pull in the new changes.

sudo apt upgrade=install the new packages for that particular version "16.04"

Hope that helps a bit.

---

### Post by Vic_Paine on 2017-05-07
Thank you for responding.  When I sudo update I get:
0% [connecting to gb.archive.ubuntu.com (2001:67c:1360:8001: :21)] [connecting t(unblinking cursor)
If I try sudo apt-get upgrade I get
vic@Ferdinand:~$ sudo apt-get upgrade
[sudo] password for vic: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
vic@Ferdinand:~$ 
No idea what the problem is I'm afraid.

---

### Post by #&amp;thj^% on 2017-05-07
You would see that if you had another package manager open Like Software-Center or Synaptic.
Close all package managers and run again.

---

### Post by Vic_Paine on 2017-05-08
Tried that but hangs on last line. UPDATE seems to be connection speed problem, walked away and left it and it did update.  Not sure why, connection speed is OK when booting win 10 on same pc.
[PHP]vic@Ferdinand:~$ sudo apt-get upgrade
[sudo] password for vic: 
Sorry, try again.
[sudo] password for vic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04
  linux-image-generic-hwe-16.04
The following packages will be upgraded:
  apparmor appmenu-qt5 appstream apt apt-transport-https apt-utils bind9-host
  desktop-file-utils distro-info-data dnsmasq-base dnsutils dpkg dpkg-dev
  eject fonts-opensymbol ghostscript ghostscript-x gir1.2-appindicator3-0.1
  gir1.2-gst-plugins-base-1.0 gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-4.0
  gir1.2-webkit2-4.0 gnome-software gnome-software-common grub-common grub-pc
  grub-pc-bin grub2-common gstreamer1.0-alsa gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-x imagemagick imagemagick-6.q16
  imagemagick-common init init-system-helpers libapparmor-perl libapparmor1
  libappindicator3-1 libappstream3 libapt-inst2.0 libapt-pkg5.0 libarchive13
  libbind9-140 libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
  libdns-export162 libdns162 libdpkg-perl libevent-2.0-5 libexiv2-14
  libfreetype6 libgail-3-0 libgd3 libgs9 libgs9-common
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libicu55 libisc-export160 libisc160 libisccc140
  libisccfg140 libjavascriptcoregtk-4.0-18 liblightdm-gobject-1-0 liblwres141
  libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra libmagickwand-6.q16-2
  libmetacity-private3a libnm-glib-vpn1 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libnm0 libnma-common libnma0 libnspr4 libnss3
  libnss3-nssdb libpam-systemd libpci3 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-style-breeze libreoffice-style-galaxy libreoffice-writer libsane
  libsane-common libsmbclient libsystemd0 libtiff5 libudev1 libwbclient0
  libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 libxml2 libxslt1.1 lightdm
  linux-libc-dev locales login makedev metacity-common multiarch-support nano
  network-manager network-manager-gnome passwd pciutils python3-pil
  python3-software-properties python3-uno python3-update-manager resolvconf
  samba-libs sane-utils snap-confine snapd sni-qt software-properties-common
  software-properties-gtk systemd systemd-sysv tcpdump thermald
  ubuntu-core-launcher ubuntu-software udev uno-libs3 update-manager
  update-manager-core update-notifier update-notifier-common ure wget
156 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
Need to get 37.9 MB/179 MB of archives.
After this operation, 11.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
75% [Connecting to gb.archive.ubuntu.com (2001:67c:1360:8001::17)]

[/PHP]

---

### Post by RobGoss on 2017-05-08
> **Vic_Paine said:**
> Sorry only just got back, yes I tried that but not the bit after the double &.  Don't really want to upgrade I prefer using the LTS and I presume that command will update to a newer version?  Thank you for your interest.

As it was pointed out the commands I posted will not change your system just update to the latest packages

At you connected to the internet?

---

### Post by Vic_Paine on 2017-05-08
> **RobGoss said:**
> As it was pointed out the commands I posted will not change your system just update to the latest packages

At you connected to the internet?
There seems to be a problem with download speed, I left it apparently hung and when I came back it had uploaded.  The PC (home built) doesn't have a problem with download speed when in Win 10 but it does seem sluggish in Ubuntu.  Is there anything I can check to try and find the bottleneck?  Yes I am connected to the Internet.

---

### Post by #&amp;thj^% on 2017-05-08
> **Vic_Paine said:**
> There seems to be a problem with download speed, I left it apparently hung and when I came back it had uploaded.  The PC (home built) doesn't have a problem with download speed when in Win 10 but it does seem sluggish in Ubuntu.  Is there anything I can check to try and find the bottleneck?  Yes I am connected to the Internet.

This happens from time to time...If it continues to be slow try switching to the Main sever as described here:
[https://askubuntu.com/questions/682532/ubuntu-repository-change](https://askubuntu.com/questions/682532/ubuntu-repository-change)

Or if you comfortable with the terminal the easy way:
This command should do the trick

```
sudo sed -i 's/http:\/\/us./http:\/\//g' /etc/apt/sources.list
```

It will remove the 'us.' prefix in each of the addresses to convert them to addresses of the main server.

Of course replace 'us' by any other mirror you are using.

---

### Post by Vic_Paine on 2017-05-08
Thanks, I'll try that if I have continuing slow download.  Often find the terminal easier and you can see what's going on.  I'm in the UK using UK server.

---

