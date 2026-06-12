---
title: "New PC apps download but won't install or run"
date: 2017-05-08
forum: Installation &amp; Upgrades
---

### Post by tachum1 on 2017-05-08
HI,

I am a long term Ubuntu user. I just bought a new computer box, running ntel® Pentium(R) CPU G4560 @ 3.50GHz × 4  and the graphics card is an Intel® Kabylake GT1 . It has an ASUS motherboard. 8Gb RAM and SSD.

I had problems getting 17.04 on and found that apps woudln't either install or run. I downloaded Synaptic to get things going and it wouldn't run. This makes things hard. Installing apps by command line is OK but installing using package manager apps doesn't work. When I run Synaptic it asks for a password and then stops. Ditto everything else. 

I found others had similar problems so I went back to 16.04 LTS. Same problems exactly. 

I am starting to think this might be a graphics problem? here is the glxinfo initial output

glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4

I have never really had major problems with ubuntu installs but I am totally beat here. Any ideas? 

Cheers

---

### Post by sp40140 on 2017-05-08
What problems did you have while installing 17.04? How did you fix them?
Are you able to install ANY software at all (if so, how)? 
Is your install stable? Do you see random crashes / errors?

---

### Post by tachum1 on 2017-05-08
Both 17.04 and 16.04 ran ok once installed. No crashes etc. I just can't run any apps that didn't come installed during installation.

---

### Post by mastablasta on 2017-05-08
did you maybe use sudo when launching an application with graphical interface?

you say install works from command line. well do an install of graphics app in command line, then run it from terminal. see what kind of output you get and post it here wrapped in code tags (the # icon in "go advanced" answer option).

---

### Post by sp40140 on 2017-05-08
Can you give me example of the software you are trying to run which you installed manually?
can you check if it's installed properly? by running :
```
 sudo dpkg -l <program name>
```

---

### Post by tachum1 on 2017-05-09
Thanks for your help.

I installed Synaptic by command line and the icon appears on the list but won't run (although it asked for a password) when you double click. I enter the password and nothing happens. 
here is the co0mmand line output..
```
sudo dpkg -l synaptic
[sudo] password for gaz: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  synaptic       0.83         amd64        Graphical package manager

```
I also installed Cinnamon Desktop buty it won't run. output....

```
sudo dpkg -l synaptic (sorry I copied the wrong line. Should be Cinnamon, but the output was the same)
[sudo] password for gaz: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  synaptic       0.83         amd64        Graphical package manager

```
Does this help?

---

### Post by sp40140 on 2017-05-09
I should have tweaked the command to:
```
 sudo dpkg -l | grep <program name> 
```
But this is fine as well.
It seems that it's installed.
Have you tried to install any other software?
Also, if you haven't run these commands please run them and let us know if they give any errors:
```

sudo apt update
sudo apt upgrade

```

---

### Post by tachum1 on 2017-05-11
Ok will try when I get home. many thanks

---

### Post by tachum1 on 2017-05-15
Ok apologies for the delay. My modem router failed. A replacement will arrive shortly.

Here is the output for synaptic..

sudo dpkg -l | grep synaptic
[sudo] password for gaz: 
ii   synaptic                                     0.83                                          amd64        Graphical  package manager
ii  xserver-xorg-input-synaptics-hwe-16.04       1.8.3-1ubuntu1~16.04.1                        amd64        Synaptics  TouchPad driver for X.Org server
gaz@gaz-desktop:~$ 



Here is the output for sudo apt update or did you mean sudo apt-get update?

gaz@gaz-desktop:~$ sudo apt-get update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Fetched 306 kB in 3s (76.9 kB/s)  
Reading package lists... Done
gaz@gaz-desktop:~$ 


and for upgrade...

gaz@gaz-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra firefox firefox-locale-en flashplugin-installer
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libfreetype6
  libjavascriptcoregtk-4.0-18 librtmp1 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 logrotate openssh-client zlib1g
14 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 72.4 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] 

output. Note that all seems to work ok, including flashplayer...
z@gaz-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra firefox firefox-locale-en flashplugin-installer
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libfreetype6
  libjavascriptcoregtk-4.0-18 librtmp1 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 logrotate openssh-client zlib1g
