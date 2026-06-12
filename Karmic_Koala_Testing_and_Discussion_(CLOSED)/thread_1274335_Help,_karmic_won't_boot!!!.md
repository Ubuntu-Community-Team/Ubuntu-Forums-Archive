---
title: "Help, karmic won't boot!!!"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by steigerjb on 2009-09-24
I upgraded to Karmic Koala yesterday using ```
update-manager -d
```

I upgraded pretty smoothly i guess. Restarted the computer and came back. It said I had more updates to install so I did. Rebooted again, but now the desktop won't load up good. It goes to like as far as attached pic. If i click on the top left where the menu is supposed to be, it starts to show up but not fully. I am sorry, I really don't know how to describe it.

I am pretty much doomed aren't I? I have no recovery mode in my grub list, just karmic and vista :(

WHY DID I UPGRADE TO KARMIC KOALA NOW?? WHY DIDN'T I JUST WAIT?? ](*,) :cry:

---

### Post by unmole on 2009-09-24
considering that the desktop shows up, you are not doomed. hit Alt+Crt+bacspace to kill X org. and then try downgrading from the CLI.

---

### Post by steigerjb on 2009-09-24
> **unmole said:**
> considering that the desktop shows up, you are not doomed. hit Alt+Crtl+backspace to kill X org. and then try downgrading from the CLI.

the desktop doesn't really show. just what is seen in that pic. nothing functions though.

crtl alt backspace does nothing. downgrade from CLI??? huh? how? I didn't think downgrading was possible.

---

### Post by unmole on 2009-09-24
It is possible to downgrade but it NOT recomended. I say just whip out your 9.04 live CD make  backup your files and re-install. How ever if your willing to risk screwing your computer even further here you go _[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)_

---

### Post by LewRockwell on 2009-09-24
boot up using a LiveCD *nix distro, mount the ubuntu partition, and go to your /boot directory to see which kernels you can boot up

then you can edit your /boot/grub/menu.lst file to allow you to boot whichever kernel you want

.

---

### Post by kansasnoob on 2009-09-24
> **LewRockwell said:**
> boot up using a LiveCD *nix distro, mount the ubuntu partition, and go to your /boot directory to see which kernels you can boot up

then you can edit your /boot/grub/menu.lst file to allow you to boot whichever kernel you want

.

+1! I've been able to rescue my Karmic a number of times by using chroot. First you must know what partition Karmic / is on. I just know where mine is but you should be able to figure it out by looking at Gparted (aka: Partition Editor) or possibly running the command:

```
sudo fdisk -l
```

Mine is on sda3 so I'd run each of the following commands to mount (substitute your / partition# for sda3):

```
sudo mount /dev/sda3 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

Then:

```
sudo chroot /mnt
```

From there you can now do a lot of things. You may want to edit that menu.lst (if it's legacy grub) by uncommenting recovery mode options and older kernels (**Note: no sudo required because you're already root**):

```
gedit /boot/grub/menu.lst
```

Mostly very common things like:

```
apt-get update
```

```
apt-get upgrade
``` (or dist-upgrade)

```
apt-get -f install
```

```
dpkg --configure -a
```

etc, etc..........

When you're done just run the following commands:

```
exit
```

```
sudo umount /mnt/dev

```
```
sudo umount /mnt/proc
```

```
sudo umount /mnt

```
```
sudo reboot
```

---

### Post by steigerjb on 2009-09-24
> **kansasnoob said:**
> +1! I've been able to rescue my Karmic a number of times by using chroot. First you must know what partition Karmic / is on. I just know where mine is but you should be able to figure it out by looking at Gparted (aka: Partition Editor) or possibly running the command:

```
sudo fdisk -l
```

Mine is on sda3 so I'd run each of the following commands to mount (substitute your / partition# for sda3):

```
sudo mount /dev/sda3 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

Then:

```
sudo chroot /mnt
```

