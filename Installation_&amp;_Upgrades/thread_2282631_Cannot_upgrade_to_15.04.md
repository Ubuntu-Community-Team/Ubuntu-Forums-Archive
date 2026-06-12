---
title: "Cannot upgrade to 15.04"
date: 2015-06-15
forum: Installation &amp; Upgrades
---

### Post by defaria on 2015-06-15
When I try to update to 15.04, synaptic tells me "Trying to recover from package failure". 

[ATTACH=CONFIG]262613[/ATTACH]

It never succeeds recovering from the package failure and I cannot close the dialog box. Instead I have to kill synaptic. I also get a bunch of these in the terminal that I started synaptic from:

```
** (synaptic:60211): WARNING **: TerminalTimeout in step: Trying to recover from package failure

** (synaptic:60211): WARNING **: no statusfd changes/content updates in terminal for 120 seconds

```

This causes me to have:

```

update-initramfs: deferring update (trigger activated)
Setting up libdevmapper1.02.1:amd64 (2:1.02.90-2.2) ...
Processing triggers for libc-bin (2.19-18) ...
Processing triggers for systemd (220-6) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for dbus (1.8.18-1) ...
Processing triggers for initramfs-tools (0.120) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-39-generic
Errors were encountered while processing:
 gconf2
 bluez
 libreoffice-gnome
$

```

I run synaptic again and I'm told I have 3 broken packages - gconf-service-backend, gconf2 and ubuntu-desktop. I select Edit > Fix broken packages and it selects only gconf-service-backend and ubuntu-desktop. Trying to run that leads me back to the attached picture above.

If I try sudo apt-get -f install I get:

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  activity-log-manager cheese fonts-lklug-sinhala fonts-sil-abyssinica
  fonts-sil-padauk fonts-tibetan-machine gnome-video-effects
  gstreamer1.0-plugins-base-apps libcmis-0.4-4 libegl1-mesa-drivers
  libopenvg1-mesa libreoffice-ogltrans libreoffice-pdfimport libspice-server1
  libwhoopsie-preferences0 printer-driver-brlaser signon-keyring-extension
  ubuntu-settings ubuntu-touch-sounds whoopsie-preferences
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gconf-service
The following packages will be REMOVED:
  gconf-service-backend ubuntu-desktop
The following packages will be upgraded:
  gconf-service
1 upgraded, 0 newly installed, 2 to remove and 1130 not upgraded.
3 not fully installed or removed.
Need to get 0 B/414 kB of archives.
After this operation, 496 kB disk space will be freed.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  gconf-service
Install these packages without verification? [y/N] y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US",
	LC_ALL = (unset),
	LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 223816 files and directories currently installed.)
