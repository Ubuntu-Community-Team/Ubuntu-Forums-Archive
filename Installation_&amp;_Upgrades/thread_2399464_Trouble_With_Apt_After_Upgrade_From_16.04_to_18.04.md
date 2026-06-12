---
title: "Trouble With Apt After Upgrade From 16.04 to 18.04"
date: 2018-08-25
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2018-08-25
I ran an upgrade last night to go from 16.04LTS to 18.04LTS. This morning, the system told me that the upgrade failed due to an error and that it would run recovery. Well, it didn't run anything, so  rebooted. When I did, the system is upgraded to 18.04 (as per lsb_release) but I had/have trouble with installing packages. Everything else seems to work, though.

First, it was telling me that I had broken packages (ubuntu-desktop). Well, I'm running the MATE desktop environment, so I did the suggested [sudo apt --fix-broken install] as well as an [autoremove] and [autoclean] which removed the ubuntu-desktop package along with some other files. I no longer show any broken packages BUT.... if I try to install any package from within the Synaptic Package Manager, that program becomes a broken package and I cannot go any further. If I run this install from the command line, this is what I get: 

```

derek@derek-home:~$ sudo apt-get install vlc
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-plugin-qt (= 3.0.3-1-1ubuntu1) but it is not going to be installed
       Depends: vlc-plugin-video-output (= 3.0.3-1-1ubuntu1) but it is not going to be installed
       Recommends: vlc-plugin-skins2 (= 3.0.3-1-1ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I ran a [purge] on vlc and then tried to reinstall it and I get the same error. 

If I try to install tellico, I get this error:

```

derek@derek-home:~$ sudo apt-get install tellico
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tellico : Depends: kio but it is not going to be installed
           Depends: libkf5cddb5 but it is not going to be installed
           Depends: libkf5completion5 (>= 4.97.0) but it is not going to be installed
           Depends: libkf5configgui5 (>= 4.97.0) but it is not going to be installed
           Depends: libkf5configwidgets5 (>= 4.98.0) but it is not going to be installed
           Depends: libkf5crash5 (>= 5.15.0) but it is not going to be installed
           Depends: libkf5guiaddons5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5iconthemes5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5jobwidgets5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5khtml5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5kiocore5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5kiofilewidgets5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5kiogui5 but it is not going to be installed
           Depends: libkf5kiowidgets5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5newstuff5 (>= 5.27.0) but it is not going to be installed
           Depends: libkf5parts5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5sane5 (>= 4.3.4) but it is not going to be installed
           Depends: libkf5service-bin but it is not going to be installed
           Depends: libkf5service5 (>= 4.99.0) but it is not going to be installed
           Depends: libkf5solid5 (>= 4.97.0) but it is not going to be installed
           Depends: libkf5sonnetui5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5textwidgets5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5wallet-bin but it is not going to be installed
           Depends: libkf5wallet5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5widgetsaddons5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5windowsystem5 (>= 4.96.0) but it is not going to be installed
           Depends: libkf5xmlgui5 (>= 4.98.0) but it is not going to be installed
           Depends: libpoppler-qt5-1 (>= 0.24.5) but it is not going to be installed
           Depends: libqt5gui5 (>= 5.7.0) but it is not going to be installed
           Depends: libqt5widgets5 (>= 5.6.0~beta) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Both of these were installed before the upgrade. Another question I have is... why does a dist-upgrade remove packages (like tellico) and can you not tell it to leave them alone!?

If I try to do an [upgrade] now, it tells me that there are packages held back:

```

derek@derek-home:~$ sudo apt-get upgrade
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gir1.2-gst-plugins-base-1.0 gnome-session-bin leocad libfarstream-0.2-5
  libjavascriptcoregtk-4.0-18 libsuil-0-0 libwebkit2gtk-4.0-37 pulseview
  sigrok
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

If I try to do a [dist-upgrade] now, it tries to remove the mate-desktop environment! This is what I am talking about....

```

derek@derek-home:~$ sudo apt-get dist-upgrade
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apturl-common atril-common fonts-mathjax fonts-stix gir1.2-gtk-2.0
  libatrildocument3 libexiv2-14 libgexiv2-2 libjs-mathjax libxpresent1
  shotwell-common zenity-common
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  apturl atril deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 deja-dup-caja gufw libatrilview3 marco
  mate-desktop-environment-core shotwell ubuntu-mate-core ubuntu-mate-desktop
  zenity
The following packages have been kept back:
  gir1.2-gst-plugins-base-1.0 gnome-session-bin leocad libfarstream-0.2-5
  libjavascriptcoregtk-4.0-18 libsuil-0-0 libwebkit2gtk-4.0-37 pulseview
  sigrok
0 upgraded, 0 newly installed, 15 to remove and 9 not upgraded.
After this operation, 15.3 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

What can I do to fix this?

-=[ EDIT ]=-
I don't know if this helps, but I ran an install on vlc using aptitude instead of apt-get and this was the output:

