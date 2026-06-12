---
title: "HAL removal."
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ccw on 2010-01-15
Lucid Aplha 2 release notes:
> Hal removal

Lucid Alpha 2 sports full removal of the hal package, making Ubuntu faster to boot and faster to resume from suspend.

```
$ apt-show-versions | grep hal
hal/lucid uptodate 0.5.14-0ubuntu2
hal-info/lucid uptodate 20091130-1
libhal-storage1/lucid uptodate 0.5.14-0ubuntu2
libhal1/lucid uptodate 0.5.14-0ubuntu2
$ sudo apt-get purge hal hal-info libhal-storage1 libhal1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsilcclient-1.1-3 erlang-crypto telepathy-gabble python-avahi erlang-xmerl
  python-couchdb python-pygoocanvas erlang-syntax-tools python-louis
  liblouis-data python-virtinst empathy-common python-speechd libsctp1
  libgupnp-1.0-2 libgoocanvas3 libindicate-gtk1 lksctp-tools libdotconf1.0
  python-urlgrabber libcouchdb-glib-1.0-1 telepathy-salut couchdb-bin
  erlang-runtime-tools gstreamer0.10-gnonlin python-gtk-vnc libgdata-common
  python-desktopcouch telepathy-butterfly libcurl3 libgoocanvas-common
  liblouis0 libavahi-ui0 speech-dispatcher erlang-mnesia python-telepathy
  libart2.0-cil erlang-public-key libspeechd2 libgconf2.0-cil
  python-desktopcouch-records libflickrnet2.2-cil libgdata6 desktopcouch
  erlang-inets libgupnp-igd-1.0-2 usb-creator-common media-player-info
  python-papyon libzephyr4 erlang-ssl libnice0 gstreamer0.10-nice
  libgmime2.2a-cil libloudmouth1-0 libjson-glib-1.0-0 python-crypto
  libgssdp-1.0-1 libgssdp-1.0-2 telepathy-mission-control-5 erlang-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  contact-lookup-applet* deskbar-applet* empathy* evolution*
  evolution-couchdb* evolution-exchange* evolution-indicator*
  evolution-plugins* f-spot* firefox-3.5-gnome-support* firefox-gnome-support*
  galeon* gbrainy* gdm* gdm-guest-session* gimp* gnome-about* gnome-applets*
  gnome-mag* gnome-media* gnome-mount* gnome-netstatus-applet* gnome-orca*
  gnome-panel* gnome-pilot* gnome-pilot-conduits* gnome-power-manager*
  gnome-session* gnome-spell* gnome-system-tools* gnome-utils*
  gstreamer0.10-plugins-good* hal* hal-info* hamster-applet* indicator-applet*
  indicator-applet-session* indicator-me* indicator-messages*
  indicator-session* libbonoboui2-0* libdeskbar-tracker* libgail-gnome-module*
  libgnome-pilot2* libgnome-vfs2.0-cil* libgnome2-0* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.24-cil* libgnomepanel2.24-cil* libgnomeui-0*
  libgnomevfs2-0* libgnomevfs2-bin* libgnomevfs2-extra* libgstfarsight0.10-0*
  libhal-storage1* libhal1* liblpint-bonobo0* libnautilus-burn4* liboobs-1-4*
  libpanel-applet2-0* libpurple0* libtelepathy-farsight0* libvirt-bin*
  mousetweaks* nautilus-share* pidgin* pidgin-otr* pitivi* policykit-gnome*
  python-gnome2* python-gnome2-desktop* python-gnomeapplet*
  python-nautilusburn* python-pyatspi* rhythmbox* seahorse-plugins*
  system-config-printer-gnome* telepathy-haze* tomboy* totem* totem-gstreamer*
  totem-mozilla* totem-plugins* tracker* tracker-search-tool* tracker-utils*
  ubuntu-desktop* ubuntu-virt-mgmt* ubuntu-virt-server* usb-creator*
  usb-creator-gtk* vinagre* virt-manager* xulrunner-1.9.1-gnome-support*
0 upgraded, 0 newly installed, 95 to remove and 0 not upgraded.
After this operation, 205MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Really? Looks like there's A LOT of dependencies to be addressed.

---

### Post by xebian on 2010-01-15
> **ccw said:**
> Lucid Aplha 2 release notes:


```
$ apt-show-versions | grep hal
hal/lucid uptodate 0.5.14-0ubuntu2
hal-info/lucid uptodate 20091130-1
libhal-storage1/lucid uptodate 0.5.14-0ubuntu2
libhal1/lucid uptodate 0.5.14-0ubuntu2
$ sudo apt-get purge hal hal-info libhal-storage1 libhal1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsilcclient-1.1-3 erlang-crypto telepathy-gabble python-avahi erlang-xmerl
  python-couchdb python-pygoocanvas erlang-syntax-tools python-louis
  liblouis-data python-virtinst empathy-common python-speechd libsctp1
  libgupnp-1.0-2 libgoocanvas3 libindicate-gtk1 lksctp-tools libdotconf1.0
  python-urlgrabber libcouchdb-glib-1.0-1 telepathy-salut couchdb-bin
  erlang-runtime-tools gstreamer0.10-gnonlin python-gtk-vnc libgdata-common
  python-desktopcouch telepathy-butterfly libcurl3 libgoocanvas-common
  liblouis0 libavahi-ui0 speech-dispatcher erlang-mnesia python-telepathy
  libart2.0-cil erlang-public-key libspeechd2 libgconf2.0-cil
  python-desktopcouch-records libflickrnet2.2-cil libgdata6 desktopcouch
  erlang-inets libgupnp-igd-1.0-2 usb-creator-common media-player-info
  python-papyon libzephyr4 erlang-ssl libnice0 gstreamer0.10-nice
  libgmime2.2a-cil libloudmouth1-0 libjson-glib-1.0-0 python-crypto
  libgssdp-1.0-1 libgssdp-1.0-2 telepathy-mission-control-5 erlang-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  contact-lookup-applet* deskbar-applet* empathy* evolution*
  evolution-couchdb* evolution-exchange* evolution-indicator*
  evolution-plugins* f-spot* firefox-3.5-gnome-support* firefox-gnome-support*
  galeon* gbrainy* gdm* gdm-guest-session* gimp* gnome-about* gnome-applets*
  gnome-mag* gnome-media* gnome-mount* gnome-netstatus-applet* gnome-orca*
  gnome-panel* gnome-pilot* gnome-pilot-conduits* gnome-power-manager*
  gnome-session* gnome-spell* gnome-system-tools* gnome-utils*
  gstreamer0.10-plugins-good* hal* hal-info* hamster-applet* indicator-applet*
  indicator-applet-session* indicator-me* indicator-messages*
  indicator-session* libbonoboui2-0* libdeskbar-tracker* libgail-gnome-module*
  libgnome-pilot2* libgnome-vfs2.0-cil* libgnome2-0* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.24-cil* libgnomepanel2.24-cil* libgnomeui-0*
  libgnomevfs2-0* libgnomevfs2-bin* libgnomevfs2-extra* libgstfarsight0.10-0*
  libhal-storage1* libhal1* liblpint-bonobo0* libnautilus-burn4* liboobs-1-4*
  libpanel-applet2-0* libpurple0* libtelepathy-farsight0* libvirt-bin*
  mousetweaks* nautilus-share* pidgin* pidgin-otr* pitivi* policykit-gnome*
  python-gnome2* python-gnome2-desktop* python-gnomeapplet*
  python-nautilusburn* python-pyatspi* rhythmbox* seahorse-plugins*
  system-config-printer-gnome* telepathy-haze* tomboy* totem* totem-gstreamer*
  totem-mozilla* totem-plugins* tracker* tracker-search-tool* tracker-utils*
  ubuntu-desktop* ubuntu-virt-mgmt* ubuntu-virt-server* usb-creator*
  usb-creator-gtk* vinagre* virt-manager* xulrunner-1.9.1-gnome-support*