Preparing to unpack .../gconf-service_3.2.6-3_amd64.deb ...
Unpacking gconf-service (3.2.6-3) over (3.2.6-2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/gconf-service_3.2.6-3_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/gconf/gconfd-2', which is also in package gconf-service-backend 3.2.6-2ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gconf-service_3.2.6-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now what?

---

### Post by kansasnoob on 2015-06-15
What method are you using to upgrade? I assume from the title that you're trying to upgrade 14.10 to 15.04, is that correct? If so I wonder how Synaptic comes into play?

---

### Post by defaria on 2015-06-15
I believe I was using the upgrade tool when it came back and said it couldn't only do a partial upgrade. I believe I selected Continue. That failed in some manner. I don't remember how. I think I ran it again but selected Partial Upgrade this time. That Also failed. Then I got to thinking that Synaptic has that thing about fixing broken packages so I tried the above.

What do you suggest I do?

---

### Post by kansasnoob on 2015-06-15
I've generally found that the easiest way to recover from a failed upgrade is simply to back up all important data (including Firefox and Thunderbird profiles, etc) and then performing a fresh installation. However someone else may be able to help you recover from the breakage if you have a great deal of patience.

If you need some advice on reinstalling please post the full output of:

```
sudo parted -l
```

That will tell us what partitioning arrangement we're dealing with.

---

### Post by sandyd on 2015-06-15
I think there is a repository causing this.

You are installing gconf-service_3.2.6-3_amd64.deb
In the repos, its called [gconf-service_3.2.6-3ubuntu1_amd64.deb]("http://packages.ubuntu.com/vivid/amd64/gconf-service/download")

---

### Post by defaria on 2015-06-16
> **sandyd said:**
> I think there is a repository causing this.

You are installing gconf-service_3.2.6-3_amd64.deb
In the repos, [gconf-service_3.2.6-3ubuntu1_amd64.deb exists.]("http://packages.ubuntu.com/vivid/amd64/gconf-service/download")

Actually I'm just trying to update. I don't understand what you are saying here. In the repos gconf-service_3.2.6-3ubuntu1_amd64.deb exists? Ok, fine. So what do I do?

---

### Post by defaria on 2015-06-16
I'm not gonna be re-installing everything any time soon. I shouldn't need to.

---

### Post by kansasnoob on 2015-06-16
Well we can try to figure out what's wrong. In your thread description you mention upgrading to 15.04 but one of the errors you posted shows a 14.10 kernel:

> update-initramfs: Generating /boot/initrd.img-3.16.0-39-generic

We need to begin by seeing just what we're working with so please post the full output of each of the following commands [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"):

```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

```
ls /etc/apt/sources.list.d
```

```
sudo apt-get update
```

```
sudo apt-get -f install
```

Hopefully that will point us in the right direction.

---

### Post by defaria on 2015-06-18
I may have started an upgrade to 15.04 then canceled it.

```
Andromeda:lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic
Andromeda:
```

```
Andromeda:cat /etc/apt/sources.list
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ utopic main restricted universe

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-proposed main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe
deb http://ftp.de.debian.org/debian sid main
Andromeda:
```

```
Andromeda:ls /etc/apt/sources.list.d
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.distUpgrade
gnome3-team-gnome3-precise.list.save
google-chrome-beta.list
google-chrome-beta.list.distUpgrade
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.distUpgrade
Andromeda:
```

```
Andromeda:sudo apt-get update
Ign http://us.archive.ubuntu.com utopic InRelease
Ign http://us.archive.ubuntu.com utopic-security InRelease        
Ign http://dl.google.com stable InRelease                                       
Ign http://us.archive.ubuntu.com utopic-updates InRelease                       
Hit http://dl.google.com stable Release.gpg                                              
Hit http://dl.google.com stable Release                                                  
Ign http://us.archive.ubuntu.com utopic-proposed InRelease
Ign http://us.archive.ubuntu.com utopic-backports InRelease           
Hit http://dl.google.com stable/main amd64 Packages
Get:1 http://ftp.de.debian.org sid InRelease [204 kB]                               
Hit http://dl.google.com stable/main i386 Packages                            
Hit http://us.archive.ubuntu.com utopic Release.gpg                                      
Get:2 http://us.archive.ubuntu.com utopic-security Release.gpg [933 B]         
Get:3 http://us.archive.ubuntu.com utopic-updates Release.gpg [933 B]                    
Get:4 http://us.archive.ubuntu.com utopic-proposed Release.gpg [933 B]                   
Hit http://us.archive.ubuntu.com utopic-backports Release.gpg                            
Ign http://dl.google.com stable/main Translation-en_US                          
Ign http://dl.google.com stable/main Translation-en                             
Hit http://us.archive.ubuntu.com utopic Release           
Get:5 http://us.archive.ubuntu.com utopic-security Release [63.5 kB]            
Get:6 http://us.archive.ubuntu.com utopic-updates Release [63.5 kB]                
Get:7 http://us.archive.ubuntu.com utopic-proposed Release [217 kB]               
Ign http://ftp.de.debian.org sid InRelease                       
Get:8 http://ftp.de.debian.org sid/main amd64 Packages/DiffIndex [7,876 B]
Hit http://us.archive.ubuntu.com utopic-backports Release    
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages             
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages                     
Get:9 http://ftp.de.debian.org sid/main i386 Packages/DiffIndex [7,876 B]
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages                          
Hit http://us.archive.ubuntu.com utopic/main i386 Packages                               
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages                         
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages                           
Hit http://us.archive.ubuntu.com utopic/main Translation-en                              
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en                        
Hit http://us.archive.ubuntu.com utopic/universe Translation-en                          
Get:10 http://us.archive.ubuntu.com utopic-security/main amd64 Packages [200 kB]         
Hit http://ftp.de.debian.org sid/main Translation-en                                     
Ign http://ftp.de.debian.org sid/main Translation-en_US                                  
Get:11 http://us.archive.ubuntu.com utopic-security/restricted amd64 Packages [8,496 B]  
Get:12 http://us.archive.ubuntu.com utopic-security/universe amd64 Packages [76.6 kB]    
Get:13 http://us.archive.ubuntu.com utopic-security/main i386 Packages [198 kB]          
Get:14 http://us.archive.ubuntu.com utopic-security/restricted i386 Packages [8,438 B]   
Get:15 http://us.archive.ubuntu.com utopic-security/universe i386 Packages [76.6 kB]     
Hit http://us.archive.ubuntu.com utopic-security/main Translation-en                     
Hit http://us.archive.ubuntu.com utopic-security/restricted Translation-en               
Hit http://us.archive.ubuntu.com utopic-security/universe Translation-en                 
Get:16 http://us.archive.ubuntu.com utopic-updates/main amd64 Packages [288 kB]          
Get:17 http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages [11.0 kB]   
Get:18 http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages [110 kB]      
Get:19 http://us.archive.ubuntu.com utopic-updates/main i386 Packages [285 kB]           
Get:20 http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages [11.0 kB]    
Get:21 http://us.archive.ubuntu.com utopic-updates/universe i386 Packages [110 kB]       
Hit http://us.archive.ubuntu.com utopic-updates/main Translation-en                      
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en                
Hit http://us.archive.ubuntu.com utopic-updates/universe Translation-en                  
Get:22 http://us.archive.ubuntu.com utopic-proposed/main amd64 Packages [76.6 kB]        
Get:23 http://us.archive.ubuntu.com utopic-proposed/restricted amd64 Packages [28 B]     
Get:24 http://us.archive.ubuntu.com utopic-proposed/universe amd64 Packages [10.7 kB]    
Get:25 http://us.archive.ubuntu.com utopic-proposed/main i386 Packages [75.4 kB]         
Get:26 http://us.archive.ubuntu.com utopic-proposed/restricted i386 Packages [28 B]      
Get:27 http://us.archive.ubuntu.com utopic-proposed/universe i386 Packages [10.2 kB]     
Get:28 http://us.archive.ubuntu.com utopic-proposed/main Translation-en [31.2 kB]        
Hit http://us.archive.ubuntu.com utopic-proposed/restricted Translation-en               
Hit http://us.archive.ubuntu.com utopic-proposed/universe Translation-en                 
Hit http://us.archive.ubuntu.com utopic-backports/main amd64 Packages                    
Hit http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages                
Hit http://us.archive.ubuntu.com utopic-backports/main i386 Packages                     
Hit http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages               
Hit http://us.archive.ubuntu.com utopic-backports/universe i386 Packages                 
Hit http://us.archive.ubuntu.com utopic-backports/main Translation-en                    
Hit http://us.archive.ubuntu.com utopic-backports/restricted Translation-en              
Hit http://us.archive.ubuntu.com utopic-backports/universe Translation-en                
Fetched 2,154 kB in 44s (48.7 kB/s)                                                      
Reading package lists... Done
W: GPG error: http://ftp.de.debian.org sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010
Andromeda:
```

```
Andromeda:sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gconf-service gconf2-common libgconf-2-4
The following packages will be REMOVED:
  gconf-service-backend
The following packages will be upgraded:
  gconf-service gconf2-common libgconf-2-4
3 upgraded, 0 newly installed, 1 to remove and 1382 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,879 kB of archives.
After this operation, 5,302 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
WARNING: The following packages cannot be authenticated!
  gconf-service libgconf-2-4 gconf2-common
Install these packages without verification? [y/N] y
(Reading database ... 222497 files and directories currently installed.)
Preparing to unpack .../gconf-service_3.2.6-3_amd64.deb ...
Unpacking gconf-service (3.2.6-3) over (3.2.6-2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/gconf-service_3.2.6-3_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/gconf/gconfd-2', which is also in package gconf-service-backend 3.2.6-2ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gconf-service_3.2.6-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Andromeda:
```

---

### Post by kansasnoob on 2015-06-18
OK, you're on 14.10 (aka: Utopic) rather than 15.04.

There are a number of issues. Why in the world are you using packages from Debian Unstable:

```
Andromeda:cat /etc/apt/sources.list
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ utopic main restricted universe

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ utopic-security main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-proposed main restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe
**[COLOR="#FF0000"]deb http://ftp.de.debian.org/debian sid main[/COLOR]**
```

You may also have some Precise PPA's still enabled:

```
Andromeda:ls /etc/apt/sources.list.d
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.distUpgrade
gnome3-team-gnome3-precise.list.save
google-chrome-beta.list
google-chrome-beta.list.distUpgrade
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.distUpgrade
```

So I'd begin by opening Synaptic, click on Settings > Repositories. The Precise PPA's will probably be under Other Software, but I'm not sure where the Debian Sid repo will show up (if at all). We may have to use gedit to comment out the Debian Sid repo if it doesn't show up in the Software & Updates UI. Also while you have that open the Proposed updates under the Updates tab (named Pre-released updates).

Once you have no Debian Sid, Precise, or Utopic Proposed repos enabled you can just close that UI and close Synaptic, then open the terminal and run:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

Just FYI Utopic is only supported for one more month:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So if we are able to get this straightened out you'll almost immediately have to upgrade to Vivid, and then in a little over 6 months you'll need to upgrade again. I personally prefer using only LTS versions on production machines, but that's just idle chit-chat ;)

---

### Post by defaria on 2015-06-19
I started synaptic and immediately it said I had 2 broken packages. I'm gonna ignore that for now. Looking at Settings > Repository > Other Software I see Debian 'Sid' (unstable) as the first entry. I don't know how that got there. I toggled it off. Here's what I have listed under Other Software:

* [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main
* [http://ppa-launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa-launchpad.net/gnome3-team/gnome3/ubuntu)
* [http://ppa-launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa-launchpad.net/gnome3-team/gnome3/ubuntu) (Source Code)
* [http://ppa-launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa-launchpad.net/nilarimogard/webupd8/ubuntu)
* [http://ppa-launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa-launchpad.net/nilarimogard/webupd8/ubuntu) (Source Code)

Of those only the Google one is toggled on. Next I fired up a terminal and when to /etc/apt/sources.list.d and moved the files there that said precise to a directory named save. Then I did:

[code]Wizard Andromeda:apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg            
Hit http://dl.google.com stable Release                
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages            
Ign http://us.archive.ubuntu.com utopic InRelease              
Ign http://us.archive.ubuntu.com utopic-security InRelease
Ign http://us.archive.ubuntu.com utopic-updates InRelease
Ign http://us.archive.ubuntu.com utopic-proposed InRelease
Ign http://us.archive.ubuntu.com utopic-backports InRelease
Hit http://us.archive.ubuntu.com utopic Release.gpg
Hit http://us.archive.ubuntu.com utopic-security Release.gpg
Hit http://us.archive.ubuntu.com utopic-updates Release.gpg
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Hit http://us.archive.ubuntu.com utopic-proposed Release.gpg
Hit http://us.archive.ubuntu.com utopic-backports Release.gpg
Hit http://us.archive.ubuntu.com utopic Release
Hit http://us.archive.ubuntu.com utopic-security Release
Hit http://us.archive.ubuntu.com utopic-updates Release
Hit http://us.archive.ubuntu.com utopic-proposed Release
Hit http://us.archive.ubuntu.com utopic-backports Release
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic/main i386 Packages
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic/main Translation-en
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-security/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic-security/main i386 Packages
Hit http://us.archive.ubuntu.com utopic-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic-security/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic-security/main Translation-en
Hit http://us.archive.ubuntu.com utopic-security/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic-security/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/main i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/main Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-proposed/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic-proposed/main Translation-en
Hit http://us.archive.ubuntu.com utopic-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic-proposed/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com utopic-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com utopic-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com utopic-backports/main Translation-en          
Hit http://us.archive.ubuntu.com utopic-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com utopic-backports/universe Translation-en      
Reading package lists... Done                                                  
Wizard Andromeda:[/quote]

and 

[code]Wizard Andromeda:apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  activity-log-manager cheese fonts-lklug-sinhala fonts-sil-abyssinica
  fonts-sil-padauk fonts-tibetan-machine gnome-video-effects
  gstreamer1.0-plugins-base-apps libgfortran3 liblapack3 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libqt5positioning5 libreoffice-ogltrans
  libtidy-0.99-0 libufe-xidgetter0 libunity-webapps0 libwhoopsie-preferences0
  oxideqt-codecs printer-driver-brlaser python-beautifulsoup python-feedparser
  python-gmenu python-numpy python-oauth2 python-pyorbit python-rsvg
  python-support python-tz python-utidylib python-webkit python-wnck
  qml-module-qtquick-dialogs qml-module-qtquick-privatewidgets
  qml-module-qtwebkit qtdeclarative5-accounts-plugin
  qtdeclarative5-dialogs-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-web-plugin qtdeclarative5-ubuntu-web-plugin-assets
  ubuntu-settings unity-webapps-common unity-webapps-qml unity-webapps-service
  webaccounts-extension-common webapp-container webbrowser-app
  whoopsie-preferences xul-ext-unity xul-ext-webaccounts
  xul-ext-websites-integration
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apturl compiz compiz-gnome compizconfig-backend-gconf gconf2 gksu
  gnome-applets gnome-applets-data gnome-media gnome-terminal
  gnome-terminal-data gnome-user-share gstreamer0.10-gconf libbonoboui2-0
  libgconf2-4 libgksu2-0 libgnome-media-profiles-3.0-0 libgnome2-0
  libgnome2-bin libgnome2-common libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libqtgconf1 libreoffice-gnome libswt-gnome-gtk-3-jni
  libunity-2d-private0 nautilus-share python-gnome2 screenlets
  screenlets-pack-all transmission-gtk ubuntu-desktop ubuntu-tweak unity
  unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-tweak-tool
0 upgraded, 0 newly installed, 41 to remove and 19 not upgraded.
2 not fully installed or removed.
After this operation, 114 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 222496 files and directories currently installed.)
Removing ubuntu-tweak (0.8.7-1~trusty2) ...
Removing libreoffice-gnome (1:4.3.7~rc2-0ubuntu1) ...
Removing libqtgconf1 (0.1-0ubuntu5) ...
...[/quote]

Well at least that finished! Trying Software Updater to see what that says... Hmmm... A couple of updates... Seems fine. Thanks!

I have to reboot now. Afterwards I'll try the update to 15.04. BTW, are there any problems I'll hit going to 15.04? I ask because I'm a little leery about using systemd.

---

### Post by kansasnoob on 2015-06-19
I've encountered no problems at all with systemd. Be sure and toggle the proposed updates repo off before trying to upgrade to 15.04. Also try:

```
sudo apt-get dist-upgrade -s
```

The -s suffix only simulates what will happen when you try to fully update your current Utopic install. If it looks OK then just run:

```
sudo apt-get dist-upgrade
```

Then I'd run the current install for a few days at least to watch for any apparent borkage. I suspect there will be some borkage due to the Debian Sid packages.

Which desktop environment do you run? It might be a good idea to "re-install" that DE before continuing to be sure there are no missing dependencies.

---

### Post by defaria on 2015-06-22
So I decided that I'd try the above but first I ran the update-manager to see if there were any updates for 14.10 and there were so I applied them. Since there were kernal updates it wanted to reboot so I did. When I come back I get a dialog box saying that a system error occurred and another dialog box saying there's a new version of Ubuntu, 15.04 and did I want to update it. I tried to process this system error but the dialog just went away never to return. As for the new version of Ubuntu I said, ask me later. But now I have a blank screen. No gnome-panel, no compiz, no root menu, no way to start a terminal, etc. I tried to ssh in from another session but my machine is not talking on the net. Can't ssh - connection refused. Can't even ping! Wonderful. Kernal update breaks the whole system. Luckily I can restore to my previous snapshot and try again but it keeps doing the same thing.

OK back on my snapshotted 14.10. Seems I cannot ping or ssh into this one either. Odd. Strike that, I cannot ssh in from the host OS but can from other machines.

```
Andromeda:sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-39 linux-headers-3.16.0-39-generic
  linux-image-3.16.0-39-generic linux-image-extra-3.16.0-39-generic
Use 'apt-get autoremove' to remove them.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Andromeda:

```

Well I guess I'll autoremove to be clean... Hmmm...

```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```

Now I have:

```

Andromeda:sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Andromeda:uname -a
Linux andromeda 3.16.0-41-generic #57-Ubuntu SMP Thu Jun 18 08:44:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Andromeda:cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"
NAME="Ubuntu"
VERSION="14.10 (Utopic Unicorn)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.10"
VERSION_ID="14.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
Andromeda:

```

I'm not sure... Should I do sudo apt-get dist-upgrade without the -s? Or sudo do-release-upgrade or run update-manager and try to upgrade to 15.04 from there? I'll do another snapshot here... 

Hmmm... sudo apt-get dist-upgrade does nothing. I guess it thinks I'm on 15.04.

sudo do-release-upgrade:

```

...
Do you want to start the upgrade? 


6 packages are going to be removed. 110 new packages are going to be 
installed. 1372 packages are going to be upgraded. 

You have to download a total of 1,020 M. This download will take 
about 10 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]

```

Let it go. Asked me to turn off xscreensaver. OK. Went onward, screen blanked, now I can't unblank it. Great... Extended the screen to both monitors. Viola! The screen unblanked. Silly VM... Trick only lasted for a short time. Nothing updates on the screen. The terminal I was running do-release-upgrade will not respond. It will not move. It will not do anything. This is great! Trying the trick of suspending the VM and resuming it... Nope. It's hosed. UGH!

Reverted back again.... Tried applying update using synaptic. Wanted me to restart. Restarted. Can't log in. Login loop. Prompted for password, put that in, screen clears and goes back to the login screen. I can use Alt-Ctl-F1 to get a IDE session and log in. My user is OK, just can't get past the login screen. UGH #2. Reverting. I gotta get some real work done.

Note that my current machine is talking via NIS to the domain. Perhaps that's screwing up something?

---

### Post by kansasnoob on 2015-06-22
I suspect some serious borkage from the Debian Sid incident. When you restore the previous snapshot what effect does it have on software sources? Is it dropping Sid back into the works?

You never answered what desktop environment you use. I wondered because you earlier ran apt-get autoremove and it removed some key components of Unity:

```
The following packages will be REMOVED:
apturl compiz compiz-gnome compizconfig-backend-gconf gconf2 gksu
gnome-applets gnome-applets-data gnome-media gnome-terminal
gnome-terminal-data gnome-user-share gstreamer0.10-gconf libbonoboui2-0
libgconf2-4 libgksu2-0 libgnome-media-profiles-3.0-0 libgnome2-0
libgnome2-bin libgnome2-common libgnomeui-0 libgnomevfs2-0
libgnomevfs2-common libqtgconf1 libreoffice-gnome libswt-gnome-gtk-3-jni
libunity-2d-private0 nautilus-share python-gnome2 screenlets
screenlets-pack-all transmission-gtk ubuntu-desktop ubuntu-tweak unity
unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
unity-tweak-tool
0 upgraded, 0 newly installed, 41 to remove and 19 not upgraded.
2 not fully installed or removed.
After this operation, 114 MB disk space will be freed.
Do you want to continue? [Y/n] Y
```

So I'd check the software sources again when you restore the previous snapshot and make sure we're not once again trying to use Debian Sid packages.

If you're using the standard Ubuntu desktop (unity) I'd then see what happens when you run:

```
sudo apt-get install ubuntu-desktop -s
```

You can seldom (if ever) release upgrade your way out of borkage, that's why I said I've found it's best to just figure out what blew things up (in this case trying to use Debian Sid packages), then reinstall, and avoid repeating the mistakes that caused the previous borkage.

---

### Post by defaria on 2015-06-23
No I don't use unity - I'm a gnome/compiz/emerald guy. That "sid" thing is in sources.list but it's commented out:

```

Wizard Andromeda:pwd
/etc/apt
Wizard Andromeda:find . -type f -exec grep ftp.de.debian {} +
./sources.list:# deb http://ftp.de.debian.org/debian sid main
Wizard Andromeda:

```

Installed Unity Desktop by removing the -s. Re applied update. Let me in this time. With a Unity desktop. Logged out and set my login to Gnome Flashback Compiz.

Ran software updater again. Said there was a new version of Ubuntu (15.04). Said to upgrade... So I tried again. Midway through screen went blank and the VM locked up.

---

