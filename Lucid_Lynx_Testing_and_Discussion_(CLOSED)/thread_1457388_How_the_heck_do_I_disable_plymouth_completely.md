---
title: "How the heck do I disable plymouth completely?"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gastly on 2010-04-18
I just want to disable plymouth completely, I don't really care for the 'nice' bootsplash that it offers.

I've tried removing the "quiet splash" option in Grub, it disables the splash, but at shutdown, some artifacts show up on the screen and plymouth still runs in the background eating up valuable boot time and therefore slowing down the boot process. (Attached bootchart graph). (**EDIT: View it here: [http://img96.imageshack.us/img96/788/gastlydesktoplucid20100.png](http://img96.imageshack.us/img96/788/gastlydesktoplucid20100.png))

If I try to remove the package, it takes down all the "core" packages with it...why in the world do other core packages depend on plymouth? I mean it just shows a splash screen, so xorg should not depend on it.

My boot in karmic was around 15-17 seconds and on lucid (which was aiming for a 10 second boot I believe) is about 26 seconds.

Does someone know a way to disable it completely? Thanks in advance :)

---

### Post by Uncle Spellbinder on 2010-04-18
Not that I would understand it anyway, but your boot-chart attachment is not even close to being viewable.

---

### Post by aviramof on 2010-04-18
not that i'm an expert but did you tried to remove plymouth package from synaptic?

---

### Post by Uncle Spellbinder on 2010-04-18
Plymouth cannot be removed anymore. It depends on far to much (or far to much depends on it).

---

### Post by gastly on 2010-04-18
> **Uncle Spellbinder said:**
> Not that I would understand it anyway, but your boot-chart attachment is not even close to being viewable.