14 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 72.4 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64  chromium-codecs-ffmpeg-extra amd64 58.0.3029.96-0ubuntu0.16.04.1279 [999  kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4.1 [51.2 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 logrotate amd64 3.8.7-2ubuntu2.16.04.1 [37.8 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 librtmp1 amd64 2.4+20151223.gitfa8646d-1ubuntu0.1 [54.4 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 openssh-client amd64 1:7.2p2-4ubuntu2.2 [587 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libfreetype6 amd64 2.6.1-0.1ubuntu2.3 [316 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox amd64 53.0.2+build1-0ubuntu0.16.04.2 [46.4 MB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox amd64 53.0.2+build1-0ubuntu0.16.04.2 [46.4 MB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox-locale-en amd64 53.0.2+build1-0ubuntu0.16.04.2 [665 kB]
Get:9  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64  flashplugin-installer amd64 25.0.0.171ubuntu0.16.04.1 [6,846 B]
Get:10  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64  libwebkit2gtk-4.0-37-gtk2 amd64 2.16.1-0ubuntu0.16.04.2 [8,637 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.16.1-0ubuntu0.16.04.2 [10.6 MB]
Get:12  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64  libjavascriptcoregtk-4.0-18 amd64 2.16.1-0ubuntu0.16.04.2 [3,949 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.16.1-0ubuntu0.16.04.2 [67.4 kB]
Get:14  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64  gir1.2-javascriptcoregtk-4.0 amd64 2.16.1-0ubuntu0.16.04.2 [21.7 kB]
Fetched 61.2 MB in 3min 44s (273 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 223139 files and directories currently installed.)
Preparing to unpack .../chromium-codecs-ffmpeg-extra_58.0.3029.96-0ubuntu0.16.04.1279_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (58.0.3029.96-0ubuntu0.16.04.1279) over (58.0.3029.81-0ubuntu0.16.04.1277) ...
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_amd64.deb ...
Unpacking zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Setting up zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
(Reading database ... 223139 files and directories currently installed.)
Preparing to unpack .../logrotate_3.8.7-2ubuntu2.16.04.1_amd64.deb ...
Unpacking logrotate (3.8.7-2ubuntu2.16.04.1) over (3.8.7-2ubuntu2) ...
Preparing to unpack .../librtmp1_2.4+20151223.gitfa8646d-1ubuntu0.1_amd64.deb ...
Unpacking librtmp1:amd64 (2.4+20151223.gitfa8646d-1ubuntu0.1) over (2.4+20151223.gitfa8646d-1build1) ...
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../libfreetype6_2.6.1-0.1ubuntu2.3_amd64.deb ...
Unpacking libfreetype6:amd64 (2.6.1-0.1ubuntu2.3) over (2.6.1-0.1ubuntu2.2) ...
Preparing to unpack .../firefox_53.0.2+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox (53.0.2+build1-0ubuntu0.16.04.2) over (53.0+build6-0ubuntu0.16.04.1) ...
Preparing to unpack .../firefox-locale-en_53.0.2+build1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox-locale-en (53.0.2+build1-0ubuntu0.16.04.2) over (53.0+build6-0ubuntu0.16.04.1) ...
Preparing to unpack .../flashplugin-installer_25.0.0.171ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (25.0.0.171ubuntu0.16.04.1) over (25.0.0.148ubuntu0.16.04.1) ...
Preparing to unpack .../libwebkit2gtk-4.0-37-gtk2_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37-gtk2:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../libwebkit2gtk-4.0-37_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../libjavascriptcoregtk-4.0-18_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-webkit2-4.0_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-4.0_2.16.1-0ubuntu0.16.04.2_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) over (2.16.1-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for update-notifier-common (3.168.4) ...
flashplugin-installer: processing...
flashplugin-installer:  downloading  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz)
Get:1 [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20170509.1.orig.tar.gz) [30.4 MB]
Fetched 30.4 MB in 1min 4s (469 kB/s)                                          
W:  Can't drop privileges for downloading as file  '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170509.1.orig.tar.gz'  couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission  denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170509.1.orig.tar.gz
Flash Plugin installed.
Setting up chromium-codecs-ffmpeg-extra (58.0.3029.96-0ubuntu0.16.04.1279) ...
Setting up logrotate (3.8.7-2ubuntu2.16.04.1) ...
Setting up librtmp1:amd64 (2.4+20151223.gitfa8646d-1ubuntu0.1) ...
Setting up openssh-client (1:7.2p2-4ubuntu2.2) ...
Setting up libfreetype6:amd64 (2.6.1-0.1ubuntu2.3) ...
Setting up firefox (53.0.2+build1-0ubuntu0.16.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (53.0.2+build1-0ubuntu0.16.04.2) ...
Setting up flashplugin-installer (25.0.0.171ubuntu0.16.04.1) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up libwebkit2gtk-4.0-37-gtk2:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.16.1-0ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
gaz@gaz-desktop:~$ 

Just rechecked. Graphic based installer won't run and Synaptic won't run from the icon.

Thanks!

---

