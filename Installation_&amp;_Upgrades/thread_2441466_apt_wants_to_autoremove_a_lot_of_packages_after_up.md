---
title: "apt wants to autoremove a lot of packages after upgrade 19.10-&gt;20.04"
date: 2020-04-23
forum: Installation &amp; Upgrades
---

### Post by encyclopedist on 2020-04-23
I have just upgraded my main laptop from 19.10 to 20.04 and after reboot when I do `sudo apt full-upgrade` is shows this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  aglfn dh-python enchant engauge-digitizer-doc epiphany-browser-data geoip-database gir1.2-gtop-2.0 gir1.2-handy-0.0
  gir1.2-harfbuzz-0.0 gmsh-doc gnome-software-common gnuplot-data libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libapt-pkg5.90 libasound2-dev libatk-bridge2.0-dev libatk1.0-dev libatspi2.0-dev
  libavresample4 libbind9-161 libbrlapi0.6 libbtparse1 libcodec2-0.8.1 libdatrie-dev libdbus-1-dev libdc1394-22
  libdca0 libdmapsharing-3.0-2 libdns1104 libdns1109 libdrm-dev libdvdnav4 libdvdread7 libenchant1c2a libept1.5.90
  libevent-2.1-6 libevent-core-2.1-6 libevent-pthreads-2.1-6 libexiv2-14 libfaad2 libfam0 libflickcurl0
  libfltk-images1.3 libfltk1.3 libfprint0 libfribidi-dev libgeoip1 libgeos-3.7.2 libgit2-27 libgles1
  libgnome-desktop-3-18 libgpod-common libgpod4 libgraphite2-dev libgstreamer-plugins-bad1.0-0 libgupnp-igd-1.0-4
  libharfbuzz-dev libharfbuzz-gobject0 libhwloc5 libibus-1.0-dev libicu63 libilmbase23 libirs161 libisc1100 libisc1105
  libisccc161 libisccfg163 libisl21 libjs-sphinxdoc libjs-underscore libkf5auth-data libkf5codecs-data libkf5codecs5
  libkf5config-data libkf5configcore5 libkf5configgui5 libkf5coreaddons-data libkf5coreaddons5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5guiaddons5 libkf5i18n-data libkf5iconthemes-data libkf5itemviews-data
  libkf5service-data libkf5wallet-data libkf5widgetsaddons-data libkf5windowsystem-data liblirc-client0 liblog4cpp5v5
  liblua5.2-0 liblwres161 libmircookie-dev libmircookie2 libmircore-dev libmirprotobuf3 libmjpegutils-2.1-0 libmms0
  libmozjs-60-0 libmpcdec6 libmplex2-2.1-0 libmypaint-1.3-0 libmysofa0 libnetcdf13 libnfs12 libnice10 liboauth0
  libobjc-8-dev libomp-9-dev libomp5-9 libopenal-data libopenal1 libopenblas-base libopenexr23 libopengl-dev
  libpango1.0-dev libplymouth4 libpoppler-qt5-1 libpoppler90 libprotobuf-dev libprotobuf-lite17 libpulse-dev
  libpython2-dev libpython2.7 libpython2.7-dev libpython3.7-minimal libqpdf21 libqt5sql5 libqt5sql5-sqlite
  libqt5texttospeech5 libqt5waylandclient5 libqt5xmlpatterns5 libsgutils2-2 libsndio-dev libsndio7.0 libsoundtouch1
  libspandsp2 libsrt1 libsrtp2-1 libthai-dev libudev-dev libusbmuxd4 libusrsctp1 libva-wayland2 libvigraimpex6
  libvo-aacenc0 libwayland-bin libwayland-dev libwildmidi2 libx11-xcb-dev libxcb-dri2-0-dev libxcb-dri3-dev
  libxcb-glx0-dev libxcb-randr0-dev libxcb-shape0-dev libxcb-sync-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxkbcommon-dev libxrandr-dev libxss-dev libxt-dev libxtst-dev
  libxv-dev libxxf86vm-dev libxxhash0 libzbar0 linux-headers-5.3.0-45 linux-headers-5.3.0-45-generic
  linux-modules-5.3.0-45-generic linux-tools-5.3.0-45 linux-tools-5.3.0-45-generic llvm-9-tools pango1.0-tools
  python-asn1crypto python-certifi python-configparser python-decorator python-idna python-ipython-genutils
  python-matplotlib2-data python-pathlib2 python-pexpect python-ptyprocess python-pyparsing python-scandir
  python-subprocess32 python-tz python-wcwidth python-yaml python3-asn1crypto python3-mako python3-markupsafe
  python3-pyside2uic python3-pyxattr python3-scour python3.7-minimal rdesktop rtmpdump ruby-did-you-mean scour
  ubuntu-system-service ubuntu-web-launchers wayland-protocols x11proto-composite-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-randr-dev x11proto-record-dev x11proto-scrnsaver-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev youtube-dl
Use 'sudo apt autoremove' to remove them.

```

These seems to be some essential packages, so I am hesitant to remove them. Shall I remove then or there is something wrong with my setup? For example, was some important metapackage removed during upgrade?

---

### Post by mörgæs on 2020-04-23
Hi, welcome to the fora.

Now you see why many people recommend a clean install over an upgrade. So many small steps could go wrong and I don't have a foundation for telling if all of the packages above can safely be purged. On the other hand they must go if they are not supported any more. 

Always update, never upgrade.

---

### Post by encyclopedist on 2020-04-24
At the time I did not have a USB drive at hand to do a clean reinstall, but later I found one and did a reinstall. Now everything is working fine, only I had to spend time installing all the necessary software.

---

### Post by TheFu on 2020-04-24
> **encyclopedist said:**
> At the time I did not have a USB drive at hand to do a clean reinstall, but later I found one and did a reinstall. Now everything is working fine, only I had to spend time installing all the necessary software.

For people trying to make this as painless as possible to get all the previously installed software back, we can save a list of manually installed packages BEFORE we begin using:
```
$ apt-mark showmanual | tee /tmp/pkgs_manual.lst
```

Backup that list to a flash drive or where ever won't be touched by the fresh install. Backup our important files and settings, those are usually in $HOME and /etc/ ... also to disconnected storage.  Assume any connected disks will be wiped during a fresh install because accidents happen. Better safe than sorry.

Do a fresh install that formats the OS and any other areas we'd like.  At the 2nd boot, connect the "backup storage" from before and copy all the HOME back to a subdirectory under our HOME so we can carefully move stuff back.  Data should be fine, quick and easy.  Settings in ~/.config/ and ~/.local/ probably need more care.

Restore the system settings selectively into /etc/.  DO NOT just blindly copy them in overwriting the freshly installed settings.  But it is nice to have any old firewall rules, custom fail2ban jail settings, custom sudoers or configs from other system processes.  Under /etc/ any files with .local at the end should probably be compared to any freshly installed versions. The system admin should know which files have been touched.

And lastly, take the list of manually installed packages, feed that into 
```
sudo apt-mark manual $(cat /tmp/pkgs_manual.lst) # <--- assuming you copied the file back to /tmp/
sudo apt-get -u dselect-upgrade
sudo apt install -f

```
That will install those packages if they are missing from the current install.  Takes just a few minutes to do these things, probably saving us hours of trying to recall which software we previously installed.  OF course, if you install a bunch of software to try out, but don't remove it, then doing this will just end with a cluttered system. A fresh install is a good time to change that behavior.

---

