---
title: "System Settings"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by aakshayy on 2012-09-14
Hello.. This is my first post on ubuntu forums. I recently installed ubuntu on my Dell InspironN5010 laptop. After successfully installing it i was told to update and upgrade using the apt-get commands. Because of an unstable internet connection i think some parts of packages were not successfully installed. When i tried re-running the command, it showed
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot apt apt-transport-https apt-utils aptdaemon banshee banshee-extension-soundmenu bind9-host c2esp compiz compiz-core compiz-gnome
  compiz-plugins-default compiz-plugins-main-default cups cups-driver-gutenprint dconf-gsettings-backend dnsmasq-base dnsutils espeak espeak-data
  exiv2 foo2zjs foomatic-db-compressed-ppds fuse-utils ginn gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gnome-control-center
  gnome-control-center-data gnome-disk-utility gnome-keyring gnome-orca gnome-settings-daemon gnome-sudoku gnome-terminal gnome-terminal-data gnomine
  gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service hpijs hplip hplip-cups hplip-data indicator-session libappindicator1 libatk-adaptor
  libcap2-bin libcompizconfig0 libdecoration0 libenchant1c2a libespeak1 libfuse2 libgck-1-0 libgcr-3-1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgrip0 libgwibber-gtk2 libhpmud0 libidl0 libindicate5 libjpeg8 libldap-2.4-2 liblockfile1 libnice10 libnm-gtk0 liboauth0 libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-writer libsane libsane-hpaio libsdl1.2debian libtotem-plparser17 libtotem0 libunity-2d-private0 libv4l-0 libvte-2.90-9
  libvte-common libvte9 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libxfixes3 libyelp0 linux-generic linux-headers-generic linux-image-generic min12xxw
  network-manager network-manager-gnome ntfs-3g pnm2ppa ptouch-driver pulseaudio-utils pxljr python-appindicator python-apt python-aptdaemon
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-dbus python-gobject python-indicate python-uno python-vte
  rastertosag-gdi rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins seahorse
  sessioninstaller shotwell software-center splix tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk
  ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation ttf-opensymbol ttf-takao-pgothic ttf-thai-tlwg ttf-unfonts-core ubuntu-desktop ubuntu-minimal
  ubuntu-wallpapers udisks unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-common unity-services update-manager
  update-manager-core usb-creator-common usb-creator-gtk vino wireless-crda wpasupplicant xdiagnose xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xz-utils yelp zeitgeist zeitgeist-core
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.



```
Also i installed another distro gnome 3. And now when i click on the System settings application it does not open neither does it give any error.
What is wrong? Plz help.. Any help would be appreciated. Thanks

---

### Post by jerrrys on 2012-09-14
Hi aakshayy, welcome to the forums :)

Did you do a successful sudo apt-get update first?

---