From there you can now do a lot of things. You may want to edit that menu.lst (if it's legacy grub) by uncommenting recovery mode options and older kernels (**Note: no sudo required because you're already root**):

```
gedit /boot/grub/menu.lst
```

Mostly very common things like:

```
apt-get update
```

```
apt-get upgrade
``` (or dist-upgrade)

```
apt-get -f install
```

```
dpkg --configure -a
```

etc, etc..........

When you're done just run the following commands:

```
exit
```

```
sudo umount /mnt/dev

```
```
sudo umount /mnt/proc
```

```
sudo umount /mnt

```
```
sudo reboot
```

i am sda5. do i do that stuff from live cd?

---

### Post by steigerjb on 2009-09-24
i tried loading other kernel...desktop seemed to load fully but mouse doesn't move :(

---

### Post by steigerjb on 2009-09-24
```
apt-get update
```

root@ubuntu:/# apt-get update
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic Release.gpg                            
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic/main Translation-en_US                 
  Could not resolve 'mirrors.us.kernel.org'
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
  Could not resolve 'archive.canonical.com'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic/restricted Translation-en_US           
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic/universe Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic/multiverse Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-updates Release.gpg
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-updates/main Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-updates/restricted Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-updates/universe Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-updates/multiverse Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Could not resolve 'dl.google.com'
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
  Could not resolve 'dl.google.com'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-security Release.gpg
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-security/main Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-security/restricted Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-security/universe Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) karmic-security/multiverse Translation-en_US
  Could not resolve 'mirrors.us.kernel.org'