Sorry about that, I didn't know the forums resize the images automatically. Here's the full link [http://img96.imageshack.us/img96/788/gastlydesktoplucid20100.png](http://img96.imageshack.us/img96/788/gastlydesktoplucid20100.png)

> **aviramof said:**
> not that i'm an expert but did you tried to remove plymouth package from synaptic?
Yes I did and it tries to remove half of Ubuntu with it.

> **Uncle Spellbinder said:**
> Plymouth cannot be removed anymore. It depends on far to much (or far to much depends on it).
hmm...so we're stuck with it eh? Well, I think most of the core packages don't really need plymouth, I don't know why they added plymouth as a dependency to them.

---

### Post by philinux on 2010-04-18
Wow I just did a remove to see what gives. I've never seen anything like it before. It wants to remove 1,799MBs. This has got to be a bug.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331)
A splash screen is now viewed as a core package.

```
sudo apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following packages will be REMOVED
  acpi-support acpid aisleriot alsa-base alsa-utils anacron apparmor
  apparmor-utils apport apport-gtk aptdaemon apturl at at-spi avahi-daemon
  avahi-utils bluez bluez-cups bootchart brasero brasero-common brltty
  brltty-x11 capplets-data checkbox checkbox-gtk compiz compiz-core
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf computer-janitor-gtk console-setup consolekit
  couchdb-bin cron cups cups-driver-gutenprint dbus dbus-x11 default-jre
  desktopcouch dkms dmsetup e2fsprogs eog erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evince evolution evolution-couchdb
  evolution-data-server evolution-exchange evolution-indicator
  evolution-plugins evolution-webcal f-spot file-roller firefox
  firefox-branding firefox-gnome-support foo2zjs foomatic-db
  foomatic-db-engine friendly-recovery ftp gbrainy gcalctool
  gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm
  gdm-guest-session gedit ghostscript-cups ghostscript-x gimp gksu gnome-about
  gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install
  gnome-control-center gnome-disk-utility gnome-games-common gnome-keyring
  gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-power-manager
  gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra
  gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share
  gnome-utils gnomine gstreamer0.10-plugins-good gstreamer0.10-pulseaudio
  gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service hal
  hostname hplip hplip-cups ibus ibus-m17n ibus-table icedtea6-plugin ifupdown
  imagemagick indicator-applet indicator-applet-session indicator-me
  indicator-session indicator-sound initramfs-tools initscripts irqbalance
  jockey-common jockey-gtk kbd language-selector lesstif2 lftp
  libaccess-bridge-java libaccess-bridge-java-jni libasound2-plugins
  libatspi1.0-0 libbonoboui2-0 libbrasero-media0 libcamel1.2-14
  libcanberra-pulse libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0
  libdesktopcouch-glib-1.0-2 libebackend1.2-0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libgail-gnome-module libgconf2-4 libgconf2.0-cil libgdata6 libgdu0
  libgegl-0.0-0 libgksu2-0 libgnome-desktop-2-17 libgnome-media0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
  libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgstfarsight0.10-0
  libgtkhtml-editor0 libgtkhtml3.14-19 libgweather-common libgweather1 libice6
  liblpint-bonobo0 libm17n-0 libmagickcore2 libmagickcore2-extra
  libmagickwand2 libmetacity-private0 libnet-dbus-perl libnss-mdns liboobs-1-4
  libpanel-applet2-0 libpolkit-gtk-1-0 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libpurple0 librpc-xml-perl libsdl1.2debian
  libsdl1.2debian-pulseaudio libsm6 libsoup-gnome2.4-1
  libstartup-notification0 libtelepathy-farsight0 libubuntuone-1.0-1
  libwebkit-1.0-2 libwnck22 libwww-perl libxaw7 libxklavier16
  libxml-parser-perl libxml-sax-expat-perl libxml-twig-perl libxml-xpath-perl
  libxmu6 libxres1 libxss1 libxt6 libxtst6 libxvmc1 libxxf86dga1 light-themes
  linux-generic linux-image-2.6.32-20-generic linux-image-2.6.32-21-generic
  linux-image-generic linux-sound-base localepurge logrotate m17n-contrib
  m17n-db media-player-info metacity metacity-common module-init-tools
  mountall mousetweaks mtink nautilus nautilus-data nautilus-gksu
  nautilus-sendto nautilus-share netbase network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd ntfs-3g ntpdate
  nvidia-current nvidia-settings obex-data-server onboard openjdk-6-jre
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-filter-binfilter
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-officebean
  openoffice.org-report-builder-bin openoffice.org-writer openprinting-ppds
  pcmciautils pitivi plymouth plymouth-label plymouth-theme-fade-in
  plymouth-theme-ubuntu-logo pm-utils pm-utils-powersave-policy policykit-1
  policykit-1-gnome powermgmt-base ppp pppconfig pppoeconf pptp-linux procps
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-farsight python-gconf python-gnome2
  python-gnomeapplet python-papyon python-pyatspi python-speechd
  python-ubuntuone python-uno python-virtkey python-webkit python-wnck
  quadrapassel rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store rsyslog screen-resolution-extra
  screensaver-default-images seahorse simple-scan software-center
  software-properties-gtk speech-dispatcher splix system-config-printer-gnome
  system-tools-backends telepathy-butterfly telepathy-haze telepathy-salut
  telnet tomboy totem totem-common totem-mozilla totem-plugins
  transmission-gtk tsclient ttf-mscorefonts-installer ubufox ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers ubuntuone-client-gnome udev udisks
  ufw update-manager update-notifier upower upstart ureadahead
  usb-creator-common usb-creator-gtk util-linux vinagre vino wireless-crda
  x-ttcidfont-conf x11-apps x11-common x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils
  xinit xorg xscreensaver-data xscreensaver-gl xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xulrunner-1.9.1
  xulrunner-1.9.2 yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 451 to remove and 0 not upgraded.
After this operation, 1,799MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase &#8216;Yes, do as I say!&#8217;
 ?] 

```

---

### Post by MacUntu on 2010-04-18
> **gastly said:**
> My boot in karmic was around 15-17 seconds and on lucid (which was aiming for a 10 second boot I believe) is about 26 seconds.

What's up with your ureadahead? I'd delete /var/lib/ureadahead/pack*, reboot, wait a bit, reboot and bootchart again.

As for removing Plymouth: philinux's post should show that it's not a good idea - Plymouth isn't just a new splash screen. Don't know about your shutdown issue, though.

---

### Post by uRock on 2010-04-18
This bites, I was looking forward to removing it and installing the Karmic or Jaunty splash. Oh well, still beats the poop out of restarting a Windows system.

---

### Post by zika on 2010-04-18
There was a talk about disabling Plymouth. I've tried and it works: rename all the files plymouth* in /etc/init/ or move them out of that folder...
Please do not blame me if something goes wrong on Your system, since I've not tried this in the last week, changes were made to Plymouth in the meantime...
I did not try the same with plymouth* in /etc/init.d ...

---

### Post by RAOF on 2010-04-19
Plymouth is not just the splash; it's also the way that the initscripts interact with the user (such as cryptsetup needing you to enter a passphrase, or fsck asking what to do), and sets up other things.

It's not just the splash. :)

---

### Post by zika on 2010-04-19
> **RAOF said:**
> Plymouth is not just the splash; it's also the way that the initscripts interact with the user (such as cryptsetup needing you to enter a passphrase, or fsck asking what to do), and sets up other things.

It's not just the splash. :)It is supposed to be not just the splash... as much as I understand... :) At this moment... It is surely more than just the splash... :(

---

### Post by purgatori on 2010-04-19
> **zika said:**
> It is supposed to be not just the splash... as much as I understand... :) At this moment... It is surely more than just the splash... :(

And yet... it doesn't affect Ubuntu at all when you remove it.

Look around for a 'hacked' version of mountall which eliminates all the dependency nonsense built in to plymouth. After you install said hacked version, plymouth can be removed, and I for one did not detect any deleterious effects. 

This really is how it should have been from the beginning.

---

### Post by k3lt01 on 2010-04-19
> **gastly said:**
> I just want to disable plymouth completely, I don't really care for the 'nice' bootsplash that it offers.

I've tried removing the "quiet splash" option in Grub, it disables the splash, but at shutdown, some artifacts show up on the screen and plymouth still runs in the background eating up valuable boot time and therefore slowing down the boot process. (Attached bootchart graph). Talk about timing. I've been working on a related issue for half of today.

You can't disable Plymouth, it's just to ingrained into the system to remove it. What you can do though is take "splash" out of your Grub line that deals with the kernel itself. That will remove th splash aspect of plymouth from bootup and shutdown but will leave the required init aspect intact so your system will actually boot properly. Taking out "quiet splash" does very little as you have found out so just remove "splash" and give it  a go.

---

### Post by gastly on 2010-04-19
> **RAOF said:**
> Plymouth is not just the splash; it's also the way that the initscripts interact with the user (such as cryptsetup needing you to enter a passphrase, or fsck asking what to do), and sets up other things.

It's not just the splash. :)

I think that's really the problem isn't it? All other utilities depend way too much on it :)

