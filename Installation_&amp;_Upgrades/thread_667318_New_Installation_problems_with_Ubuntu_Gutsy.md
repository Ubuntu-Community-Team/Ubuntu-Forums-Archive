---
title: "New Installation problems with Ubuntu Gutsy"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by alonge on 2008-01-14
I actually have a few issues after installation:
1. When putting a DVD in the DVD player Totem movie player pops up and tells me "An Error occurred, could not read from resource" GStreamer is all enabled.
2. I am unable to view any movie clips on firefox. I subscribe to Blockbuster and watch the movie trailers, but am unable to do so with linux.
3. The OS was installed and I went into the Synaptic package manager and added packages and only ones that had the Ubuntu image next to them. Now when the OS boots up, first it says kubuntu, then a screen comes up that says Edubuntu and that is where I have to put in my user and pass.
I originally just installed Ubuntu (Gutsy). Doees this matter?
4. (Biggest Problem) When I go to the terminal and su root it won't accept the password I used when I first did the installation. I was only prompted for one password during installation and that one works for everything when I am in the OS.
Is there some default password that Ubuntu gives the root? Is there any way to find it or am I going to have to do a complete reinstall?
5. When using the synaptic package manager, no matter what I do it gives me the error message "E: msttcorefonts:subprocess post-installation script returned error exit status 1" and I cannot uninstall it. It turns dark red. I cannot remove msttcorefonts.
Any help on any of these issues would really be appreciated. Thanks

---

### Post by stalker145 on 2008-01-14
> **alonge said:**
> I actually have a few issues after installation:
1. When putting a DVD in the DVD player Totem movie player pops up and tells me "An Error occurred, could not read from resource" GStreamer is all enabled.
2. I am unable to view any movie clips on firefox. I subscribe to Blockbuster and watch the movie trailers, but am unable to do so with linux.
3. The OS was installed and I went into the Synaptic package manager and added packages and only ones that had the Ubuntu image next to them. Now when the OS boots up, first it says kubuntu, then a screen comes up that says Edubuntu and that is where I have to put in my user and pass.
I originally just installed Ubuntu (Gutsy). Doees this matter?
4. (Biggest Problem) When I go to the terminal and su root it won't accept the password I used when I first did the installation. I was only prompted for one password during installation and that one works for everything when I am in the OS.
Is there some default password that Ubuntu gives the root? Is there any way to find it or am I going to have to do a complete reinstall?
5. When using the synaptic package manager, no matter what I do it gives me the error message "E: msttcorefonts:subprocess post-installation script returned error exit status 1" and I cannot uninstall it. It turns dark red. I cannot remove msttcorefonts.
Any help on any of these issues would really be appreciated. Thanks

1 - Does your DVD happen to be dual layer, blu-ray, or something odd and your DVD player is a simple DVD? Are all of your cables connected tightly and properly?
I'm really not sure about this one, but this is where I would start.

 2 - Have you enabled "Ubuntu Restricted Extras" and the flash plugin for Mozilla/FireFox in the Add/Remove application?

3 - No problem here. You just have a ton of extra apps installed. Each desktop (U/K/E/Xubuntu) each have their own splash and login screens. When you installed all of the extra packages, one of the other DM's (Desktop Manager) just took over.

4 - By "won't accept the password", do you mean you can't see the cursor moving (which is normal behavior) or do you mean you type the password and it fails?

5 - Sorry, no idea.

---

### Post by alonge on 2008-01-14
My DVD player is a pretty old one, so perhaps that is the problem with that.
I have enabled the Ubuntu Restricted Extras. The flash plugin is added and is working great in Firefox.
At the terminal when I su root and it asks for the password, I put in the only password that I put in during installation and it says, "authentication failure" "sorry"
There are things I won't be able to access without being root. Even the Adept manager won't let me check for updates or much else without being logged in as root.
Many many years ago, I took a unix class and I remember he taught us how to reload the OS without the GUI and that we could change the password there, but I'll be darned if I remember what to do.
Gosh, I sure hope I don't have to go through and reinstall the OS and all the packages again. 
Since I have taken that course, I have not used this at all, so I am actually just a newbie. Thanks for your help.

---

### Post by kostkon on 2008-01-14
> **alonge said:**
> I actually have a few issues after installation:
1. When putting a DVD in the DVD player Totem movie player pops up and tells me "An Error occurred, could not read from resource" GStreamer is all enabled.
2. I am unable to view any movie clips on firefox. I subscribe to Blockbuster and watch the movie trailers, but am unable to do so with linux.
3. The OS was installed and I went into the Synaptic package manager and added packages and only ones that had the Ubuntu image next to them. Now when the OS boots up, first it says kubuntu, then a screen comes up that says Edubuntu and that is where I have to put in my user and pass.
I originally just installed Ubuntu (Gutsy). Doees this matter?
4. (Biggest Problem) When I go to the terminal and su root it won't accept the password I used when I first did the installation. I was only prompted for one password during installation and that one works for everything when I am in the OS.
Is there some default password that Ubuntu gives the root? Is there any way to find it or am I going to have to do a complete reinstall?
5. When using the synaptic package manager, no matter what I do it gives me the error message "E: msttcorefonts:subprocess post-installation script returned error exit status 1" and I cannot uninstall it. It turns dark red. I cannot remove msttcorefonts.
Any help on any of these issues would really be appreciated. Thanks