Reading package lists... Done
W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic/Release.gpg](http://mirrors.us.kernel.org/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/Release.gpg](http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/Release.gpg](http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://mirrors.us.kernel.org/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirrors.us.kernel.org'

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not resolve 'dl.google.com'

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Could not resolve 'dl.google.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@ubuntu:/#

---

### Post by zika on 2009-09-24
It looks like You do not have DNS sorted well. try ```
sudo dhclient eth0
```(substituting eth0 with whatever device You use) in CLI before *sudo apt-get update*... That worked for lot of us in the time of trouble last week or so ...

---

### Post by steigerjb on 2009-09-24
> **zika said:**
> It looks like You do not have DNS sorted well. try ```
sudo dhclient eth0
```(substituting eth0 with whatever device You use) in CLI before *sudo apt-get update*... That worked for lot of us in the time of trouble last week or so ...

what do you mean whatever device I use? beats me.

---

### Post by steigerjb on 2009-09-24
```
root@ubuntu:/# sudo dhclient eth0
sudo: unable to resolve host ubuntu
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:19:b9:52:b3:1e
Sending on   LPF/eth0/00:19:b9:52:b3:1e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by kansasnoob on 2009-09-24
My guess is that you're not getting an internet connection. Sadly (gladly for me) I've not encountered that, so not much help there.

Possibly if you're using wireless change to a wired connection for now:confused:

I'm sure there must be a way, basically the equivalent of choosing to run a shell w/networking from the selections at the end of recovery mode, I just don't know how:confused:

---

### Post by steigerjb on 2009-09-24
> **kansasnoob said:**
> My guess is that you're not getting an internet connection. Sadly (gladly for me) I've not encountered that, so not much help there.

Possibly if you're using wireless change to a wired connection for now:confused:

I'm sure there must be a way, basically the equivalent of choosing to run a shell w/networking from the selections at the end of recovery mode, I just don't know how:confused:

i don't have a cord

---

### Post by kansasnoob on 2009-09-24
Just a thought. Try running both 'apt-get -f install' and 'dpkg --configure -a' which will both depend only on existing packages.

---

### Post by steigerjb on 2009-09-24
> **kansasnoob said:**
> Just a thought. Try running both 'apt-get -f install' and 'dpkg --configure -a' which will both depend only on existing packages.

```
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev menu-xdg libglib1.2ldbl desktop-base planner
  libboost-regex1.34.1 libgsf-gnome-1-114 gthumb libavutil-unstripped-49
  libtheora-bin gnome-games-extra-data python-renderpm qjackctl libdevil-dev
  libgtk1.2 libgda3-common python-gnome2-extras libdiscid0 warzone2100-music
  cheese mplayer-skins libots0 gnome-network-admin hardinfo g++-4.3
  gthumb-data check ttf-kannada-fonts gnome-office paprefs
  libaiksaurusgtk-1.2-0c2a liblualib50-dev abiword-common libwebkit-1.0-1
  abiword abiword-plugin-mathview latex-xft-fonts libaiksaurus-1.2-0c2a
  gnome-themes openoffice.org-writer2latex liblualib50 libboost-thread1.34.1
  python-lxml libass1 swfdec-gnome python-reportlab-accel gnumeric-common
  libsoup2.2-8 gnumeric-doc libpostproc-unstripped-51 libdvbpsi4
  libsox-fmt-ffmpeg libggi-target-x dasher link-grammar-dictionaries-en p7zip
  libx264-65 gnome-themes-extras libgoffice-0-6-common liblua50-dev gdm-themes
  abiword-help arj lua50 gnome-volume-manager libboost-signals1.34.1
  libavformat-unstripped-52 libt1-5 libggi2 libaiksaurus-1.2-data libwv-1.2-3
  ogmtools python-4suite-doc dasher-data gnome-backgrounds libsox-fmt-all
  libgii1 gok libgdome2-0 ttf-telugu-fonts gnome-spell libglc0
  abiword-plugin-grammar libavfilter-unstripped-0 libboost-iostreams1.34.1
  libwmf-bin libgtk2-gladexml-perl libffado0 libtiff4-dev libgdk-pixbuf2
  libgii1-target-x libswfdec-0.8-0 libsox-fmt-mp3 libgoffice-0-6 libphonon4
  python-uniconvertor dirac libgtk1.2-common imagemagick-doc libtiffxx0c2
  pulseaudio-module-zeroconf liferea libgdome2-cpp-smart0c2a padevchooser
  libkadm55 swfdec-mozilla gnome-core paman gnome-netstatus-applet
  python-4suite-xml libswscale-unstripped-0 libgda3-bin ttf-oriya-fonts
  gnumeric libgda3-3 mjpegtools libcegui-mk2-dev libboost-filesystem1.34.1
  liblink-grammar4 libgtkmathview0c2a libgconfmm-2.6-1c2
  libboost-filesystem1.37.0 gnome-accessibility liblua50 jackd
  ttf-bengali-fonts libavdevice-unstripped-52 perlmagick libvlccore0 pavumeter
  lame inkscape nvidia-180-kernel-source python-reportlab
  libboost-system1.37.0 warzone2100-data serpentine sound-juicer simgear1.0.0
  qt4-qtconfig libmusicbrainz3-6 nvidia-180-libvdpau gnome-vfs-obexftp
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# dpkg --configure -a
root@ubuntu:/# 

```

---

### Post by zika on 2009-09-24
You have wireless connection. Give us the output of **ifconfig** in CLI. I do not have much experience with wireless, I'm cable guy but something might be done.

---

### Post by steigerjb on 2009-09-24
> **zika said:**
> You have wireless connection. Give us the output of **ifconfig** in CLI. I do not have much experience with wireless, I'm cable guy but something might be done.

```
root@ubuntu:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:52:b3:1e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:b9:52:b3:1e  
          inet addr:169.254.6.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7b:eb:2c  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe7b:eb2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9277066 (9.2 MB)  TX bytes:1494609 (1.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-7B-EB-2C-37-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/# 

```

---

### Post by cariboo on 2009-09-24
Try:

```
sudo dhclient wlan0
```

---

### Post by steigerjb on 2009-09-24
```
root@ubuntu:/# sudo dhclient wlan0
sudo: unable to resolve host ubuntu
There is already a pid file /var/run/dhclient.pid with pid 15768
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:d2:7b:eb:2c
Sending on   LPF/wlan0/00:19:d2:7b:eb:2c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.24 from 192.168.1.1
DHCPREQUEST of 192.168.1.24 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.24 from 192.168.1.1
bound to 192.168.1.24 -- renewal in 37904 seconds.
root@ubuntu:/# 

```

---

### Post by steigerjb on 2009-09-24
I just got all my videos off the Ubuntu partition, there are safe now

---

### Post by steigerjb on 2009-09-24
i don't think doing sudo apt-get update will do anything anyway. there are no more updates

---

### Post by steigerjb on 2009-09-24
the real question is...why is my mouse frozen if I try old kernels? Cuz it seems to work with old kernals, just I can't do anything w/o the mouse.

---

### Post by kansasnoob on 2009-09-24
> **steigerjb said:**
> the real question is...why is my mouse frozen if I try old kernels? Cuz it seems to work with old kernals, just I can't do anything w/o the mouse.

Is it a USB mouse? If so do you have a PS2 mouse you could use temporarily? **Note: Very bad idea to plug in a ps2 mouse without powering down completely!**

I was actually just rereading everything. That long list of stuff to remove scares me sort of. Some may be replaced with newer packages but I'd bet some was manually installed on Jaunty and would have to be reinstalled later on.

How is / on free space?

---

### Post by steigerjb on 2009-09-24
> **kansasnoob said:**
> Is it a USB mouse? If so do you have a PS2 mouse you could use temporarily? **Note: Very bad idea to plug in a ps2 mouse without powering down completely!**

I was actually just rereading everything. That long list of stuff to remove scares me sort of. Some may be replaced with newer packages but I'd bet some was manually installed on Jaunty and would have to be reinstalled later on.

How is / on free space?

laptop

---

### Post by kansasnoob on 2009-09-24
OK. Have you tried booting the recovery mode for an older kernel?

Maybe we can work from there with networking.

Is disc/partition free space OK?

---

### Post by kansasnoob on 2009-09-24
BTW there were some problems this AM with the network applet, and some carried over to actual connectivity:

[http://ubuntuforums.org/showthread.php?t=1274185](http://ubuntuforums.org/showthread.php?t=1274185)

A fix is now out in the US archives:

[https://launchpad.net/ubuntu/+source/network-manager-applet/0.8~a~git.20090923t220421.1ac8ffd-0ubuntu3/+changelog](https://launchpad.net/ubuntu/+source/network-manager-applet/0.8~a~git.20090923t220421.1ac8ffd-0ubuntu3/+changelog)

Such is the way an Alpha goes:)

---

### Post by steigerjb on 2009-09-24
i deleted the Karmic partition and reinstalled Jaunty

---

### Post by tjeremiah on 2009-09-24
> **kansasnoob said:**
> +1! I've been able to rescue my Karmic a number of times by using chroot. First you must know what partition Karmic / is on. I just know where mine is but you should be able to figure it out by looking at Gparted (aka: Partition Editor) or possibly running the command:

```
sudo fdisk -l
```

Mine is on sda3 so I'd run each of the following commands to mount (substitute your / partition# for sda3):

```
sudo mount /dev/sda3 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

Then:

```
sudo chroot /mnt
```

From there you can now do a lot of things. You may want to edit that menu.lst (if it's legacy grub) by uncommenting recovery mode options and older kernels (**Note: no sudo required because you're already root**):

```
gedit /boot/grub/menu.lst
```

Mostly very common things like:

```
apt-get update
```

```
apt-get upgrade
``` (or dist-upgrade)

```
apt-get -f install
```

```
dpkg --configure -a
```

etc, etc..........

When you're done just run the following commands:

```
exit
```

```
sudo umount /mnt/dev

```
```
sudo umount /mnt/proc
```

```
sudo umount /mnt

```
```
sudo reboot
```
ok, i finally was able to do what you said, but past mounting the drive, nothing happens. Then I get to chroot and it doesnt allow me to continue.

---