---

### Post by gastly on 2010-04-19
> **purgatori said:**
> And yet... it doesn't affect Ubuntu at all when you remove it.

Look around for a 'hacked' version of mountall which eliminates all the dependency nonsense built in to plymouth. After you install said hacked version, plymouth can be removed, and I for one did not detect any deleterious effects. 

This really is how it should have been from the beginning.

hmm...would it be possible to use karmic's mountall? It doesn't have dependencies on plymouth.

> **k3lt01 said:**
> Talk about timing. I've been working on a related issue for half of today.

You can't disable Plymouth, it's just to ingrained into the system to remove it. What you can do though is take "splash" out of your Grub line that deals with the kernel itself. That will remove th splash aspect of plymouth from bootup and shutdown but will leave the required init aspect intact so your system will actually boot properly. Taking out "quiet splash" does very little as you have found out so just remove "splash" and give it  a go.

Well, I've tried it, I removed "quiet splash" and I think keeping the "quiet" and removing the "splash" will have the same effect as removing both, right? :)
Still, some artifacts do show up at shutdown, I'm just wondering what's causing it.

Maybe I'll try and fiddle with plymouth conf files in /etc/init :mrgreen:

---

### Post by Yellow Pasque on 2010-04-19
Here's a version of mountall with no mandatory dependency on plymouth:
[https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

It's currently a bit older than the default lucid version, but you can still use it (and I will update the next time I boot into ubuntu).

---

### Post by grandtoubab on 2010-04-19
I try with that one
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372/comments/21](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372/comments/21)

