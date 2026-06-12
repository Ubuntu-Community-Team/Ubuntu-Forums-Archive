---
title: "Problem with upgrades in Ubuntu 10.10 running in Windows VirtualBox"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by samsanchez on 2010-12-14
Hi

I'm running Ubuntu 10.10 on VirtualBox in Windows.

When I try [FONT=Courier New]sudo apt-get upgrade[FONT=Verdana] I get the following:

[/FONT][/FONT]```
WARNING: The following packages cannot be authenticated!
  libc-dev-bin libc6-dev libc-bin libc6 tzdata libcairo2 libgp11-0 libgcr0 gnome-keyring ubuntu-docs ubuntu-sso-client sysvinit-utils sysv-rc initscripts libdrm2 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1
  udev plymouth-label plymouth libplymouth2 libudev0 apparmor libapparmor1 libapparmor-perl apparmor-utils libldap-2.4-2 plymouth-theme-ubuntu-text gconf2-common libgconf2-4 gconf2 libvte-common libvte9
  python-vte update-manager update-manager-core libasound2 alsa-utils app-install-data-partner libdecoration0 compiz-gnome compiz-plugins compiz-core compiz update-inetd libedataserver1.2-13 libcamel1.2-14
  libebook1.2-9 nautilus-sendto-empathy empathy empathy-common libebackend1.2-0 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libegroupwise1.2-13 libgdata1.2-1 libgdata-google1.2-1 evolution-data-server
  evolution-data-server-common libedataserverui1.2-8 libevolution evolution evolution-common evolution-exchange gcalctool gconf-defaults-service gdb gdm-guest-session libgpod4 libgudev-1.0-0
  rhythmbox-plugins rhythmbox-plugin-cdrecorder libnautilus-extension1 nautilus-data nautilus rhythmbox libgvfscommon0 gvfs-fuse libwbclient0 libsmbclient gvfs-backends gvfs gwibber gwibber-service hplip
  libsane-hpaio hplip-data hpijs libhpmud0 hplip-cups humanity-icon-theme libibus2 ibus python-ibus ibus-gtk jockey-gtk jockey-common libgpod-common libpam-gnome-keyring pulseaudio-utils pulseaudio
  pulseaudio-module-x11 pulseaudio-module-gconf pulseaudio-module-bluetooth pulseaudio-esound-compat libpulse-mainloop-glib0 libpulse-browse0 libpulse0 libpurple-bin libpurple0 gnome-settings-daemon
  ubuntuone-client-gnome xdg-utils libsyncdaemon-1.0-1 ubuntuone-client python-ubuntuone-client libutouch-grail1 light-themes smbclient nautilus-share samba-common samba-common-bin pitivi
  plymouth-theme-ubuntu-logo python-cupshelpers python-papyon simple-scan python-aptdaemon-gtk aptdaemon python-aptdaemon software-center system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-haze tomboy xul-ext-ubufox ubufox vino xserver-xorg-video-intel indicator-sound libgexiv2-0 rhythmbox-ubuntuone-music-store
Install these packages without verification [y/N]?
```I'll post the output for the 'sudo apt-get update' which precedes this, in case it sheds any light on the matter:

```
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://extras.ubuntu.com maverick Release               
Hit http://security.ubuntu.com maverick-security Release.gpg        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://security.ubuntu.com maverick-security Release
Hit http://extras.ubuntu.com maverick/main Sources                   
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://extras.ubuntu.com maverick/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB [94.5kB]
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Bad header line
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Get:2 http://gb.archive.ubuntu.com maverick-updates Release.gpg [32.0kB]
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
99% [1 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick/main Sources/DiffIndex
E: Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources.IndexDiff - open (2: No such file or directory)

```

Can anyone help?

---

### Post by samsanchez on 2010-12-14
Just to clarify, I haven't installed any new repositories or anything like that. This is a virtually new, standard installation.

---

### Post by plucky on 2010-12-14
> E: Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources.IndexDiff - open (2: No such file or directory)

You should delete this file ```
cd /var/lib/apt/lists/
sudo rm gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources.IndexDiff
```

Then run ```
sudo apt-get update
```

Should re-create it correctly.

Good Luck

---

### Post by samsanchez on 2010-12-14
No joy, I'm afraid. It doesn't think that the file you mentioned exists.

I tried deleting:

gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources

This worked, but the apt-get upgrade still gave me the same warning as before.

---

### Post by plucky on 2010-12-14
> **samsanchez said:**
> No joy, I'm afraid. It doesn't think that the file you mentioned exists.

I tried deleting:

gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources

This worked, but the apt-get upgrade still gave me the same warning as before.

Please list the files in that directory.

```
ls -l /var/lib/apt/lists/
```

---

### Post by sikander3786 on 2010-12-14
> ```
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
  Bad header line
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Bad header line

```

Changing the update server from Software Center > Edit > Software Sources helps in most cases. I would prefer the Main Server for downloads.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/26083](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/26083)