```

derek@derek-home:~$ sudo aptitude install vlc
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
The following NEW packages will be installed:
  libaribb24-0{a} libbasicusageenvironment1{a} libcddb2{a} libdvbpsi10{a} 
  libebml4v5{a} libegl-mesa0{ab} libegl1{a} libglvnd0{a} libgroupsock8{a} 
  libkate1{a} liblivemedia62{a} libmatroska6v5{a} libmicrodns0{a} 
  libmpcdec6{a} libnfs11{a} libopenmpt-modplug1{a} libplacebo4{a} 
  libqt5gui5{a} libqt5svg5{a} libqt5widgets5{a} libqt5x11extras5{a} 
  libresid-builder0c2a{a} libsdl-image1.2{a} libsidplay2{a} libssh2-1{a} 
  libupnp6{a} libusageenvironment3{a} libva-wayland2{a} libvlc-bin{a} 
  libvlc5{a} libvulkan1{a} qt5-gtk-platformtheme{a} vlc vlc-bin{a} 
  vlc-data{a} vlc-l10n{a} vlc-plugin-base{a} vlc-plugin-qt{a} 
  vlc-plugin-skins2{a} vlc-plugin-video-output{a} 
  vlc-plugin-video-splitter{a} vlc-plugin-visualization{a} 
0 packages upgraded, 42 newly installed, 0 to remove and 9 not upgraded.
Need to get 6,885 kB/17.3 MB of archives. After unpacking 82.6 MB will be used.
The following packages have unmet dependencies:
 libegl-mesa0 : Depends: libgbm1 (= 18.0.5-0ubuntu0~18.04.1) but 1:18.0.1-0~x~padoka0 is installed
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      libegl-mesa0 [Not Installed]                       
2)      libegl1 [Not Installed]                            
3)      libqt5gui5 [Not Installed]                         
4)      libqt5svg5 [Not Installed]                         
5)      libqt5widgets5 [Not Installed]                     
6)      libqt5x11extras5 [Not Installed]                   
7)      qt5-gtk-platformtheme [Not Installed]              
8)      vlc [Not Installed]                                
9)      vlc-plugin-qt [Not Installed]                      
10)     vlc-plugin-skins2 [Not Installed]                  
11)     vlc-plugin-video-output [Not Installed]            



Accept this solution? [Y/n/q/?] 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

---

### Post by rebeltaz on 2018-08-25
dist-upgrade log files attached....


[ATTACH]280845[/ATTACH]

-and-

[ATTACH]280844[/ATTACH]

---

### Post by rebeltaz on 2018-08-25
As an added issue... whenever I start up a terminal window, I get this:

```

ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.

```

I fixed this by installing gtk3-nocsd, but .....

---

### Post by Impavidus on 2018-08-26
You have a release upgrade gone wrong. I can't say why, maybe because of non-standard repositories, broken packages beforehand, pinned packages or something else. The best way out is a fresh install. Create a 18.04.1 live disk, backup your files and install.

---

### Post by rebeltaz on 2018-08-26
> **Impavidus said:**
> You have a release upgrade gone wrong. I can't say why, maybe because of non-standard repositories, broken packages beforehand, pinned packages or something else. The best way out is a fresh install. Create a 18.04.1 live disk, backup your files and install.

A lot of the time, I see this as the answer to updates gone wrong. I even see people recommend this over upgrades. This is not my first time having to do a clean install. I have no problem doing that - aside from the obvious headaches of having to set the system back up the way I had/like it. I'm just curious as to why Ubuntu includes an "in place" upgrade option if things can (or apparently often do) do so wrong in the first place? 

I know that the clean install is the simple solution - for both me and the ones from whom I seek help - but surely that cannot be the **only** answer.....

---

### Post by Impavidus on 2018-08-26
I've done about 15 release upgrades and only had minor issues twice. I never had to do a clean install (not to replace a broken system), although I did a few clean installs anyway and they helped to clean up the system. In my experience, release upgrades usually work.

In your case, it's a big mess. Why was gtk3-nocsd not installed, despite being needed? Why was it needed anyway (it's not on my system, but I run Xubuntu)? What's the issue with libgbm1, of which you have some non-standard version? Why do you run into package conflicts when you try to install any package?

I suspect you have a bunch of non-standard software sources. Removing those and upgrading (or downgrading) everything to the versions in the official repos may help a bit, if it works. But even if it works, it doesn't guarantee a clean upgrade. If you really wish to investigate, go ahead.

BTW, a dist-upgrade is designed to remove packages when they conflict with the newer version of a package that is to be upgraded.

---

### Post by rebeltaz on 2018-08-27
Well... I fixed the apt issue via some creative use of aptitude, but that broke something else to the point where I could login under recovery mode - all the way into the GUI - but it would not go past the splash screen in normal mode. So then I tried removing everything mate related and installed the gnome desktop packages. That got me to a login prompt loop, even in recovery mode. Finally, after many hours of headache, I bit the bullet and did a clean install. grumble.... grumble... grumble...

---