remove plymouth and was unable to boot again very badly!!!!

so I have to downgrade to the official version 
[http://packages.ubuntu.com/lucid/i386/admin/mountall](http://packages.ubuntu.com/lucid/i386/admin/mountall)

reinstall at least plymouth and the logo theme to recover my desktop

so I am asking myself if I have to thanks this Dr folamour....

---

### Post by k3lt01 on 2010-04-19
> **gastly said:**
> Well, I've tried it, I removed "quiet splash" and I think keeping the "quiet" and removing the "splash" will have the same effect as removing both, right? :)That isn't what happened in my case, I am finding more and more you need to do exactly what the devs tell you, on word extra here or there can make a difference.

---

### Post by gastly on 2010-04-20
> **Temüjin said:**
> Here's a version of mountall with no mandatory dependency on plymouth:
[https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

It's currently a bit older than the default lucid version, but you can still use it (and I will update the next time I boot into ubuntu).

Thanks!, I installed mountall from this ppa and then I removed plymouth (aptitude did try to remove ubuntu-desktop with it, but it offers other suggestions when you press 'n').

All in all, plymouth is out of my system yay! :D
It just made my boot 6 sec's faster (26 to 20 sec's hehe).
Although an error is shown at boot and at shutdown about plymouth being 'terminated' with a certain exit status (dunno the exact line). I believe that plymouth is being started but since it's not there, therefore the error shows up. But still, it beats getting shown some strange artifacts at shutdown :)

---

### Post by psusi on 2010-04-20
Wait until fsck finds something wrong and tries to ask you a question.  You won't get the message, and your system will just appear to hang during boot.

That is why plymouth is required.

---

### Post by emarkay on 2010-04-20
> **psusi said:**
> Wait until fsck finds something wrong and tries to ask you a question.  You won't get the message, and your system will just appear to hang during boot.

That is why plymouth is required.

So, surely there's a way to get this information in another way.
Seems strange so complex of a program became so integral so quickly... :)
Anyone look in the Plymouth code for "Approved by the FBI" or "NSA Approved"???!!

---

### Post by Longinus00 on 2010-04-20
> **emarkay said:**
> So, surely there's a way to get this information in another way.
Seems strange so complex of a program became so integral so quickly... :)
Anyone look in the Plymouth code for "Approved by the FBI" or "NSA Approved"???!!

I don't know what you're talking about but in older versions usplash was used instead of plymouth. Basically, you need something and plymouth has some real advantages compared to usplash.

---

### Post by Yellow Pasque on 2010-04-20
> **Longinus00 said:**
> I don't know what you're talking about but in older versions usplash was used instead of plymouth. Basically, you need something and plymouth has some real advantages compared to usplash.
In past Ubuntu versions, those of us who just wanted a fast/informative text boot could quickly/easily purge usplash. I know plymouth is pretty and ties boot elements together, but it seems like it could use more bugfixing. Why Ubuntu chose an LTS release to introduce plymouth is beyond me, but it seems to be a pattern (a poorly-configured pulseaudio got introduced in Hardy/8.04 LTS).

---

### Post by qamelian on 2010-04-20
> **Longinus00 said:**
> I don't know what you're talking about but in older versions usplash was used instead of plymouth. Basically, you need something and plymouth has some real advantages compared to usplash.

Oddly enough, I remember a vast outcry over Plymouth NOT being used instead of Usplash a version or two ago. Oh, how the tables have turned!:lolflag:

---

### Post by Didius Falco on 2010-04-20
> **qamelian said:**
> Oddly enough, I remember a vast outcry over Plymouth NOT being used instead of Usplash a version or two ago. Oh, how the tables have turned!:lolflag:

If it were the same people, that would be of interest, but I suspect those examples would be thin on the ground.

---