0 upgraded, 0 newly installed, 95 to remove and 0 not upgraded.
After this operation, 205MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Really? Looks like there's A LOT of dependencies to be addressed.

This is not true as I can see still a lot of hal processes running around.

---

### Post by xebian on 2010-01-15
Here is from a A2 Live Cd

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# ps ax | grep hal
 2509 ?        Ss     0:00 /usr/sbin/hald
 2510 ?        S      0:00 hald-runner
 2552 ?        S      0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event1 /dev/input/event0
 2565 ?        S      0:00 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
 2566 ?        S      0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
 2569 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 2634 pts/0    S+     0:00 grep hal
root@ubuntu:~# 



```

---

### Post by kostkon on 2010-01-15
I suppose they mean they removed HAL from the boot process but HAL will be still loaded because of the many apps that still need it.

---

### Post by MacUntu on 2010-01-15
Does the default installation depend on hal?

```
[18:00 ~]$ sudo apt-get purge hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hal is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[18:00 ~]$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Only the xorg-edgers PPA enabled.

---

### Post by VMC on 2010-01-15
> **kostkon said:**
> I suppose they mean they removed HAL from the boot process but HAL will be still loaded because of the many apps that still need it.
I think your right.

 I noticed the OP didn't say "Y" on the removal...that would have been interesting. :)

---

### Post by xebian on 2010-01-15
> **kostkon said:**
> I suppose they mean they removed HAL from the boot process but HAL will be still loaded because of the many apps that still need it.

Here is the release announcement.  

```
Hal removal

Lucid Alpha 2 sports full removal of the hal package, making Ubuntu faster to boot and faster to resume from suspend.   
```

Take whatever it means to you.

---

### Post by caryb on 2010-01-15
O wonder if hal is loading on my laptop as it hasn't recognized my battery since the removal from the boot proccess.


Cary

---

### Post by falconindy on 2010-01-15
It likely means HAL is completely removed as a necessity for Xorg (meaning it can be loaded on demand and not during boot). I already run a patched Xserver that relies directly on libudev and responds to uevents. Tastes great, less filling.

However, me and my anti-bloat mindset have had a hard time filling in a few gaps with programs that avoid the use of HAL. It's going to take more than just freedesktop giving up HAL to see it removed entirely.

---

### Post by Ibidem on 2010-01-15
> **falconindy said:**
> It likely means HAL is completely removed as a necessity for Xorg (meaning it can be loaded on demand and not during boot). I already run a patched Xserver that relies directly on libudev and responds to uevents. Tastes great, less filling.

However, me and my anti-bloat mindset have had a hard time filling in a few gaps with programs that avoid the use of HAL. It's going to take more than just freedesktop giving up HAL to see it removed entirely.
I only have libhal for the GIMP; what programs are you looking for?
Icewm (window manager)
PCManfm-nohal (file manager)
usbmount  (automount usb)
OO3.2   
Audacious
Pulseaudio

Ibidem

---

### Post by MacUntu on 2010-01-15
Banshee being another one.

---

### Post by falconindy on 2010-01-15
> **Ibidem said:**
> I only have libhal for the GIMP; what programs are you looking for?
Icewm (window manager)
PCManfm-nohal (file manager)
usbmount  (automount usb)
OO3.2   
Audacious
Pulseaudio

Ibidem
Weird. I've never needed HAL for Gimp, nor OpenOffice... Just checked dependencies on the binaries to make sure and there's nothing referencing libhal.

At the moment I'm drawing on blank on the itches I haven't been able to scratch. Mplayer and gtkPod got recompiled without HAL (and so many other things) and run without a hitch. I don't use pulseaudio (barely anyone really **needs** to), and I stick to coreutils for a file manager. I've written udev rules to cover my auto mounting.

---

### Post by BwackNinja on 2010-01-15
[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy) - how things are progressing. I think that the reason why everything can't just be purged thus far is that gnome-power-manager still depends on parts of hal. Once this is fixed, then hal can probably disappear. The gimp uses hal for configuring special input devices.

---

### Post by falconindy on 2010-01-15
> **BwackNinja said:**
> [https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy) - how things are progressing. I think that the reason why everything can't just be purged thus far is that gnome-power-manager still depends on parts of hal. Once this is fixed, then hal can probably disappear. The gimp uses hal for configuring special input devices.
Input devices, regardless of how special, can be handled by libudev or at worst, xorg.conf.

---

### Post by BwackNinja on 2010-01-15
> **falconindy said:**
> Input devices, regardless of how special, can be handled by libudev or at worst, xorg.conf.