Otherwise, you definitely need to follow **plucky's** suggestions.

---

### Post by samsanchez on 2010-12-15
In answer to your question, Plucky:

```
ls -l /var/lib/apt/lists/
total 61124
-rw-r--r-- 1 root root        0 2010-10-11 00:00 extras.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
-rw-r--r-- 1 root root        0 2010-10-11 00:00 extras.ubuntu.com_ubuntu_dists_maverick_main_source_Sources
-rw-r--r-- 1 root root    57290 2010-10-11 00:00 extras.ubuntu.com_ubuntu_dists_maverick_Release
-rw-r--r-- 1 root root       65 2010-12-14 08:01 extras.ubuntu.com_ubuntu_dists_maverick_Release.gpg
-rw-r--r-- 1 root root  9290611 2010-10-10 11:14 gb.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
-rw-r--r-- 1 root root  3764068 2010-10-10 11:17 gb.archive.ubuntu.com_ubuntu_dists_maverick_main_source_Sources
-rw-r--r-- 1 root root   872490 2010-10-10 11:15 gb.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   605962 2010-10-10 11:18 gb.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_source_Sources
-rw-r--r-- 1 root root    39772 2010-10-10 11:18 gb.archive.ubuntu.com_ubuntu_dists_maverick_Release
-rw-r--r-- 1 root root    27385 2010-10-10 11:14 gb.archive.ubuntu.com_ubuntu_dists_maverick_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     9426 2010-10-01 12:03 gb.archive.ubuntu.com_ubuntu_dists_maverick_restricted_i18n_Translation-en%5fGB
-rw-r--r-- 1 root root    13585 2010-10-10 11:17 gb.archive.ubuntu.com_ubuntu_dists_maverick_restricted_source_Sources
-rw-r--r-- 1 root root 28808979 2010-10-10 11:15 gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages
-rw-r--r-- 1 root root 17048287 2010-10-10 11:18 gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_source_Sources
-rw-r--r-- 1 root root   839547 2010-12-14 03:12 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root   196328 2010-12-14 03:15 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_source_Sources
-rw-r--r-- 1 root root     5780 2010-12-14 03:12 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root     2233 2010-12-14 03:15 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_multiverse_source_Sources
-rw-r--r-- 1 root root    31364 2010-12-14 03:17 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_Release
-rw-r--r-- 1 root root        0 2010-12-14 03:12 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root        0 2010-12-14 03:15 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_restricted_source_Sources
-rw-r--r-- 1 root root   341435 2010-12-14 03:12 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root    67542 2010-12-14 03:15 gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_source_Sources
-rw-r----- 1 root root        0 2010-10-07 16:58 lock
drwxr-xr-x 2 root root     4096 2010-12-14 13:34 partial
-rw-r--r-- 1 root root   310039 2010-12-14 02:05 security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
-rw-r--r-- 1 root root    59404 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_main_source_Sources
-rw-r--r-- 1 root root     3366 2010-12-14 02:05 security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root     1154 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_source_Sources
-rw-r--r-- 1 root root    27229 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_Release
-rw-r--r-- 1 root root      198 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_Release.gpg
-rw-r--r-- 1 root root        0 2010-12-14 02:05 security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root        0 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_restricted_source_Sources
-rw-r--r-- 1 root root    95872 2010-12-14 02:05 security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root    14997 2010-12-14 02:06 security.ubuntu.com_ubuntu_dists_maverick-security_universe_source_Sources

```

What I don't understand is why this is happening on an entirely new installation. Is this a bug in Ubuntu 10.10? Has anyone else experienced this problem?

---

### Post by plucky on 2010-12-15
Open a terminal and ```
cd /var/lib/apt/lists/
```

Then ```
sudo rm *
``` will delete all the files in that directory but will fail with the "partial" directory as it is a directory.

Then run ```
sudo apt-get update
``` will download the lists again.

Good Luck

---

### Post by samsanchez on 2010-12-15
That seems to have worked. Thanks.

Just out of curiosity, do you think this is a bug, or is it a result of intalling on VirtualBox? I only ask because I was considering making Ubuntu my main operating system, but I might not if I'm going to get more problems like this.

---

### Post by plucky on 2010-12-15
> **samsanchez said:**
> That seems to have worked. Thanks.

Just out of curiosity, do you think this is a bug, or is it a result of intalling on VirtualBox? I only ask because I was considering making Ubuntu my main operating system, but I might not if I'm going to get more problems like this.

This was most likely to be a problem on the server you were downloading from being out of step with the Main Server,rather than something you did.

Learning a new operating system takes time to learn.

Trying new things and learning is fun but could break your system.

Learning on Virtualbox is good,but I think it limits some of what you can achieve with a proper install.Although restoring from a snapshot is very fast.

Good Luck with whatever you decide.

Please use **[Thread Tools]** to mark as [Solved]

---

