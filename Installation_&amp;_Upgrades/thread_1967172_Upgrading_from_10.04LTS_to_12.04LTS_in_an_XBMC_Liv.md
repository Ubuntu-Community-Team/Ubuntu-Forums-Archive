---
title: "Upgrading from 10.04LTS to 12.04LTS in an XBMC Live install"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by blm14 on 2012-04-27
the sudo do-release-upgrade -d more or less went without a hitch. Except I reboot and now I see this:

```

xbmc@XBMCLive:/etc/grub.d$ uname -a
Linux XBMCLive 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 i686 i386 GNU/Linux

```

Eeek! I try to do an upgrade:

```


xbmc@XBMCLive:/etc/grub.d$ uname -a
Linux XBMCLive 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 i686 i386 GNU/Linux
xbmc@XBMCLive:/etc/grub.d$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  apt apt-utils avahi-daemon bind9-host bison debhelper dhcp3-client dhcp3-common esound-common fglrx
  fp-compiler fp-units-rtl gawk gettext libaudiofile-dev libavcodec-dev libavfilter-dev libavformat-dev
  libavutil-dev libboost-dev libboost-thread-dev libcdio-dev libesd0 libesd0-dev libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libiso9660-dev liblockfile1 libmikmod2 libmikmod2-dev libmodplug-dev libmpcdec-dev
  libmysqlclient-dev libpostproc-dev libqtcore4 libqtgui4 libschroedinger-1.0-0 libsoap-lite-perl libswscale-dev
  libxmltv-perl linux-generic linux-image-generic lirc lsb-release man-db ntpdate nvidia-settings python
  python-apt python-dev python-gnupginterface python-minimal python-qt3 python-sip python-software-properties
  python-sqlite python-xkit screen-resolution-extra ttf-liberation ubuntu-minimal udisks update-manager-core
  upower usbutils whois wireless-crda wpasupplicant x11-utils xbmc xbmc-bin xbmc-data xbmc-live
  xbmc-skin-confluence xbmc-standalone xmltv xmltv-gui xmltv-util xterm
0 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic
cp: cannot stat `/lib/libacl*': No such file or directory
E: /usr/share/initramfs-tools/hooks/live failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.32-29-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
xbmc@XBMCLive:/etc/grub.d$

```

double eek! Ok, so how can I make this machine use the proper kernel? It looks like the newest kernel did not even download:

```
xbmc@XBMCLive:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
done

```

Halp!

---

