---
title: "Gutsy Upgrade (and I) made a mess (graphics and broken packages)"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by tich on 2008-01-21
I have been running Gutsy since beta and have never experienced any problems with upgrades until yesterday.
The linux-headers have been available to upgrade for about 2 weeks now but I kept putting it off because i was worried my computer would break, and it did.

This is not entirely the fault of Gutsy/Ubuntu I certainly had a pretty big hand in it.
When I did the upgrade I had the beta Nvidia driver installed and numerous 3rd party repositories.  I understand that both of those things are things I should have changed before the upgrade.  

But now I need help to find a solution.
[B]
Here is what I know:[/B]
I am running Gutsy on a Thinkpad t61 with the Nvidia Quadro NVS 140M 128MB graphics card.
I was using the beta Nvidia driver available from the Nvidia website.

**I have many 3rd party repositories:**
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb [http://www.nighton.net/](http://www.nighton.net/) feisty main
deb-src [http://www.nighton.net/](http://www.nighton.net/) feisty main
deb [http://www.iola.dk/nemo/repo](http://www.iola.dk/nemo/repo) binary/
deb [http://download.gna.org/gcfilms/ubuntu](http://download.gna.org/gcfilms/ubuntu) ./
deb-src [http://download.gna.org/gcfilms/ubuntu](http://download.gna.org/gcfilms/ubuntu) ./ 
[B]
Here is how the scene went down.[/B]
I finally decided to upgrade using the update-manager.
After it started I realized that I didn't disable the Nvidia driver first, but it was too late.
I restarted the computer using the .14 kernel, the computer booted fine, including the Nvidia driver (the nvidia splash worked fine), up to the login screen. but after the login screen the monitor went to black, flashed some text, went black again and returned me to the login screen.  And this is a never ending loop.

If I boot up the computer using the .12 kernel it goes to the broken graphics manager thing (I am not sure what it is called). I have tried unsuccessfully to choose the appropriate video card but I can load Vesa and run Ubuntu with an 800x600 monitor.
(which is where I am typing this from)

When I first rebooted into the .12 I removed anything that had to do with Nvidia with the expectation of reinstalling (first from the restricted-driver-manager or envy and later the beta driver again from the website) but the .12 doesn't have the  linux-restricted-modules-2.6.22-12-generic installed (maybe removed with the Nvidia stuff) and won't let me run the restricted-driver-manager
I am also unable to reinstall the  linux-restricted-modules-2.6.22-12-generic
Instead I get this warning:  
"Package linux-restricted-modules-2.6.22-12-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"
My next attempt was to run Envy but I am unable to install build-essential
I get this warning:
build-essential:
 Depends: libc6-dev but it is not going to be installed or libc-dev
 Depends: g++ but it is not going to be installed
I would need older versions of these that seem to be no longer available. (Aptitude tells me to insert the Gutsy alpha3 cd to get the appropriate versions of this stuff.)

I have tried using 'fix broken packages' in Synaptic.
I have tried 'apt-get -f install' and 'dpkg --configure -a' to fix my broken packages but nothing seems to work.

**So how can I **
1.  fix the broken packages?
2.  get nvidia back?

Any help will be greatly appreciated.
And, obviously, if you need some info that I neglected to include please ask, I will be more than happy to supply it!

**Oh yeah and just in case, here is the list of upgrades that broke the system:**
avahi-autoipd (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
avahi-daemon (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
bind9-host (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
cupsys (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
cupsys-bsd (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
cupsys-client (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
cupsys-common (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
dnsutils (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
esound-common (0.2.38-0ubuntu4) to 0.2.38-0ubuntu4.1
evolution-data-server (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
evolution-data-server-common (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
gdm (2.20.1-0ubuntu1) to 2.20.1-0ubuntu2
ghostscript (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
ghostscript-x (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
libavahi-client3 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-common-data (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-common3 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-compat-howl0 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-compat-libdnssd1 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-core5 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libavahi-glib1 (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
libbind9-30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libboost-date-time1.34.1 (1.34.1-2ubuntu1) to 1.34.1-2ubuntu1.1
libboost-filesystem1.34.1 (1.34.1-2ubuntu1) to 1.34.1-2ubuntu1.1
libboost-regex1.34.1 (1.34.1-2ubuntu1) to 1.34.1-2ubuntu1.1
libboost-thread1.34.1 (1.34.1-2ubuntu1) to 1.34.1-2ubuntu1.1
libcamel1.2-10 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libcupsimage2 (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
libcupsys2 (1.3.2-1ubuntu7.2) to 1.3.2-1ubuntu7.5
libdns32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libebook1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libecal1.2-7 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedata-book1.2-2 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedata-cal1.2-6 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedataserver1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedataserverui1.2-8 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libegroupwise1.2-13 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libesd-alsa0 (0.2.38-0ubuntu4) to 0.2.38-0ubuntu4.1
libexchange-storage1.2-3 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libgs8 (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
libisc32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libisccc30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libisccfg30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
liblwres30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libpq5 (8.2.5-1.1) to 8.2.6-0ubuntu0.7.10.1
libpt-1.10.0 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-alsa (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l2 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libsnmp-base (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
libsnmp10 (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
libxfont1 (1:1.3.0-0ubuntu1) to 1:1.3.0-0ubuntu1.1
libxml2 (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1
libxml2-utils (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1
linux-headers-2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47
linux-headers-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-image-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
network-manager-gnome (0.6.5-0ubuntu10) to 0.6.5-0ubuntu11~7.10.0
openssh-client (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
python-avahi (0.6.20-2ubuntu3.1) to 0.6.20-2ubuntu3.2
python-libxml2 (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1
ssh-askpass-gnome (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
update-manager (1:0.81.1) to 1:0.81.2
update-manager-core (1:0.81.1) to 1:0.81.2
xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8) to 2:1.3.0.0.dfsg-12ubuntu8.3
xserver-xorg-dev (2:1.3.0.0.dfsg-12ubuntu8) to 2:1.3.0.0.dfsg-12ubuntu8.3
xserver-xorg-video-intel (2:2.1.1-0ubuntu9) to 2:2.1.1-0ubuntu9.1

---

### Post by tich on 2008-01-22
i would be really happy, as a first step, to just get build-essential to install.
any help with that would be awesome!

---

### Post by Partyboi2 on 2008-01-23
>  My next attempt was to run Envy but I am unable to install build-essential
I didn't think you needed build-essential to install envy, envy is a deb package that you just need to download from [here]("http://albertomilone.com/nvidia_scripts1.html") and double click to install.
If you are needing to install build-essential for some other reason it is on the cd, so put the ubuntu cd and open up synaptic and seach for build-essential.
can you post your source.list
```
cat etc/apt/sources.list
```

---