### Post by Yellow Pasque on 2010-04-20
> **qamelian said:**
> Oddly enough, I remember a vast outcry over Plymouth NOT being used instead of Usplash a version or two ago. Oh, how the tables have turned!:lolflag:

I think plymouth is a great OPTION, but I don't think it's stable enough to force on everyone (especially in an LTS release). Ubuntu put a lot of focus on speeding boot times in the 9.x releases, and they also went with a nice  xsplash option in Karmic. Plymouth may be the way of the future, but it feels like a definite step backwards right now.

---

### Post by uRock on 2010-04-20
Who is forcing you to use it? You don't have to upgrade any time soon unless you are running Intrepid. How else are they going to make it work without putting it out there and testing it? I think they are doing a great job working the kinks out and before long there will be ways to change the boot theme.

---

### Post by Yellow Pasque on 2010-04-20
> **uRock said:**
> Who is forcing you to use it? You don't have to upgrade any time soon unless you are running Intrepid. How else are they going to make it work without putting it out there and testing it? I think they are doing a great job working the kinks out and before long there will be ways to change the boot theme.
Ok. I could stay on an older release without plymouth, but then software starts getting outdated. Oh well, I guess this is why I've switched to a rolling-release distro (Debian Sidux) for my main install.

> How else are they going to make it work without putting it out there and testing it?
Again, introducing it in an LTS release seems a bit aggressive.

---

### Post by k3lt01 on 2010-04-20
> **Didius Falco said:**
> If it were the same people, that would be of interest, but I suspect those examples would be thin on the ground.Maybe they are in witness protection or something because they are afraid of the angry barbarian hordes their actions have unleashed :lolflag:

In all seriousness though urock is right, and in the same vein so are people saying the opposite. The devs will never please everyone its just a pity people can't be constructive in their complaints instead of some of the constant whining that has been coming through in the last couple of releases.

---

### Post by psusi on 2010-04-21
Again, plymouth is required to multiplex access to the console by the various startup jobs that are now run in parallel by upstart.  One of the big goals of lucid has been faster boots, which is why it is using upstart to run startup jobs in parallel instead of one at a time, and thus, why you have plymouth.  If you don't like it, then go back to an older, slower release.  If there is something wrong with it, then generate quality bug reports so it can get fixed.

---

### Post by Mr. Picklesworth on 2010-04-21
> **philinux said:**
> Wow I just did a remove to see what gives. I've never seen anything like it before. It wants to remove 1,799MBs. This has got to be a bug.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331)
A splash screen is now viewed as a core package.


Philinux, I just left a comment on the bug report you linked to. The mountall package has, since version 2.10, had a hard dependency on Plymouth.

Here's the relevant [changelog]("https://edge.launchpad.net/ubuntu/+source/mountall/2.10") entry:
>   * Add hard dependency on Plymouth; without it running, mountall will ignore any filesystem which doesn't show up within a few seconds or that fails to fsck or mount.  If you don't want graphical splash, you simply need not install themes.

---

### Post by null_pointer_us on 2010-04-21
This command should remove the themes:

```
sudo aptitude remove plymouth-theme-ubuntu-text plymouth-theme-ubuntu-logo
```

It looks like [COLOR="DarkOrange"]plymouth-label[/COLOR] and [COLOR="DarkOrange"]plymouth-x11[/COLOR] can also be removed.

Some people in this thread said that Plymouth is required for some interactive steps like fsck prompts. Could they clarify which packages are required just to keep that prompt behavior without the graphical stuff?

---

### Post by djchandler on 2010-04-21
I have the RC installed from the 4/19 ISO. The impression I have is that issues with Plymouth have been resolved for the most part. At least I'm not encountering the problems I had before this fresh install.

When it works it's nice. Hang in there everybody.
:guitar:

---

### Post by gastly on 2010-04-23
I updated to the rc and the first thing I did was to install the nvidia binary drivers and blacklist nouveau. It's been running pretty good, the slow boot problem is gone now and the artifacts are also gone at shutdown.

Plymouth still runs, but I have no problem with it now as it's not slowing things down like before.

Oh and btw, installing a hacked version of mountall is a bad idea, I've learned now :lolflag: :)

---