1. You have to enable DVD support in Ubuntu. Please read [this documentation]("https://help.ubuntu.com/community/RestrictedFormats") or in a simpler form [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability").

2. Again, please read the [*Restricted Formats* documentation]("https://help.ubuntu.com/community/RestrictedFormats") on how to add support for *Quicktime*, *Windows Media* and other formats.

3. I don't know if this is normal, as *stalker145* says. You may have installed the desktop packages  of other environments and your system for some reason got messed up a little. Did you plan to install *Kubuntu* and *Edubuntu* or it happened by chance?

4. Please read [this]("https://help.ubuntu.com/community/RootSudo").

5. It seems that for some reason the installation of *msttcorefonts* was interrupted. Do this: open a terminal and give
```
sudo dpkg --configure -a
```
and see if this will fix your problem.

---

### Post by alonge on 2008-01-14
I first did sudo dpkg --configure -a
didn't give me any error messages.
I then did what I am copying to this screen and you can see the progression of what happened. Unfortunately I just got paged in to work, so have to leave right away. But if you can look at what it says, perhaps it will shed some light on it. This is all I've done so far.
Thanks.

[sudo] password for barbara:
barbara@backroom:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  liborbit2-dev libsm-dev krec kscd libice-dev libaspell-dev libgnutlsxx13
  libflite1 kmrml libtasn1-3-dev libatk1.0-dev libaudio-dev libgpg-error-dev
  libjasper-dev x11proto-xinerama-dev comerr-dev libopencdk8-dev
  libhal-storage-dev x11proto-render-dev libgcrypt11-dev libxi-dev
  libxmu-headers libxrender-dev mesa-common-dev libgnome-keyring-dev ksirc
  libkrb5-dev qt3-dev-tools kpovmodeler libstartup-notification0-dev
  libldap2-dev libcucul-dev libsamplerate0-dev x11proto-record-dev
  x11proto-composite-dev intltool libxcursor-dev lua50 libpth-dev kview
  libapt-pkg-dev libgnutls-dev libspeex-dev x11proto-randr-dev gjdoc hspell
  x11proto-damage-dev libxt-dev libxmu-dev libxdamage-dev libraw1394-dev
  libtiff4-dev libidl-dev libart-2.0-dev libmad0-dev x11proto-fixes-dev
  libdbus-glib-1-dev libqt3-headers libxcomposite-dev libhal-dev libmpfr1ldbl
  libtiffxx0c2 liblcms1-dev liblzo2-dev libxrandr-dev libkadm55 libpurple-dev
  libselinux1-dev libartsc0-dev libxfixes-dev libavutil-dev libxinerama-dev
  libsepol1-dev libgsm1-dev kdesdk-scripts cpp-4.1-doc libxtst-dev gettext-kde
  libidn11-dev kmid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
barbara@backroom:~$

---

### Post by kostkon on 2008-01-14
> **alonge said:**
> I first did sudo dpkg --configure -a
didn't give me any error messages.
I then did what I am copying to this screen and you can see the progression of what happened. Unfortunately I just got paged in to work, so have to leave right away. But if you can look at what it says, perhaps it will shed some light on it. This is all I've done so far.
Thanks.

[sudo] password for barbara:
barbara@backroom:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  liborbit2-dev libsm-dev krec kscd libice-dev libaspell-dev libgnutlsxx13
  libflite1 kmrml libtasn1-3-dev libatk1.0-dev libaudio-dev libgpg-error-dev
  libjasper-dev x11proto-xinerama-dev comerr-dev libopencdk8-dev
  libhal-storage-dev x11proto-render-dev libgcrypt11-dev libxi-dev
  libxmu-headers libxrender-dev mesa-common-dev libgnome-keyring-dev ksirc
  libkrb5-dev qt3-dev-tools kpovmodeler libstartup-notification0-dev
  libldap2-dev libcucul-dev libsamplerate0-dev x11proto-record-dev
  x11proto-composite-dev intltool libxcursor-dev lua50 libpth-dev kview
  libapt-pkg-dev libgnutls-dev libspeex-dev x11proto-randr-dev gjdoc hspell
  x11proto-damage-dev libxt-dev libxmu-dev libxdamage-dev libraw1394-dev
  libtiff4-dev libidl-dev libart-2.0-dev libmad0-dev x11proto-fixes-dev
  libdbus-glib-1-dev libqt3-headers libxcomposite-dev libhal-dev libmpfr1ldbl
  libtiffxx0c2 liblcms1-dev liblzo2-dev libxrandr-dev libkadm55 libpurple-dev
  libselinux1-dev libartsc0-dev libxfixes-dev libavutil-dev libxinerama-dev
  libsepol1-dev libgsm1-dev kdesdk-scripts cpp-4.1-doc libxtst-dev gettext-kde
  libidn11-dev kmid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
barbara@backroom:~$

Please, go to *System -> Preferences -> Network Proxy* and check if the option *Direct internet connection* is selected. If it is not, select it, then do again a
```
sudo dpkg --configure -a
```
and try again to install this package.

---