Just as it says on the bugreport link there: [https://bugzilla.gnome.org/show_bug.cgi?id=592364](https://bugzilla.gnome.org/show_bug.cgi?id=592364)

its not so much that there's a problem, but that it needs to be done. Also, it says the need can be gone with gtk using XI2

---

### Post by chrisccoulson on 2010-01-15
HAL can already be completely removed on the default desktop, and nothing installed by default requires HAL to exist anymore. The poster above was also trying to remove libhal-storage1 and libhal1, which are libraries to allow applications to access the HAL daemon. Some applications are still linked against these libraries for now, even though they don't require HAL to be running (see the rdepends of the 2 libraries below).

Once you have removed the "hal" package, then there is no more HAL on your system, even if these libraries still exist for now.

```
$ apt-cache rdepends libhal-storage1
libhal-storage1
Reverse Depends:
  libhal-storage1-dbgsym
  xfce4-volstatus-icon
  xfce4-cddrive-plugin
  xfburn
  thunar-volman
  pmount
  pcmanfm
  oxine
  libthunar-vfs-1-2
  libpam-usb
  libexo-0.3-0
  gnome-mount
  gnome-main-menu
  exo-utils
  tracker
  libhal-storage-dev
  libgnomevfs2-0
  hal

$ apt-cache rdepends libhal1
libhal1
Reverse Depends:
  libhal1-dbgsym
  isight-firmware-tools
  xfce4-volstatus-icon
  xfce4-governor-plugin
  xfce4-cddrive-plugin
  xfburn
  wmbattery
  vlc-nox
  thunar-volman
  thoggen
  synce-trayicon
  synce-hal
  synce-gnomevfs
  sleepd
  python-rra
  python-rapi2
  ppm
  pmount
  pcscd
  pcmanfm
  oxine
  odccm
  libvlccore2
  libthunar-vfs-1-2
  libsynce0
  librra0
  librra-tools
  librapi2-tools
  librapi2
  libpam-usb
  libopenusb0
  libhd16
  libgnome-device-manager0
  libexo-0.3-0
  libdvd0
  libchipcard-tools
  kcemirror
  ivman
  halevt
  gxine
  gtkpod
  gnome-volume-manager
  gnome-mount
  gnome-main-menu
  gnome-device-manager
  exo-utils
  eggcups
  collectd
  bluez-gnome
  xserver-xorg-input-wacom
  tracker
  python-nautilusburn
  python-gnome2-desktop-dbg
  nut-hal-drivers
  nautilus-cd-burner
  libvirt-bin
  liboobs-1-4
  libnautilus-burn4
  libhal-storage1
  libhal-dev
  libgnomevfs2-0
  libgnome-pilot2
  hal
  gstreamer0.10-plugins-good
  gnome-pilot
  gimp


```

---

### Post by Ibidem on 2010-01-15
> **Ibidem said:**
> I only have libhal for the GIMP; what programs are you looking for?
Icewm (window manager)
PCManfm-nohal (file manager)
usbmount  (automount usb)
OO3.2   
Audacious
Pulseaudio

Ibidem

Clarification: The GIMP depends on libhal, nothing else approaches needing HAL

---

### Post by Darkshade on 2010-01-16
I removed hal when alpha 2 came out and everything's working just fine :)

---

### Post by zika on 2010-01-16
So, what is the verdict? Shoud we all remove hal or not? If I try to remove hal, banshee has to go also. Not a big deal. About banshee I mean... What is the gain if I remove hal?
Update: removed hal...

---

### Post by Darkshade on 2010-01-16
> **zika said:**
> So, what is the verdict? Shoud we all remove hal or not? If I try to remove hal, banshee has to go also. Not a big deal. About banshee I mean... What is the gain if I remove hal?
Update: removed hal...

Banshee? Why? As I said 2 posts earlier - I removed hal when alpha 2 came out and I (and my poor neighbors) are listening to music on Banshee right now :P

---

### Post by zika on 2010-01-16
> **Darkshade said:**
> Banshee? Why? As I said 2 posts earlier - I removed hal when alpha 2 came out and I (and my poor neighbors) are listening to music on Banshee right now :PIt was asked by Synaptic. I'll try to install it. I do not miss it much.
Update: If I try to install it it asks me to install hal.

---

### Post by chrisccoulson on 2010-01-16
> **zika said:**
> It was asked by Synaptic. I'll try to install it. I do not miss it much.
Update: If I try to install it it asks me to install hal.

Banshee still uses HAL fo detecting media plays AFAIK, so it probably won't recognise media players without it.

---

### Post by VMC on 2010-01-18
> **zika said:**
> So, what is the verdict? Shoud we all remove hal or not? If I try to remove hal, banshee has to go also. Not a big deal. About banshee I mean... What is the gain if I remove hal?
Update: removed hal...

Ok you removed it. Now ,what is the answer to your second question - what is gained?

---

### Post by zika on 2010-01-18
> **VMC said:**
> Ok you removed it. Now ,what is the answer to your second question - what is gained?I do not see any difference...

---

### Post by VMC on 2010-01-18
> **zika said:**
> I do not see any difference...

Thanks. I just removed it myself did a reboot to see it I could boot.

Everything's fine so far. I wonder why or how it got installed. According to 23meg unless I installed something that depended on hals' dependencies it shouldn't have.

Thinking it might have been some codecs I installed, I just played Rhythmbox. It played fine.

---

### Post by mc4man on 2010-01-18
> I wonder why or how it got installed.

I believe it would of been part of your 'base' install, that's why atm it's not marked as 'auto installed'

It's existence on your install ( the hal package), is of no real consequence one way or the other.

If no installed app is depending on it then it's just another unused package, in other words no effect other than using a little space

I wouldn't confuse the hal package with the libhal* shared libs, which atm a very large number of packages depend on. 
(whether they use the libs or not is beyond me

---

### Post by philinux on 2010-01-18
Alpha2 clean install.

sudo apt-get purge hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  hal*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,810kB disk space will be freed.
Do you want to continue [Y/n]?

It is obviously installed, ? , do I need it?

---

### Post by phillw on 2010-01-18
> **philinux said:**
> Alpha2 clean install.

sudo apt-get purge hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  hal*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,810kB disk space will be freed.
Do you want to continue [Y/n]?

It is obviously installed, ? , do I need it?

Hi,

Unless you're running Banshee, apparently not. If something complains it's a two second job re-install.

Phill.

---

### Post by philinux on 2010-03-02
[http://www.ubuntu.com/testing/lucid/alpha3#Hal%20removal](http://www.ubuntu.com/testing/lucid/alpha3#Hal%20removal)

How come it's still installed?

I assume it's just not in use.

---

### Post by ezsit on 2010-03-02
I've always assumed that hal is no longer used during start-up. However, other programs might need it after the system is up and running, so the packages are there, just not called during start-up.

---

### Post by philinux on 2010-03-02
> **ezsit said:**
> I've always assumed that hal is no longer used during start-up. However, other programs might need it after the system is up and running, so the packages are there, just not called during start-up.

The link above then is confusing.

> Hal removal

Lucid Alpha 3 sports **full removal **of the hal package, making Ubuntu faster to boot and faster to resume from suspend. 

---

### Post by ezsit on 2010-03-02
Not really, the quote only mentions hal's relationship to boot-up and resume from suspend. I would understand that hal is no longer used for those functions. However, since hal, or at least some hal libraries are still present, there must be a need for it sometimes. Its not that confusing.

Try removing hal and any references to it in Synaptic. I am not at my Linux box at the moment, but I would guess that a whole bunch of packages might want to get removed as well. What's bugging you so much about hal anyhow?

---

### Post by philinux on 2010-03-02
Just being curious. Full removal is the term they use.

Removing hal in synaptic does not want to remove any other package.

---

### Post by grandtoubab on 2010-03-02
> **philinux said:**
> Just being curious. Full removal is the term they use.

Removing hal in synaptic does not want to remove any other package.

I have the same understanding as Philinux, so what happend if you remove HAL?

---

### Post by kahumba on 2010-03-02
[philinux]("http://ubuntuforums.org/member.php?u=353083") is not the first one getting confused because of this/such statement(s).
It's interesting that the Canonical folks didn't bother "fixing" this (blatant) statement. Not flaming, I just hate when marketing is getting ahead of facts and then, when people point at facts some try to fire back saying that those (blatant) words actually mean something different, that's the Microsoft way, common, Canonical doesn't need this.

---

### Post by godhika on 2010-03-02
I think its a quite a stretch to call a statement buried deep in some technical blueprints as marketing. The point in moving away from hal was to improve the boot performance (at least thats how I understand it) and the almost complete halsectomy met that goal. Or are there other reasons to move away from hal ?

---

### Post by kahumba on 2010-03-02
Don't try twisting the point, it's not buried, it's in the release notes and that's quite an official resource if you ask me, and don't tell me that only a handful of weird people look at the release notes.

---

### Post by philinux on 2010-03-02
Well I'm not weird and I read the release notes always. 

Especially the known issues bit ;). Part of testing isn't it.

---

### Post by 23meg on 2010-03-02
HAL is still installed, but it's no longer initialized on boot; it's now activated via D-Bus (org.freedesktop.Hal.service) only if an application that still relies on it demands it.

As for the Technical Overview (which is where "full removal" is mentioned; **not** the release notes), like Ubuntu itself, it's not put together by "Canonical folks", but many volunteers as well. If you want to make sure it's up to date and reflects facts as closely as possible, you can edit [https://wiki.ubuntu.com/LucidLynx/TechnicalOverview](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview)  (make sure you only touch parts where know what you're dealing with, and comment your changes). Joining the #ubuntu-release channel on freenode and announcing the parts you intend to help with would help coordinate the effort.

---

### Post by philinux on 2010-03-03
@23meg, thanks for the explanation.

---

### Post by kahumba on 2010-03-03
> **23meg said:**
> HAL is still installed, but it's no longer initialized on boot; it's now activated via D-Bus (org.freedesktop.Hal.service) only if an application that still relies on it demands it.
Which is what I'm saying, hal it still there and the people who wrote the **release notes** for this alpha (feel free to correct me again if you like) didn't just make a typo but written wrong info. A typo is when you write "teh" instead of "the". Writing "fully removed" is not a typo, it's misinformation which causes confusion for those who read the release notes and then check the facts, like philinux, and don't bother "fixing" it.

---

### Post by Keyper7 on 2010-03-03
edit: nevermind

---

### Post by Uncle Spellbinder on 2010-03-03
> **kahumba said:**
> ...A typo is when you write "teh" instead of "the". Writing "fully removed" is not a typo, it's misinformation which causes confusion for those who read the release notes and then check the facts, like philinux, and don't bother "fixing" it.

Well said, kahumba. 100% spot on.

---

### Post by ezsit on 2010-03-03
> HAL is still installed, but it's no longer initialized on boot; it's now activated via D-Bus (org.freedesktop.Hal.service) only if an application that still relies on it demands it.


Funny, I think that is identical to what I wrote back on the first page of this thread. You are welcome, all that continued to ask for clarification.

Also, Hal has been fully removed from the boot process, making the language in the release notes, or technical overview, almost accurate, however poorly worded.

---

### Post by Ibidem on 2010-03-03
I've added the qualification "from the boot process" to the Technical Overview.
If anyone wants to clarify it more, please do so.

Ibidem

---

### Post by 23meg on 2010-03-03
> **kahumba said:**
> Which is what I'm saying, hal it still there and the people who wrote the **release notes** for this alpha (feel free to correct me again if you like) didn't just make a typo but written wrong info. A typo is when you write "teh" instead of "the". Writing "fully removed" is not a typo, it's misinformation which causes confusion for those who read the release notes and then check the facts, like philinux, and don't bother "fixing" it.

What you're missing is the fact that that the **Technical Overview** is not written from scratch for every milestone release; instead, the latest state of the overview from the previous milestone release forms the basis for the next one, and the important changes between the two milestones are added to the document during each freeze. "Fully removed" wasn't specifically written for this particular Alpha release; it was copied from the previous one, and maybe the one before that; perhaps even from a certain phase where HAL *was* actually removed, or decided to be removed (could be the pre-UDS phase where PiTiVi wasn't yet in). So if there's a mistake, it's keeping the old text and not updating it; not writing inaccurate information from scratch, intentionally or not.
 
And as I said before: accuracy of the overview is a collective responsibility shared by the people who want to take up this work, and there's nothing preventing *anyone* from taking it up.

---

### Post by albert.darenberg on 2010-03-14
I just upgraded from Ubuntu 9.10 to 10.04. I've noticed that HAL is still running. Is this an intended behaviour?

ubuntu% ps -e | grep hal
 1928 ?        00:00:02 hald
 1932 ?        00:00:00 hald-runner
 1954 ?        00:00:00 hald-addon-inpu
 1962 ?        00:00:00 hald-addon-rfki
 1978 ?        00:00:00 hald-addon-gene
 1970 ?        00:00:06 hald-addon-stor
 1975 ?        00:00:00 hald-addon-cpuf
 1974 ?        00:00:00 hald-addon-acpi
 3843 ?        00:00:00 hald-addon-leds

---

### Post by kurros on 2010-03-14
> **albert.darenberg said:**
> Is this an intended behaviour?


If you have an app or lib installed the depends on hal, yes.

Try removing the hal package and see what depends on the package before accepting.

---

### Post by Seventh Reign on 2010-03-14
"I just upgraded from Ubuntu 9.10 to 10.04."  Being the key statement. 

Normally upgrading from a previous release to the next is perfectly fine, however upgrading from 9.10 to 10.04 is going to cause quite a few issues.  LL is probably one  you want to do a fresh install with.

---

### Post by shafin on 2010-03-14
The upgrade does not remove HAL , happened to me too. Just go to synaptic and remove hal, it'll remove some more packages, but I went through it without any problems.

---

### Post by grandtoubab on 2010-03-16
Same for me
I remove HAL using Synaptic.
It removes Moovida  but I do not use no more this mediacenter. After that a lot of Python things were no more needed, I removed it also.
All things are working well but no improve on the boot time

---

### Post by kurros on 2010-03-16
> **grandtoubab said:**
> Same for me
I remove HAL using Synaptic.
It removes Moovida  but I do not use no more this mediacenter. After that a lot of Python things were no more needed, I removed it also.
All things are working well but no improve on the boot time

HAL isn't used for booting. It's only loaded when you use an app or library that needs it (like Moovida apparently)

---

### Post by RTrev on 2010-03-20
I remember reading that HAL would be removed from Lucid, and that another entire system would take its place.  But I just looked, and HAL is installed.

In another thread someone else noticed the same, and was advised to remove it.  I can't seem to find the thread to see if that was a good idea.

Suggestions?  The system (64-bit) seems to be running fine, so maybe don't fix it if it ain't broken? ;)

Thanks.

---

### Post by andrewabc on 2010-03-20
I believe it is still installed (some apps require it as dependency?). But it is not used when booting.

That's what I heard a while back.

You on a fresh install of beta1?

---

### Post by RTrev on 2010-03-20
> **andrewabc said:**
> I believe it is still installed (some apps require it as dependency?). But it is not used when booting.

That's what I heard a while back.

You on a fresh install of beta1?

Yep.  I wasn't going to do a fresh install, except that I saw HAL was still there in my alpha install, and thought I must have done something wrong.  But the clean reinstall didn't change it.  Thanks for the reply.

---

### Post by cyberkilla on 2010-03-20
Well, the only program that seems to depend on HAL for me is Banshee, yet HAL is running the moment I log in and open System Monitor...

---

### Post by Kenny_Strawn on 2010-03-20
DeviceKit has replaced it. The reason why HAL was removed is because it bogged down boot time. In contrast to HAL, DeviceKit does not run at startup. This means that startup time has been drastically reduced - to about 9 seconds, two slower than Google Chrome OS!

---

### Post by ezsit on 2010-03-20
> Suggestions? The system (64-bit) seems to be running fine, so maybe don't fix it if it ain't broken?

Why are people sooo concerned about Hal? Is it gone? Why is it still installed? Who the heck gives a darn? It is not used during the boot process, slowing things down. Who gives a hoot whether a few scraps are left for any possible dependencies?

---

### Post by seeker5528 on 2010-03-20
> **cyberkilla said:**
> Well, the only program that seems to depend on HAL for me is Banshee, yet HAL is running the moment I log in and open System Monitor...

The system I'm on at the moment doesn't show HAL running, maybe you are running something that doesn't necessarily depend on hal, but tries to use it.

There was something in a previous thread that, if I remember correctly, indicated that HAL wasn't removed, it was switched to on-demand loading so HAL will only load if something requests it's services.

Later, Seeker

---

### Post by 23meg on 2010-03-20
Four threads on the same topic merged. Please do a forum search before starting new threads.

---

### Post by cyberkilla on 2010-03-24
> **seeker5528 said:**
> The system I'm on at the moment doesn't show HAL running, maybe you are running something that doesn't necessarily depend on hal, but tries to use it.

There was something in a previous thread that, if I remember correctly, indicated that HAL wasn't removed, it was switched to on-demand loading so HAL will only load if something requests it's services.

Later, Seeker

Hmm, I have been upgrading for several releases now. It's possible that the behaviour of HAL never changed for me. I plan to do a fresh install of when Lucid is released.

---

### Post by airtonix on 2010-03-30
OK so i have this script that makes running scripts as the logged in user more sensible when laptop lid opens and closes...

For lucid, the issues I face are : 
+ not all laptop lids are in the same place at /proc or in DBUS.
+ finding the location without compiling "miles" of code is done by using the "find by capability" aspect of hal through DBUS.
+ detection of laptop lid button events are also listened for and fired by hal through DBUS.

Questions : 
+ obviously canonical upon deciding to remove HAL have provided another way (without using HAL) to : 
  1. find elements of your hardware easily
  2. watch for and send event signals based on that hardware.

The running thread for this is located at : 
[http://ubuntuforums.org/showthread.php?t=1076486&page=5](http://ubuntuforums.org/showthread.php?t=1076486&page=5)

---

### Post by drfox on 2010-03-30
I've removed HAL and the computer boots fine, but I've gone to Synaptic to remove libhal1 and libhalstorage1, and it appears that if I remove those packages, most of my gnome programs will be uninstalled. What are others users doing? Is there a way to safely uninstall those packages?
Larry

---

### Post by chrisccoulson on 2010-03-30
> **drfox said:**
> I've removed HAL and the computer boots fine, but I've gone to Synaptic to remove libhal1 and libhalstorage1, and it appears that if I remove those packages, most of my gnome programs will be uninstalled. What are others users doing? Is there a way to safely uninstall those packages?
Larry

No, there is no safe way to remove those, and there is no need to do that either

---

### Post by drfox on 2010-03-30
> **chrisccoulson said:**
> No, there is no safe way to remove those, and there is no need to do that either

Thanks, Chris!

Larry

---

### Post by RTrev on 2010-03-30
I think the confusion about HAL is that there was some misinformation floating around for a while.  I was specifically told that HAL had been removed from Lucid, and that a good way to check to make sure I was up-to-date was to see if HAL was still installed.

Now it appears that the actual fact is that HAL should still be installed.  It simply isn't used during login any longer.

I suspect this is what's behind all the questions about HAL, is it there, should it be removed, and so on.

Just my $0.02

---

### Post by zika on 2010-03-30
Is there any benefit of un-installing HAL?

---

### Post by petejk on 2010-03-30
When I try to remove HAL from synaptic, it offers to remove the kubuntu-desktop meta as well, so I guess we're just talking ubuntu here?

Pete

---

### Post by ezsit on 2010-03-30
I really do not get all the interest in HAL. Why the frick are so many people bent on removing HAL, or trying to remove HAL, or even care whther some random HAL libraries are installed? Who the frick gives a shiit? HAL functionality is still needed by some programs once in a while. Let it be.

---

### Post by cyberkilla on 2010-03-30
> **ezsit said:**
> I really do not get all the interest in HAL. Why the frick are so many people bent on removing HAL, or trying to remove HAL, or even care whther some random HAL libraries are installed? Who the frick gives a shiit? HAL functionality is still needed by some programs once in a while. Let it be.

They don't care enough to swear about it, but you obviously do..

> **petejk said:**
> When I try to remove HAL from synaptic, it offers to remove the kubuntu-desktop meta as well, so I guess we're just talking ubuntu here?

Pete
Yes, I noticed that too.

---

### Post by ezsit on 2010-03-30
Swearing is used to draw the reader's attention into the text. I see it worked perfectly. BTW, I misspelled the swear words, so they were not, technically, swear words.

My use of semi-swear words was to emphasize frustration at people, not at the inclusion of HAL. I don't think HAL cares one way of the other.

---

### Post by cyberkilla on 2010-03-30
> **ezsit said:**
> Swearing is used to draw the reader's attention into the text. I see it worked perfectly. BTW, I misspelled the swear words, so they were not, technically, swear words.

My use of semi-swear words was to emphasize frustration at people, not at the inclusion of HAL. I don't think HAL cares one way of the other.
:facepalm:

---

### Post by psusi on 2010-03-30
So why is hal so evil, why is it being removed, and what replaces it?  My understanding is that hal basically takes events from udev and takes desktop appropriate actions on them, such as mounting and opening a nautilus browser to show you the contents of that external hd you just connected.

---

### Post by hugmenot on 2010-03-30
psusi: [https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

---

### Post by Miguel on 2010-04-11
Talking about deprecations, I'm pretty pissed to see gnomevfs2 still on my system. Yeah, it's after an update from 9.04, but still... And yes, it pisses me. I've read a ton of stuff about how they were going to deprecate many things for gnome 2.30 but it turns out gnomevfs2 is a mean survivor. Not here! If I have to live without X in order to kill gnomevfs2...

SO BE IT!

---

### Post by zika on 2010-04-11
> **Miguel said:**
> Talking about deprecations, I'm pretty pissed to see gnomevfs2 still on my system. Yeah, it's after an update from 9.04, but still... And yes, it pisses me. I've read a ton of stuff about how they were going to deprecate many things for gnome 2.30 but it turns out gnomevfs2 is a mean survivor. Not here! If I have to live without X in order to kill gnomevfs2...

SO BE IT!I do not have it, even as a choice to install, let alone installed...

---

### Post by forcecore on 2010-04-11
> **Miguel said:**
> Talking about deprecations, I'm pretty pissed to see gnomevfs2 still on my system. Yeah, it's after an update from 9.04, but still... And yes, it pisses me. I've read a ton of stuff about how they were going to deprecate many things for gnome 2.30 but it turns out gnomevfs2 is a mean survivor. Not here! If I have to live without X in order to kill gnomevfs2...

SO BE IT!

Make fresh install it is always cleaner.

---

### Post by Miguel on 2010-04-11
> **zika said:**
> I do not have it, even as a choice to install, let alone installed...

That's curious! I get this:

```
$ aptitude search gnomevfs2
i   libgnomevfs2-0                            - Sistema de archivos virtual de GNOME (bibliotecas e
p   libgnomevfs2-0-dbg                        - Sistema de archivos virtual GNOME (bibliotecas de d
p   libgnomevfs2-bin                          - GNOME Virtual File System (support binaries)       
i   libgnomevfs2-common                       - Sistema de archivos virtual GNOME (archivos comunes
p   libgnomevfs2-dev                          - Sistema de archivos virtual GNOME (archivos de desa
pi  libgnomevfs2-extra                        - Sistema de archivos virtual GNOME (módulos extra)  
p   libgnomevfs2-ruby                         - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8                      - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8-dbg                  - GNOME VFS 2 bindings for the Ruby language         

```

EDIT: And no, I don't want to make a clean install. This is linux after all.

---

### Post by 23meg on 2010-04-11
> **Miguel said:**
> That's curious! I get this:

```
$ aptitude search gnomevfs2
i   libgnomevfs2-0                            - Sistema de archivos virtual de GNOME (bibliotecas e
p   libgnomevfs2-0-dbg                        - Sistema de archivos virtual GNOME (bibliotecas de d
p   libgnomevfs2-bin                          - GNOME Virtual File System (support binaries)       
i   libgnomevfs2-common                       - Sistema de archivos virtual GNOME (archivos comunes
p   libgnomevfs2-dev                          - Sistema de archivos virtual GNOME (archivos de desa
pi  libgnomevfs2-extra                        - Sistema de archivos virtual GNOME (módulos extra)  
p   libgnomevfs2-ruby                         - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8                      - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8-dbg                  - GNOME VFS 2 bindings for the Ruby language         

```

EDIT: And no, I don't want to make a clean install. This is linux after all.

That output shows that you only have two of those packages installed (those marked with "i"). If you wonder what's pulling them in, go to the properties of the package in Synaptic, open the "Dependencies" tab and choose "Dependent packages".

---

### Post by Miguel on 2010-04-11
> **23meg said:**
> That output shows that you only have two of those packages installed (those marked with "i"). If you wonder what's pulling them in, go to the properties of the package in Synaptic, open the "Dependencies" tab and choose "Dependent packages".

Thanks for your reply, 23meg. Synaptic shows a boatload of packages depending on libgnomevfs2-0 (I didn't know you could use it to show depending packages). The list for libgnomevfs2-common is less daunting, but shows a funny package: gnome-session (see attachment). 

In any case, one package depending on libgnomevfs2-0 is... evolution!!! what the hardy herons!!!! I really don't know what's gone wrong. Please note that I launched Synaptic in english so that it would be more informative for you. 

Using aptitude's supercow powers would give me the following:
```

$ aptitude why libgnomevfs2-common
i   libgnomevfs2-0 Depends libgnomevfs2-common (< 1:2.25)
$ aptitude why libgnomevfs2-0
i   python-gnomeapplet Depends libgnomevfs2-0 (>= 1:2.17.90)
$ aptitude why python-gnomeapplet
i   gnome-mag Depends python-gnomeapplet
$ aptitude why gnome-mag
i   ubuntu-desktop Recommends gnome-mag

```

If I removed gnome-mag and python-gnomeapplet and whatever was needed, though, some **** would still depend on libgnomevfs2. This has me perplexed, to say the least.

---

### Post by Starks on 2010-04-11
Will halsectomy be complete for Lucid or Maverick?

---

### Post by Didius Falco on 2010-04-11
> **Miguel said:**
> Thanks for your reply, 23meg. Synaptic shows a boatload of packages depending on libgnomevfs2-0 (I didn't know you could use it to show depending packages). The list for libgnomevfs2-common is less daunting, but shows a funny package: gnome-session (see attachment).

You inspired me to take a look at mine as well - my install dates from 8.04, with upgrades all the through to the current beta.

If I try to remove libgnomevfs2-0, this is what it would take out with it:

> libgnomevfs2-0 will be removed with configuration

aptoncd will be removed
gdm will be removed
gdm-guest-session will be removed
gnochm will be removed
gnome-about will be removed
gnome-alsamixer will be removed
gnome-applets will be removed
gnome-mag will be removed
gnome-orca will be removed
gnome-panel will be removed
gnome-pilot will be removed
gnome-pilot-conduits will be removed
gnome-power-manager will be removed
gnome-session will be removed
gnome-utils will be removed
gnomebaker will be removed
gobby will be removed
gstreamer0.10-gnomevfs will be removed
indicator-applet will be removed
indicator-applet-session will be removed
inkscape will be removed
libbonoboui2-0 will be removed
libgail-gnome-module will be removed
libgnome-pilot2 will be removed
libgnome2-0 will be removed
libgnome2-perl will be removed
libgnome2-vfs-perl will be removed
libgnomeui-0 will be removed
liblpint-bonobo0 will be removed
libpanel-applet2-0 will be removed
mousetweaks will be removed
nautilus-share will be removed
python-gnome2 will be removed
python-gnome2-desktop will be removed
python-gnomeapplet will be removed
python-pyatspi will be removed
rhythmbox will be removed
rhythmbox-plugins will be removed
seahorse-plugins will be removed
system-config-printer-gnome will be removed
thunderbird-gnome-support will be removed
tracker-search-tool will be removed
tsclient will be removed
ubuntu-desktop will be removed
ubuntu-tweak will be removed
usb-creator will be removed
usb-creator-gtk will be removed
vinagre will be removed


Removing libgnomevfs2-common has basically the same result - it pulls in libgnomevfs2-0, which, in turn, pulls in the above list of packages.

While I like to clean up as much cruft as I can, this list is not something I want to deal with...

---

### Post by Miguel on 2010-04-11
I think we may be victims of an "either or" dependency somewhere. Clean installs could have the modern package while us dist-upgraders have the old package already installed. But this does have a memory cost, unfortunately.

---

### Post by ezsit on 2010-04-11
Has anybody bothered to read the corrected statement on the release notes:

Quoted from: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

> HAL removal
 

This beta sports full removal of HAL from the boot process, making Ubuntu faster to boot and faster to resume from suspend.   

HAL is gone from the boot process, that is it! Can't people get it through their thick skulls? HAL is still around when needed, just not in the boot process. Holy Moly!

---

### Post by hugmenot on 2010-04-11
> **ezsit said:**
> HAL is gone from the boot process, that is it! Can't people get it through their thick skulls? HAL is still around when needed, just not in the boot process. Holy Moly!

So? What your point?

GnomeVFS is still there because some software still uses it. Probaly harder to rip that out than the HAL dependencies since nearly all software uses file i/o but only few need to enumerate devices.

---

### Post by nanog on 2010-04-11
> So? What your point?

Their point was that hal is not being removed from ubuntu -- only the boot process.

---

### Post by splicerr on 2010-04-11
> **ezsit said:**
> Has anybody bothered to read the corrected statement on the release notes:

Quoted from: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

  

HAL is gone from the boot process, that is it! Can't people get it through their thick skulls? HAL is still around when needed, just not in the boot process. Holy Moly!

That was not the original statement!

[http://www.ubuntu.com/testing/lucid/alpha1](http://www.ubuntu.com/testing/lucid/alpha1)

> 
Lucid Alpha 1 sports **full removal of the hal package**, making  Ubuntu faster to boot and faster to resume from suspend. 
They probably changed it because people were rightfully complaining that hal was still around.

---

### Post by BwackNinja on 2010-04-11
as far as I can see, libhal1 and libhal-storage1 are only here because libgnomevfs2-0 is still here.

libgnomevfs2-0 is only still here because libgnome2-0 is still here.

libgnome2-0 is still here because it is depended on by fun stuff like xulrunner-gnome-support, gnome-main-menu, evolution, gdm, gnome-utils, python-gnome2 (which is needed by gnome-about, which is needed by gnome-panel which is needed by gnome-session.)

so basically, hal is only needed because of a series of deprecated modules which we also want gone, which are needed by the main things we kinda need to have in our desktop. Looking at it like this, we're pretty close to _not_ needing to have these things at least in a default install.

this is a nice place to look at deprecated modules in gnome, and we're hoping for some more green when gnome 3 comes out :) [http://people.gnome.org/~fpeters/299.html](http://people.gnome.org/~fpeters/299.html)

and yes, the _hal_ package can be removed completely, just not libhal1 and libhal-storage1. There are no lies, only misconceptions.

---

### Post by zika on 2010-04-12
> **Miguel said:**
> That's curious! I get this:

```
$ aptitude search gnomevfs2
i   libgnomevfs2-0                            - Sistema de archivos virtual de GNOME (bibliotecas e
p   libgnomevfs2-0-dbg                        - Sistema de archivos virtual GNOME (bibliotecas de d
p   libgnomevfs2-bin                          - GNOME Virtual File System (support binaries)       
i   libgnomevfs2-common                       - Sistema de archivos virtual GNOME (archivos comunes
p   libgnomevfs2-dev                          - Sistema de archivos virtual GNOME (archivos de desa
pi  libgnomevfs2-extra                        - Sistema de archivos virtual GNOME (módulos extra)  
p   libgnomevfs2-ruby                         - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8                      - GNOME VFS 2 bindings for the Ruby language         
p   libgnomevfs2-ruby1.8-dbg                  - GNOME VFS 2 bindings for the Ruby language         

```EDIT: And no, I don't want to make a clean install. This is linux after all.**I'm sorry **for inaccurate information. Either Synaptic failed on that search or I mistyped. The status is:> ~$ aptitude search gnomevfs2
i   libgnomevfs2-0                                                                                                                                                   - GNOME Virtual File System (runtime libraries)                                                                                                                              
p   libgnomevfs2-0-dbg                                                                                                                                               - GNOME Virtual File System (debugging libraries)                                                                                                                            
p   libgnomevfs2-bin                                                                                                                                                 - GNOME Virtual File System (support binaries)                                                                                                                               
i   libgnomevfs2-common                                                                                                                                              - GNOME Virtual File System (common files)                                                                                                                                   
p   libgnomevfs2-dev                                                                                                                                                 - GNOME Virtual File System library (development files)                                                                                                                      
i   libgnomevfs2-extra                                                                                                                                               - GNOME Virtual File System (extra modules)                                                                                                                                  
p   libgnomevfs2-ruby                                                                                                                                                - GNOME VFS 2 bindings for the Ruby language                                                                                                                                 
p   libgnomevfs2-ruby1.8                                                                                                                                             - GNOME VFS 2 bindings for the Ruby language                                                                                                                                 
p   libgnomevfs2-ruby1.8-dbg                                                                                                                                         - GNOME VFS 2 bindings for the Ruby language 

---

### Post by Miguel on 2010-04-12
> **BwackNinja said:**
> so basically, hal is only needed because of a series of deprecated modules which we also want gone, which are needed by the main things we kinda need to have in our desktop. Looking at it like this, we're pretty close to _not_ needing to have these things at least in a default install.

The thing is, vanilla gnome 2.30 (and that includes gnome-session, evolution and I think everything you mentioned) does *not* require gnomevfs. No way. Most of the work that has gone into gnome 2.30 has been removing old dependencies.

[Gnome 2.30 release notes](http://library.gnome.org/misc/release-notes/2.30/#rndevelopers) (hopefully, in your preferred language)
[Cleaning tasks for gnome3](http://people.gnome.org/~fpeters/299.html)

---

### Post by BwackNinja on 2010-04-12
> **Miguel said:**
> The thing is, vanilla gnome 2.30 (and that includes gnome-session, evolution and I think everything you mentioned) does *not* require gnomevfs. No way. Most of the work that has gone into gnome 2.30 has been removing old dependencies.

[Gnome 2.30 release notes](http://library.gnome.org/misc/release-notes/2.30/#rndevelopers) (hopefully, in your preferred language)
[Cleaning tasks for gnome3](http://people.gnome.org/~fpeters/299.html)

> Starting with GNOME 3.0, various deprecated parts of GNOME will be removed. These deprecated components include libraries such as libart_lgpl, libbonobo, libbonoboui, libglade, libgnome, libgnomecanvas, libgnomeprint, libgnomeprintui, libgnomeui, and libgnomevfs. For applications that ship as part of the GNOME Desktop, a number of cleanup tasks have been carried out to ensure no deprecated code is used. This will ensure a smooth transition to GNOME 3.0.

as it says there on that page, they will be removed for _GNOME 3.0_ we have GNOME 2.30. GNOME 2.32 will be GNOME 3.0.

And I already posted that second link, and it only supports what I say:

```
$ apt-cache rdepends gnome-about
gnome-about
Reverse Depends:
  ubuntustudio-desktop
  gnome-desktop-environment
  ubuntu-netbook
  ubuntu-desktop
  gnome-panel
  gnome-desktop-data

$ apt-cache depends gnome-about
gnome-about
  Depends: python
  Depends: python-gtk2
  Depends: python-gobject
  Depends: python-gnome2
  Depends: python-cairo
  Depends: gnome-desktop-data
  Conflicts: gnome-core
  Conflicts: gnome-desktop-data
  Replaces: gnome-desktop-data

$ apt-cache depends python-gnome2
python-gnome2
  ...
  Depends: libbonobo2-0
  Depends: libbonoboui2-0
  Depends: libc6
  Depends: libcairo2
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgconf2-4
  Depends: libglib2.0-0
  Depends: libgnome2-0
  Depends: libgnomecanvas2-0
  Depends: libgnomeui-0
  Depends: libgnomevfs2-0
  Depends: libgtk2.0-0
  ...

```

---

### Post by nanog on 2010-04-12
Actually hal is still present because its still used by hundreds of packages.  I am sure it will be removed from the default install as more commonly used packages are rewritten to use udev.

---

### Post by seeker5528 on 2010-04-12
> **Miguel said:**
> The thing is, vanilla gnome 2.30 (and that includes gnome-session, evolution and I think everything you mentioned) does *not* require gnomevfs. No way. Most of the work that has gone into gnome 2.30 has been removing old dependencies.

[Gnome 2.30 release notes](http://library.gnome.org/misc/release-notes/2.30/#rndevelopers) (hopefully, in your preferred language)
[Cleaning tasks for gnome3](http://people.gnome.org/~fpeters/299.html)

The page showing the cleaning tasks shows that Evolution and some language bindings still use libgnomevfs.

Assuming that page as been 2.99 since it was created and is tracking the progress to 3.0, it probably includes work that was completed after 2.30 or at least too late in the development cycle to be included in 2.30.

And that's only tracking the Gnome stuff, not all the stuff developed outside of the Gnome project, which may take a little longer to clean up.

Later, Seeker

---

### Post by iClouseau88 on 2010-04-12
Removing HAL is such a stupid idea,since without HAL one cannot see legacy hardware being recognized by Ubuntu.  The argument to make Ubuntu boots faster does not make sense to me at all.  If I want a faster boot I can always disable unneccessary processes and/or delete older files. Just my 2 cents!

---

### Post by hugmenot on 2010-04-13
> **iClouseau88 said:**
> Removing HAL is such a stupid idea,since without HAL one cannot see legacy hardware being recognized by Ubuntu.

Ugh, no, why? 


All functionality was moved to udev.

---

