---
title: "Software Updater: Partial upgrade remove Gnome Display Manager"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by tome74 on 2023-08-04
Ubuntu 22.04.2 LTS. 

Run Software Updater to update to the 6.2 kernel HWE. Software Update suggest a Partial Upgrade, which proceed to remove Gnome Display Manager.

[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292561&d=1691148706[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=292561&d=1691148706")

Reboot, and system startup in command line prompt.#-o

Had to re-install gdm3 to get back into GUI mode again.

Note: instead of using Software Updater, running 'sudo apt upgrade' from command line doesn't remove gdm3.

---

### Post by countingbricks on 2023-08-04
I had a similar experience but rolled back with Timeshift. I am also only using 'apt update' for now as it never removes packages, unlike 'apt full-upgrade' that will remove packages if it needs to in order to upgrade others. No idea what is causing it.

'nala upgrade' currently gives the following. (same as 'apt full-upgrade' but more readable)
```
===================================================================================================================================================================================================================
 Installing                                                                                                                                                                                                        
===================================================================================================================================================================================================================
  Package:                                                              Version:                                                                                                                            Size:  
  libqt5gui5-gles                                                       5.15.3+dfsg-1                                                                                                                      3.7 MB  
  notification-daemon                                                   3.20.0-4build1                                                                                                                      58 KB  
  policykit-1-gnome                                                     0.105-7ubuntu3                                                                                                                      26 KB  
                                                                                                                                                                                                                   
===================================================================================================================================================================================================================
 Kept Back, Will Not Be Upgraded                                                                                                                                                                                   
===================================================================================================================================================================================================================
  Package:                                                              Old Version:                                   New Version:                                                                         Size:  
  base-files                                                            12ubuntu4.3                                    12ubuntu4.4                                                                         403 KB  
  distro-info                                                           1.1build1                                      1.1ubuntu0.1                                                                         71 KB  
  gjs                                                                   1.72.2-0ubuntu2                                1.72.4-0ubuntu0.22.04.1                                                             195 KB  
  gnome-remote-desktop                                                  42.4-0ubuntu1                                  42.7-0ubuntu1                                                                       483 KB  
  language-pack-af                                                      1:22.04+20230209                               1:22.04+20230801                                                                      9 KB  
  language-pack-af-base                                                 1:22.04+20230209                               1:22.04+20230801                                                                    3.5 MB  
  language-pack-en                                                      1:22.04+20230209                               1:22.04+20230801                                                                      9 KB  
  language-pack-en-base                                                 1:22.04+20230209                               1:22.04+20230801                                                                    3.8 MB  
  language-pack-gnome-af                                                1:22.04+20230209                               1:22.04+20230801                                                                      9 KB  
  language-pack-gnome-af-base                                           1:22.04+20230209                               1:22.04+20230801                                                                    4.5 MB  
  language-pack-gnome-en                                                1:22.04+20230209                               1:22.04+20230801                                                                      9 KB  
  language-pack-gnome-en-base                                           1:22.04+20230209                               1:22.04+20230801                                                                    3.6 MB  
  libegl-mesa0                                                          22.2.5-0ubuntu0.1~22.04.3                      23.0.4-0ubuntu1~22.04.1                                                             381 KB  
  libgbm1                                                               22.2.5-0ubuntu0.1~22.04.3                      23.0.4-0ubuntu1~22.04.1                                                             151 KB  
  libgjs0g                                                              1.72.2-0ubuntu2                                1.72.4-0ubuntu0.22.04.1                                                             1.4 MB  
  libgl1-amber-dri                                                      21.3.7-0ubuntu1                                21.3.9-0ubuntu1~22.04.1                                                            16.0 MB  
  libgl1-mesa-dri                                                       22.2.5-0ubuntu0.1~22.04.3                      23.0.4-0ubuntu1~22.04.1                                                            30.3 MB  
  libglapi-mesa                                                         22.2.5-0ubuntu0.1~22.04.3                      23.0.4-0ubuntu1~22.04.1                                                             315 KB  
  libglx-mesa0                                                          22.2.5-0ubuntu0.1~22.04.3                      23.0.4-0ubuntu1~22.04.1                                                             580 KB  
  libunwind8                                                            1.3.2-2build2                                  1.3.2-2build2.1                                                                     201 KB  
  python3-distro-info                                                   1.1build1                                      1.1ubuntu0.1                                                                         36 KB  
  python3-distupgrade                                                   1:22.04.16                                     1:22.04.17                                                                          653 KB  
  ubuntu-release-upgrader-core                                          1:22.04.16                                     1:22.04.17                                                                          348 KB  
  ubuntu-release-upgrader-gtk                                           1:22.04.16                                     1:22.04.17                                                                          217 KB  
                                                                                                                                                                                                                   
===================================================================================================================================================================================================================
 Auto-Removing                                                                                                                                                                                                     
===================================================================================================================================================================================================================
  Package:                                                              Version:                                                                                                                            Size:  
  advancecomp                                                           2.1-2.1ubuntu2.1                                                                                                                   631 KB  
  apturl                                                                0.5.2ubuntu22                                                                                                                       56 KB  
  apturl-common                                                         0.5.2ubuntu22                                                                                                                      172 KB  
  gir1.2-accountsservice-1.0                                            22.07.5-2ubuntu1.4                                                                                                                  34 KB  
  gir1.2-adw-1                                                          1.1.7-0ubuntu0.22.04.1                                                                                                             110 KB  
  gir1.2-gck-1                                                          3.40.0-4                                                                                                                            60 KB  
  gir1.2-gcr-3                                                          3.40.0-4                                                                                                                            81 KB  
  gir1.2-gdm-1.0                                                        42.0-1ubuntu7.22.04.3                                                                                                              109 KB  
  gir1.2-geoclue-2.0                                                    2.5.7-3ubuntu3                                                                                                                      46 KB  
  gir1.2-gnomebluetooth-3.0                                             42.0-5                                                                                                                              28 KB  
  gir1.2-graphene-1.0                                                   1.10.8-1                                                                                                                            53 KB  
  gir1.2-gtk-4.0                                                        4.6.9+ds-0ubuntu0.22.04.1                                                                                                          898 KB  
  gir1.2-gweather-3.0                                                   40.0-5build1                                                                                                                        42 KB  
  gir1.2-nma-1.0                                                        1.8.34-1ubuntu1                                                                                                                     30 KB  
  gir1.2-upowerglib-1.0                                                 0.99.17-1                                                                                                                           36 KB  
  gnome-bluetooth-3-common                                              42.0-5                                                                                                                             1.0 MB  
  gnome-session-common                                                  42.0-1ubuntu2                                                                                                                      238 KB  
  gnome-shell-pomodoro-data                                             0.20.0-3                                                                                                                           6.4 MB  
  gstreamer1.0-pipewire                                                 0.3.48-1ubuntu3                                                                                                                    154 KB  
  jpegoptim                                                             1.4.6-1                                                                                                                             60 KB  
  libgnome-bluetooth-3.0-13                                             42.0-5                                                                                                                             155 KB  
  libpoppler-qt5-1                                                      22.02.0-2ubuntu0.2                                                                                                                 642 KB  
  libqt5sql5                                                            5.15.3+dfsg-2ubuntu0.2                                                                                                             477 KB  
  libqt5sql5-sqlite                                                     5.15.3+dfsg-2ubuntu0.2                                                                                                             263 KB  
  libqt5test5                                                           5.15.3+dfsg-2ubuntu0.2                                                                                                             539 KB  
  libqt5x11extras5                                                      5.15.3-1                                                                                                                            49 KB  
  libqt5xml5                                                            5.15.3+dfsg-2ubuntu0.2                                                                                                             489 KB  
  libxatracker2                                                         23.0.4-0ubuntu1~22.04.1                                                                                                            8.2 MB  
  libxcb-xv0                                                            1.14-3ubuntu3                                                                                                                       61 KB  
  libxcvt0                                                              0.1.1-3                                                                                                                             32 KB  
  libxfont2                                                             1:2.0.5-1build1                                                                                                                    214 KB  
  libxvmc1                                                              2:1.0.12-2build2                                                                                                                    66 KB  
  linux-headers-5.19.0-46-generic                                       5.19.0-46.47~22.04.1                                                                                                              28.1 MB  
  linux-hwe-5.19-headers-5.19.0-46                                      5.19.0-46.47~22.04.1                                                                                                              80.0 MB  
  linux-image-5.19.0-46-generic                                         5.19.0-46.47~22.04.1                                                                                                              12.3 MB  
  linux-modules-5.19.0-46-generic                                       5.19.0-46.47~22.04.1                                                                                                             164.8 MB  
  linux-modules-extra-5.19.0-46-generic                                 5.19.0-46.47~22.04.1                                                                                                             454.6 MB  
  luckybackup-data                                                      0.5.0-5                                                                                                                           13.5 MB  
  optipng                                                               0.7.7-2build1                                                                                                                      188 KB  
  pngcrush                                                              1.8.13-0.1                                                                                                                         143 KB  
  python3-pyqt5.sip                                                     12.9.1-1build1                                                                                                                     178 KB  
  switcheroo-control                                                    2.4-3build2                                                                                                                         93 KB  
  x11-apps                                                              7.7+8build2                                                                                                                        2.5 MB  
  x11-session-utils                                                     7.7+4build2                                                                                                                        239 KB  
  xbitmaps                                                              1.1.1-2.1ubuntu1                                                                                                                   248 KB  
  xcvt                                                                  0.1.1-3                                                                                                                             30 KB  
  xfonts-base                                                           1:1.0.5                                                                                                                            7.3 MB  
  xfonts-encodings                                                      1:1.0.5-0ubuntu2                                                                                                                   680 KB  
  xfonts-scalable                                                       1:1.0.3-1.2ubuntu1                                                                                                                 478 KB  
  xfonts-utils                                                          1:7.7+6build2                                                                                                                      444 KB  
  xinit                                                                 1.4.1-0ubuntu4                                                                                                                      63 KB  
  xinput                                                                1.6.3-1build2                                                                                                                       84 KB  
  xserver-common                                                        2:21.1.4-2ubuntu1.7~22.04.1                                                                                                        247 KB  
  xserver-xephyr                                                        2:21.1.4-2ubuntu1.7~22.04.1                                                                                                        2.7 MB  
  xserver-xorg-legacy                                                   2:21.1.4-2ubuntu1.7~22.04.1                                                                                                        279 KB  
  xwayland                                                              2:22.1.1-1ubuntu0.6                                                                                                                2.3 MB  
                                                                                                                                                                                                                   
===================================================================================================================================================================================================================
 Removing                                                                                                                                                                                                          
===================================================================================================================================================================================================================
  Package:                                                              Version:                                                                                                                            Size:  
  chrome-gnome-shell                                                    10.1-5                                                                                                                              75 KB  
  diffpdf                                                               2.1.3.1-2                                                                                                                          570 KB  
  gdm3                                                                  42.0-1ubuntu7.22.04.3                                                                                                              1.9 MB  
  gir1.2-mutter-10                                                      42.9-0ubuntu4                                                                                                                      561 KB  
  gnome-session-bin                                                     42.0-1ubuntu2                                                                                                                      499 KB  
  gnome-shell                                                           42.9-0ubuntu2                                                                                                                      4.0 MB  
  gnome-shell-extension-appindicator                                    42-2~fakesync1                                                                                                                     262 KB  
  gnome-shell-extension-desktop-icons-ng                                43-2ubuntu1                                                                                                                        442 KB  
  gnome-shell-extension-prefs                                           42.9-0ubuntu2                                                                                                                       91 KB  
  gnome-shell-extension-ubuntu-dock                                     72~ubuntu5.22.04.2.1                                                                                                               750 KB  
  gnome-shell-extensions                                                42.1-0ubuntu1                                                                                                                      1.2 MB  
  gnome-shell-pomodoro                                                  0.20.0-3                                                                                                                           735 KB  
  gnome-startup-applications                                            42.0-1ubuntu2                                                                                                                      186 KB  
  hplip-gui                                                             3.21.12+dfsg0-1                                                                                                                    150 KB  
  libqt5designer5                                                       5.15.3-1                                                                                                                           5.6 MB  
  libqt5gui5                                                            5.15.3+dfsg-2ubuntu0.2                                                                                                            13.1 MB  
  libqt5help5                                                           5.15.3-1                                                                                                                           563 KB  
  libqt5opengl5                                                         5.15.3+dfsg-2ubuntu0.2                                                                                                             604 KB  
  libqt5printsupport5                                                   5.15.3+dfsg-2ubuntu0.2                                                                                                             792 KB  
  libqt5svg5                                                            5.15.3-1                                                                                                                           509 KB  
  libqt5widgets5                                                        5.15.3+dfsg-2ubuntu0.2                                                                                                             7.7 MB  
  luckybackup                                                           0.5.0-5                                                                                                                            1.3 MB  
  nautilus-share                                                        0.7.3-2ubuntu6                                                                                                                     143 KB  
  python3-pyqt5                                                         5.15.6+dfsg-1ubuntu3                                                                                                              16.5 MB  
  trimage                                                               1.0.6-1                                                                                                                            100 KB  
  ubuntu-desktop                                                        1.481.1                                                                                                                             54 KB  
  ubuntu-desktop-minimal                                                1.481.1                                                                                                                             54 KB  
  ubuntu-session                                                        42.0-1ubuntu2                                                                                                                       82 KB  
  virtualbox-qt                                                         6.1.38-dfsg-3~ubuntu1.22.04.1                                                                                                     60.1 MB  
  xorg                                                                  1:7.7+23ubuntu2                                                                                                                     54 KB  
  xserver-xorg                                                          1:7.7+23ubuntu2                                                                                                                    375 KB  
  xserver-xorg-core                                                     2:21.1.4-2ubuntu1.7~22.04.1                                                                                                        4.1 MB  
  xserver-xorg-input-all                                                1:7.7+23ubuntu2                                                                                                                     48 KB  
  xserver-xorg-input-libinput                                           1.2.1-1                                                                                                                            118 KB  
  xserver-xorg-input-wacom                                              1:1.0.0-3ubuntu1                                                                                                                   304 KB  
  xserver-xorg-video-all                                                1:7.7+23ubuntu2                                                                                                                     48 KB  
  xserver-xorg-video-amdgpu                                             22.0.0-1ubuntu0.1                                                                                                                  193 KB  
  xserver-xorg-video-ati                                                1:19.1.0-2ubuntu1                                                                                                                   51 KB  
  xserver-xorg-video-fbdev                                              1:0.5.0-2build1                                                                                                                     56 KB  
  xserver-xorg-video-intel                                              2:2.99.917+git20210115-1                                                                                                           3.3 MB  
  xserver-xorg-video-nouveau                                            1:1.0.17-2build1                                                                                                                   274 KB  
  xserver-xorg-video-qxl                                                0.1.5+git20200331-3                                                                                                                195 KB  
  xserver-xorg-video-radeon                                             1:19.1.0-2ubuntu1                                                                                                                  539 KB  
  xserver-xorg-video-vesa                                               1:2.5.0-1build4                                                                                                                     55 KB  
  xserver-xorg-video-vmware                                             1:13.3.0-3build1                                                                                                                   212 KB  
                                                                                                                                                                                                                   
===================================================================================================================================================================================================================
 Summary                                                                                                                                                                                                           
===================================================================================================================================================================================================================
 Install      3 Packages                                                                                                                                                                                           
 Kept Back   24 Packages                                                                                                                                                                                           
 Auto-Remove 56 Packages                                                                                                                                                                                           
 Remove      45 Packages                                                                                                                                                                                           
                                                                                                                                                                                                                   
 Disk space to free  908.0 MB 
```

---

### Post by ashes00 on 2023-08-04
> **tome74 said:**
> Ubuntu 22.04.2 LTS. 

Run Software Updater to update to the 6.2 kernel HWE. Software Update suggest a Partial Upgrade, which proceed to remove Gnome Display Manager.

Reboot, and system startup in command line prompt.#-o

Had to re-install gdm3 to get back into GUI mode again.

Note: instead of using Software Updater, running 'sudo apt upgrade' from command line doesn't remove gdm3.


I had the exact same problem this morning.  Thankfully I created a TimeShift backup before.  I really hope this is fixed by Canonical soon.  If not then I will have to stay on this old kernel, and that will run out of support at some point.

---

### Post by solid-snail on 2023-08-04
Just got the same issue on a vm, but not on the host.
Have not installed it yet.
Both running 22.04.

---

### Post by scpatl4now on 2023-08-04
I think I had a similar issue.  I had to reinstall ubuntu-desptop to get back to the desktop.  I tried startx first but that returned an error.  I had another thread but it seems prudent to keep it in this thread.  My original post.  Another thing I forgot to mention is that prior to this a little red circle with a white X in it popped up on my taskbar next to the network icon.  It said packages were broken and I needed to run my package manager (which I did and it did nothing to solve it).  The offending package was a google earth installation.  When I ran the update from there thats when the screen blanked 

> I have Ubuntu 22.04 installed and went to do updates this morning. About halfway into installing them my entire screen went blank. I wasn't sure what to do so let it go 15 mins and then restarted. I could only get to command prompt login. I had to reinstall ubuntu-desktop to get back to a normal login screen. It now is trying to get me to remove things via automatic update. I don't think that is wise currently. I had tried booting to previous kernel but same thing before I reinstalled the desktop. The only options were 6.1 and 6.2 when I rebooted. The auto update listed 5.10 to remove?? I really am not trusting the updates being pushed. Is anyone having a similar problem?

---

### Post by ashes00 on 2023-08-04
> **scpatl4now said:**
> I think I had a similar issue.  I had to reinstall ubuntu-desptop to get back to the desktop.  I tried startx first but that returned an error.  I had another thread but it seems prudent to keep it in this thread.  My original post.  Another thing I forgot to mention is that prior to this a little red circle with a white X in it popped up on my taskbar next to the network icon.  It said packages were broken and I needed to run my package manager (which I did and it did nothing to solve it).  The offending package was a google earth installation.  When I ran the update from there thats when the screen blanked

I just installed Ubuntu 22.04.02 Desktop proper (Without applying updates) in Virtualbox with an ISO I had since May 10th 2023.  When I went to do the updates I too got black screen, and had to reset the VM.  Upon start up I had to login with CLI.  I tried to install ubuntu-desktop, but was told there was an error,and I needed to try sudo pkkg --configure -a to fix.  That seemed to setup a bunch of packages.  Then I could install ubuntu-desktop.  Once it was installed it launched the GUI. Reboot landed me at GUI each time afterwards.  I have a feeling there is either a propblem witht he 6.2 kernel thats being installed or the installer is failing, and its causeing a problem.

---

### Post by countingbricks on 2023-08-04
Seems like something got fixed.

'nala upgrade' now only wants to remove the old kernel. I am waiting for Timeshift to finish a backup before trying to update my system.


edit: My update was successful. I recommend you run 'apt update &&  apt full-upgrade --dry-run' to see if the fix has been synced to your mirror.

---

### Post by deadflowr on 2023-08-04
> Note: instead of using Software Updater, running 'sudo apt upgrade' from command line doesn't remove gdm3.
Because apt upgrade will never remove packages.
apt-get dist-upgrade or apt full-upgrade will remove packages if an upgrade requires it.

---

### Post by scpatl4now on 2023-08-04
Updates again was trying to push updates to me.  I looked to see what driver I was running for Nvidia and searched for additional drivers and it said I was running a manually installed driver.  It would not let me change it to any other driver.  So I let the updates run and one of which was to remove Nvidia driver 535.86.05 which is what I should be running...again blank screen so waited a while restarted and when I logged in (it did boot) I was running the Nouveau driver.  So, I went to install 535.  Half way through...blanked out monitor (actually the bluelight on it turned yellow meaning no signal.  Restarted again and when I logged in it looked to finish the update and told me to restart again...this time booted normally.  I wonder if this has something to do with Nvidia drivers???

---

### Post by scpatl4now on 2023-08-04
> **countingbricks said:**
> Seems like something got fixed.

'nala upgrade' now only wants to remove the old kernel. I am waiting for Timeshift to finish a backup before trying to update my system.


edit: My update was successful. I recommend you run 'apt update &&  apt full-upgrade --dry-run' to see if the fix has been synced to your mirror.

When I ran that I got this

```
The following packages were automatically installed and are no longer required:
  audacious-plugins-data audacity-data clang debugedit devhelp-common elfutils
  exuberant-ctags flatpak-builder fonts-open-sans gdal-data gir1.2-dazzle-1.0
  gir1.2-flatpak-1.0 gir1.2-gee-0.8 gir1.2-ggit-1.0 gir1.2-granite-1.0
  gir1.2-jsonrpc-1.0 gir1.2-template-1.0 i965-va-driver:i386
  intel-media-va-driver:i386 libaec0 libaribb24-0 libarmadillo10 libarpack2
  libasm1 libatk-bridge2.0-dev libatk1.0-dev libatspi2.0-dev libaudcore5
  libaudgui5 libaudtag3 libblkid-dev libblosc1 libbrotli-dev libcairo2-dev
  libcddb2 libcfitsio9 libcharls2 libcmark0.30.2 libcrypto++8 libdatrie-dev
  libdbus-1-dev libdc1394-25 libdca0 libdeflate-dev libdmapsharing-3.0-2
  libdvbpsi10 libdvdnav4 libebml5 libebur128-1 libegl-mesa0:i386 libegl1:i386
  libexpat1-dev libfaad2 libflac++6v5 libfluidsynth3 libfontconfig-dev
  libfontconfig1-dev libfreeaptx0 libfreetype-dev libfreetype6-dev libfreexl1
  libfribidi-dev libfyba0 libgdal30 libgdcm3.0 libgdk-pixbuf-2.0-dev
  libgee-0.8-dev libgeos-c1v5 libgeos3.10.2 libgeotiff5 libgit2-1.1
  libgit2-glib-1.0-0 libgladeui-common libgles1 libglib2.0-dev
  libglib2.0-dev-bin libglvnd-core-dev libgmic1 libgpod-common libgpod4
  libgranite-common libgranite6 libgraphicsmagick++-q16-12
  libgraphicsmagick-q16-3 libgraphite2-dev libgstreamer-plugins-bad1.0-0
  libgupnp-igd-1.0-4 libharfbuzz-dev libharfbuzz-gobject0 libhdf4-0-alt
  libhdf5-103-1 libhdf5-hl-100 libhidapi-libusb0 libhttp-parser2.9 libice-dev
  libid3tag0 libigdgmm12:i386 libinstpatch-1.0-2 libixml10 libjbig-dev
  libjpeg-dev libjpeg-turbo8-dev libjpeg8-dev libjsonrpc-glib-1.0-1 libkate1
  libkmlbase1 libkmldom1 libkmlengine1 liblastfm5-1 libldacbt-enc2
  liblirc-client0 libltc11 liblua5.2-0 liblzma-dev libmad0 libmatroska7
  libmbedcrypto7 libmbedtls14 libmbedx509-1 libmd4c0 libminizip1
  libmjpegutils-2.1-0 libmms0 libmodplug1 libmount-dev libmpcdec6
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libmygpo-qt5-1 libmysqlclient21
  libneon27-gnutls libnetcdf19 libnice10 libodbcinst2 libogdi4.1
  libopencv-core4.5d libopencv-imgcodecs4.5d libopencv-imgproc4.5d
  libopencv-videoio4.5d libopengl-dev libopenh264-6 libopenmpt-modplug1
  libopenni2-0 libopusfile0 libpango1.0-dev libpcre16-3 libpcre2-16-0
  libpcre2-dev libpcre2-posix3 libpcre3-dev libpcre32-3 libpcrecpp0v5
  libpixman-1-dev libplacebo192 libpng-dev libpng-tools libportal-gtk3-1
  libportal1 libportmidi0 libportsmf0v5 libpq5 libproj22 libprotobuf-lite23
  libproxy-tools libpthread-stubs0-dev libqhull-r8.0 libqrencode4
  libqt5concurrent5 libqt5core5a libqt5dbus5 libqt5gui5-gles libqt5keychain1
  libqt5multimedia5 libqt5network5 libqt5script5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5x11extras5 libqt5xml5 libresid-builder0c2a librttopo1
  libsdl-image1.2 libsdl1.2debian libselinux1-dev libsepol-dev libsgutils2-2
  libsidplay2 libsidplayfp6 libsm-dev libsocket++1 libsoundtouch1 libspandsp2
  libspatialaudio0 libspatialite7 libsrtp2-1 libssh2-1 libsuil-0-0 libsuperlu5
  libsysprof-4 libsysprof-ui-4 libsz2 libtbb2 libtbbmalloc2
  libtemplate-glib-1.0-0 libtemplate-glib-common libthai-dev libtiff-dev
  libtiffxx5 libtorrent-rasterbar2.0 libupnp13 liburiparser1 libva-wayland2
  libva2:i386 libvala-0.56-0 libvala-0.56-dev libvamp-hostsdk3v5 libvlc-bin
  libvlc5 libvlccore9 libvo-aacenc0 libvo-amrwbenc0 libwayland-bin
  libwayland-dev libwildmidi2 libwxbase3.0-0v5 libx11-dev libxau-dev
  libxcb-composite0 libxcb-render0-dev libxcb-shm0-dev libxcb-xinerama0
  libxcb-xinput0 libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxerces-c3.2 libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxkbcommon-dev libxrandr-dev libxrender-dev libxtst-dev
  libzbar0 libzxingcore1 mesa-va-drivers:i386 meson mysql-common ninja-build
  nvidia-firmware-535-535.54.03 ostree pango1.0-tools proj-bin proj-data
  python3-distutils python3-mako python3-markupsafe python3-mutagen
  python3-pyqt5.sip python3-semantic-version qt5-gtk-platformtheme
  qttranslations5-l10n steam-devices timgm6mb-soundfont unixodbc-common
  uuid-dev va-driver-all:i386 valgrind valgrind-if-available vlc-bin vlc-data
  vlc-l10n vlc-plugin-access-extra vlc-plugin-base vlc-plugin-notify
  vlc-plugin-samba vlc-plugin-video-splitter wayland-protocols x11proto-dev
  xorg-sgml-doctools xtrans-dev zlib1g-dev
Use 'apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libvlc5 libimage-magick-perl vlc-data libvlccore9 imagemagick vlc-bin
  libopusfile0 vlc-l10n libopenexr25 perlmagick libmagick++-6.q16-8
  libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba libavcodec58
  libimage-magick-q16-perl libmagickwand-6.q16-6 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6 vlc-plugin-access-extra
  vlc-plugin-video-splitter libswresample3 imagemagick-6-common libavformat58
  libvlc-bin vlc-plugin-base libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro

```

There are lots of things listed there which even I can tell should not be removed

---

### Post by JustSomeCanuck on 2023-08-04
I second using "sudo apt upgrade" as the safest option. I ran it a couple of hours ago with no issues. Just my two cents worth.

---

### Post by ajgreeny on 2023-08-05
There was a very similar problem yesterday, Friday August 4th in Xubuntu 22.04 where a large number of GUI application packages were listed to be removed by the **sudo apt full-upgrade**command.
I aborted and ran **sudo apt upgrade** with no problem so I assume this was a once only glitch that will be sorted very soon.
It's certainly not a problem I've seen before.

---

### Post by ajgreeny on 2023-08-05
It looks as if the problem, whatever it was, may now have been overcome.

I have just run the ***sudo apt full-upgrade*** command again this morning and everything worked as it should have done without the continued removal of most of the GUI which happened last night even after I had run the ***sudo apt upgrade*** command and rebooting.

Something has obviously changed overnight.

---

### Post by tome74 on 2023-08-05
> **ajgreeny said:**
> It looks as if the problem, whatever it was, may now have been overcome.

I have just run the ***sudo apt full-upgrade*** command again this morning and everything worked as it should have done without the continued removal of most of the GUI which happened last night even after I had run the ***sudo apt upgrade*** command and rebooting.

Something has obviously changed overnight.

Yes, I can confirm this is also working properly now with Software Updater. :P

---

### Post by solid-snail on 2023-08-05
For me apt update didn't resolve it. Still asking to remove ubuntu-desktop.

---

### Post by rahavd on 2023-08-05
I think that this is a general problem [https://askubuntu.com/q/1481093/1349180](https://askubuntu.com/q/1481093/1349180) because I installed Ubuntu 22.04 LTS, from the same Ubuntu `.iso` that gave me zero problems in the past. Prior installation from this USB drive worked flawlessly for a long time.

It is a vicious cycle, even on purely new Ubuntu with nothing else installed on it. Installing Ubuntu, since Friday 4 August, ends up with an OS that asserts immediately upon boot: '[COLOR=#525960][FONT=-apple-system]Error: Marking the upgrade (E:Unable to correct problems, you have held broken packages.)', and if I run

[/FONT][/COLOR]```
sudo apt update
sudo apt upgrade

```

I end up with no GUI.

---

### Post by rahavd on 2023-08-05
What exactly did you run and in what order? When I ran
```

sudo apt full-upgrade

```
I get: E: Unable to correct problems, you have held broken packages.

This is on a freshly installed Ubuntu 22.04, so nothing should be broken.

---

### Post by ajgreeny on 2023-08-05
> **rahavd said:**
> What exactly did you run and in what order? When I ran
```

sudo apt full-upgrade

```
I get: E: Unable to correct problems, you have held broken packages.

This is on a freshly installed Ubuntu 22.04, so nothing should be broken.
That was exactly what I saw yesterday evening (Friday 4 Aug, 22:00hrs UTC) on my Xubuntu 22.04 when using the ***full-upgrade*** command so I tried the simpler ***upgrade*** command and all was fine.
I rebooted and again tried the ***full-upgrade*** command and still got the notification that much of the GUI would be removed so, of course, I aborted the action.

This morning at about 10:30hrs UTC I tried the ***full upgrade*** command a third time and all went fine as normal.

So, something must have changed but what it was, I have absolutely no idea.

---

### Post by ajgreeny on 2023-08-05
> **solid-snail said:**
> For me apt update didn't resolve it. Still asking to remove ubuntu-desktop.
Doing only that will never solve anything, all it does is refresh the package list; in order to overcome the problem it was necessary to run ```
sudo apt update
sudo apt upgrade
``` ie, without the full-upgrade.

This morning, as I said above, running the ***full-upgrade*** command was again fault free, as it had always been in the past since I installed 22.04.

---

### Post by ian-weisser on 2023-08-05
Possible bug report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262)

---

### Post by ishmaeljx on 2023-08-05
[COLOR=#000000][FONT=&quot]I suspect this is due to something being terribly wrong with apt's phased updates.
You can try disabling it like this:

[/FONT][/COLOR][COLOR=#000000][FONT=&quot]echo 'APT::Get:[/FONT][/COLOR][COLOR=#000000][FONT=&quot]:Always-[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Include-[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Phased-[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Updates "1";' | sudo tee -a /etc/apt/[/FONT][/COLOR][COLOR=#000000][FONT=&quot]apt.conf.[/FONT][/COLOR][COLOR=#000000][FONT=&quot]d/999phased-[/FONT][/COLOR][COLOR=#000000][FONT=&quot]updates >/dev/null[/FONT][/COLOR]

---

### Post by ian-weisser on 2023-08-05
Something "wrong with phased updates" would NOT cause a Partial Upgrade.

EDIT: I withdraw this comment. Others have shown that i was wrong, and I listened.

---

### Post by ishmaeljx on 2023-08-05
> **ian-weisser said:**
> Something "wrong with phased updates" would NOT cause a Partial Upgrade.

A problem with Phased Updates would merely delay (or accelerate) when you receive packages. It would not affect the contents of those packages, or the apt solver, in the slightest.

On the other hand, a bad package that causes a Partial Upgrade might indeed by caught by Phased Updates before it reaches you (not in this case, of course). On balance, Phased Updates is a good idea.

All I can tell you is that turning off phased updates using the suggestion I made above fixed the issue for me in which apt wanted to autoremove a ton of packages for me.
My suspicion is that some major dependencies changed from one package to another in 22.04.3, and the new package(s) having the updated dependencies is being held back by apt as a phased update.
Hence why turning it off fixed the problem.

---

### Post by Geoffrey_Arndt on 2023-08-06
Well . . . I wish I'd known more about this faulty update before I tried to to run the standard updater gui.    It's 2am now here is Nebraska so am going to bed and will ask wife (her computer) to run Chromebook until I can figure out how to get a gui back.  Any tips on how to do that from a tty login prompt are appreciated.

---

### Post by ian-weisser on 2023-08-06
> **ishmaeljx said:**
> All I can tell you is that turning off phased updates using the suggestion I made above fixed the issue for me

Please add that information to the above-linked bug report.

---

### Post by ajgreeny on 2023-08-06
Added my comments to that linked bug.

---

### Post by makitso on 2023-08-06
This same thing happened with Ubuntu Budgie, the budgie desktop was removed.

---

### Post by gymbo2 on 2023-08-06
> **Geoffrey_Arndt said:**
> Well . . . I wish I'd known more about this faulty update before I tried to to run the standard updater gui.    It's 2am now here is Nebraska so am going to bed and will ask wife (her computer) to run Chromebook until I can figure out how to get a gui back.  Any tips on how to do that from a tty login prompt are appreciated.

```
startx
``` works for me.

---

### Post by Geoffrey_Arndt on 2023-08-06
startx was one of the commands  I tried early into this fiasco update.   Didn't work . . . too many pieces of the graphic system were not present.   

I don't have them written down, but there are 8 packages all involving the gnome and the desktop gui that are being "held back" and won't allow for a graphic system.   

So, we have a command line . . server like system prompt via a tty1 login(using my standard Ubuntu UserID along with standard admin password allows me to enter additional commands).    But I am no longer as competent with Linux and Ubuntu as I was just 5 years ago so I'm digging through written notes (along with CherryTree db).

---

### Post by ian-weisser on 2023-08-06
> **Geoffrey_Arndt said:**
> I don't have them written down, but there are 8 packages all involving the gnome and the desktop gui that are being "held back" and won't allow for a graphic system. 

In that case, I withdraw my earlier comment about Phased-Updates-cannot-be-a-culprit. You have shown me that it can.

Which suggests that folks suffering from Partial Upgrades due to Phased Updates should be able to try the following to complete the upgrades and restore their system:

```

sudo apt update
sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade   # Disable Phased Updates one time only - install ALL upgrades.

```

Depending upon the state of folks' systems, a reboot might be needed after that.

---

### Post by Geoffrey_Arndt on 2023-08-06
OK . . . more info about my down & out Ubuntu system (latest LTS flavor)

Response from "apt update && apt full-upgrade --dry-run:

"The following pakages have been kept back"

>   gjs
>   gnome-remote-desktop
>   libjs0g
>   python3-distupgrade
>   ubuntu-release-upgrader-core
>   ubuntu-release-upgrader-gtk

Any additional ideas/commands welcome (trying not to do a full-reinstall).    Thanks much!

Note:   running an AIO (all in one) System76 Sable.   This machine has not been especially Ubuntu friendly but I tried to work it out.   System76 no longer offers this version in their desktop lineup.

---

### Post by ashes00 on 2023-08-07
I'd like to report that I was able to do my normal Ubuntu GUI updates (Including Kernel 6.2), and the issue seems to have been resolved.  4 days from problem to fix.  Not to bad, and very thankful for Timeshift.  Timeshift has now saved my bacon 6 times!  If you have not looked at Timeshift you really need to.

---

