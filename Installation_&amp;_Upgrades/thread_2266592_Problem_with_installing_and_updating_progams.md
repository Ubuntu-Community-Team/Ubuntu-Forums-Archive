---
title: "Problem with installing and updating progams"
date: 2015-02-24
forum: Installation &amp; Upgrades
---

### Post by darko6 on 2015-02-24
1.Whenever I try to install some program using Ubuntu Software Center it pops up an error "*Package dependencies cannot be resolved - This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.* " . I can install and update programs/softwares using Synaptic package menager, though. But...

2. In Synaptic i can not find this packages:
a)Linconnect  
b)Android-notifier

---

### Post by Bucky Ball on 2015-02-24
> **darko6 said:**
> 

2. In Synaptic i can not find this packages:
a)Linconnect  
b)Android-notifier

Neither can I, which means they are not in the repositories. Android-notifier may be part of the android package, though. [This]("http://www.webupd8.org/2014/01/get-android-notifications-on-your.html") looks like how you install Linconnect.

Before doing anything else, though, please open a terminal and:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please report any and all errors.

---

### Post by darko6 on 2015-02-24
Can not install any of that.
Output of linnconect package:
[HTML]darko@darko:~$ wget http://raw.github.com/hauckwill/linconnect-server/master/LinConnectServer/install.sh--2015-02-24 08:42:44--  http://raw.github.com/hauckwill/linconnect-server/master/LinConnectServer/install.shResolving raw.github.com (raw.github.com)... 185.31.17.133Connecting to raw.github.com (raw.github.com)|185.31.17.133|:80... connected.HTTP request sent, awaiting response... 301 Moved PermanentlyLocation: https://raw.github.com/hauckwill/linconnect-server/master/LinConnectServer/install.sh [following]--2015-02-24 08:42:44--  https://raw.github.com/hauckwill/linconnect-server/master/LinConnectServer/install.shConnecting to raw.github.com (raw.github.com)|185.31.17.133|:443... connected.HTTP request sent, awaiting response... 301 Moved PermanentlyLocation: https://raw.githubusercontent.com/hauckwill/linconnect-server/master/LinConnectServer/install.sh [following]--2015-02-24 08:42:45--  https://raw.githubusercontent.com/hauckwill/linconnect-server/master/LinConnectServer/install.shResolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.31.17.133Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.31.17.133|:443... connected.HTTP request sent, awaiting response... 200 OKLength: 2180 (2,1K) [text/plain]Saving to: ‘install.sh.5’
100%[======================================>] 2.180       --.-K/s   in 0,001s  
2015-02-24 08:42:46 (1,53 MB/s) - ‘install.sh.5’ saved [2180/2180]
darko@darko:~$ chmod +x install.shdarko@darko:~$ ./install.shInstall LinConnect server? [Y/N]yInstall dependencies automatically (for Debian-based distros) [Y/N]yInstalling dependencies...Reading package lists... DoneBuilding dependency tree       Reading state information... Donegir1.2-notify-0.7 is already the newest version.libavahi-compat-libdnssd1 is already the newest version.libavahi-compat-libdnssd1 set to manually installed.python-gobject is already the newest version.The following extra packages will be installed:  git-man liberror-perl python-colorama python-distlib python-html5lib  python-setuptoolsSuggested packages:  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn python-genshiRecommended packages:  python-dev-allThe following NEW packages will be installed:  git git-man liberror-perl python-colorama python-distlib python-html5lib  python-pip python-setuptools0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.Need to get 3379 kB of archives.After this operation, 24,2 MB of additional disk space will be used.WARNING: The following packages cannot be authenticated!  liberror-perl git-man git python-colorama python-distlib python-html5lib  python-setuptools python-pipN: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionE: There are problems and -y was used without --force-yes
[/HTML]

Output of sudo apt-get autoremove
[HTML]darko@darko:~$ sudo apt-get autoremoveReading package lists... DoneBuilding dependency tree       Reading state information... Done0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.N: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensiondarko@darko:~$[/HTML]

Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[HTML]darko@darko:~$ sudo apt-get updateErr http://archives.ubuntu.com trusty-security InRelease  Err http://archives.ubuntu.com trusty-updates InRelease                    Err http://archives.ubuntu.com trusty-security Release.gpg                 Could not resolve 'archives.ubuntu.com'Err http://archives.ubuntu.com trusty-updates Release.gpg  Could not resolve 'archives.ubuntu.com'Ign http://archive.ubuntu.com trusty InReleaseGet:1 http://archive.ubuntu.com trusty Release.gpg [933 B]Hit http://archive.ubuntu.com trusty ReleaseIgn http://archive.ubuntu.com trusty ReleaseIgn http://archive.ubuntu.com trusty/main Sources/DiffIndexIgn http://archive.ubuntu.com trusty/restricted Sources/DiffIndexIgn http://archive.ubuntu.com trusty/universe Sources/DiffIndexIgn http://archive.ubuntu.com trusty/multiverse Sources/DiffIndexIgn http://archive.ubuntu.com trusty/main i386 Packages/DiffIndexIgn http://archive.ubuntu.com trusty/restricted i386 Packages/DiffIndexIgn http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndexIgn http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndexHit http://archive.ubuntu.com trusty/main Translation-enHit http://archive.ubuntu.com trusty/multiverse Translation-enHit http://archive.ubuntu.com trusty/restricted Translation-enHit http://archive.ubuntu.com trusty/universe Translation-enHit http://archive.ubuntu.com trusty/main Sources  Hit http://archive.ubuntu.com trusty/restricted SourcesHit http://archive.ubuntu.com trusty/universe SourcesHit http://archive.ubuntu.com trusty/multiverse SourcesHit http://archive.ubuntu.com trusty/main i386 PackagesHit http://archive.ubuntu.com trusty/restricted i386 PackagesHit http://archive.ubuntu.com trusty/universe i386 PackagesHit http://archive.ubuntu.com trusty/multiverse i386 PackagesIgn http://archive.ubuntu.com trusty/main Translation-en_USIgn http://archive.ubuntu.com trusty/multiverse Translation-en_USIgn http://archive.ubuntu.com trusty/restricted Translation-en_USIgn http://archive.ubuntu.com trusty/universe Translation-en_USFetched 933 B in 6s (141 B/s)                                                  Reading package lists... DoneN: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionN: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionW: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-security/InRelease  
W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  
W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'archives.ubuntu.com'
W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'archives.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
darko@darko:~$ [/HTML]

Etc...[/FONT][/COLOR]

---

### Post by dino99 on 2015-02-24
"W: Failed to fetch [http://archives.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://archives.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  "
so a few questions:
- are you really using Trusty ?
- have you the required compilation packages installed  ?
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by darko6 on 2015-02-24
Yesterday I had a message pops up "Requires installation of untrusted packages - This requires installing packages from unauthenticated sources". Then i tried to update system and it notifies me that i have no Pub Key installed. I tried to install them, tried literally everything, with no progress.

---

### Post by darko6 on 2015-02-24
1.Yes I am using trusthy. Can not access that link.
2.Dont know how to install that.

---

### Post by darko6 on 2015-02-24
I have installed Mac Os theme, though.

---

### Post by Bucky Ball on 2015-02-24
Please use regular code tags, not html tags. They keep the original formatting and much easier to decipher. Please see the last link in my signature for how.

---

### Post by ajgreeny on 2015-02-24
You seem also to have enabled a huge number of ppa and other non-standard repositories, according to the error shown in your autoremove command in post #3.  I don't think I have ever seen that many (112) enabled on a system before, and it is no surprise that you have problems updating your sources or installing anything; I think your system has a huge problem with versions of packages that are not standard.  Here's the error in code tags for easier reading.
```
darko@darko:~$ sudo apt-get autoremoveReading package lists... DoneBuilding dependency tree       Reading state information... Done0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'team-xbmc-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mc3man-trusty-media-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'moka-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'maarten-baert-simplescreenrecorder-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'audience-members-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-webdesigner.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-atraci-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'atareao-sunflower-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mqchael-pipelight-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'spideroak.com.sources.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'alexmurray-indicator-sensors-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mefrio-g-plymouthmanager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fyrmir-compiz-plugins-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-apps-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-wine-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'peterlevi-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'vala-team-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'thefanclub-ubuntu-after-install-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'thebernmeister-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ingalex-super-boot-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-earth.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-icons2-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-y-ppa-manager-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'lookit-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'adilson-experimental-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-themes-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kubuntu-ppa-backports-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'docky-core-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-tor-browser-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'opera.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'noobslab-icons-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'numix-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'screenlets-dev-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntuhandbook1-corebird-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'costales-folder-color-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'intellinuxgraphics.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-popcorntime-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'pipelight-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mozillateam-firefox-next-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skunk-pepper-flash-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-java-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'atareao-atareao-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'claudiocn-slm-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ravefinity-project-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nitrux-nitrux-artwork-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nilarimogard-webupd8-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'steam.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ehoover-compholio-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'shimmerproject-ppa-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'appgrid-stable-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fyrmir-livewallpaper-daily-trusty.list.disable' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensiondarko@darko:~$
```

Where on earth did you get your software-sources from? It looks as if you may have gone to [Sources List Generator]("http://repogen.simplylinux.ch/") or some other site and ticked the boxes to include everything on offer; not a good idea if you don't know what they are for or what the repos supply.

Just to get started again you could disable all those strange repos in one command with ```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.dbackup
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade
``` then we can figure out a longer term strategy for you.

---

### Post by darko6 on 2015-02-24
Bucky,
Sorry, my mistake.

ajgreeny,

Ok, I had writen that command in therminal and here is the output:
Ps. I have had a problem with writing a password for the first command.

```
darko@darko:~$ sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.dbackup[sudo] password for darko: 
1Sorry, try again.
[sudo] password for darko: 
Sorry, try again.
[sudo] password for darko: 
mv: cannot stat ‘/etc/apt/sources.list.d’: No such file or directory
darko@darko:~$ sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.dbackup
mv: cannot stat ‘/etc/apt/sources.list.d’: No such file or directory
darko@darko:~$ sudo apt-get update
Err http://archives.ubuntu.com trusty-security InRelease
  
Err http://archives.ubuntu.com trusty-updates InRelease
  
Err http://archives.ubuntu.com trusty-security Release.gpg
  Could not resolve 'archives.ubuntu.com'
Err http://archives.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'archives.ubuntu.com'
Ign http://archive.ubuntu.com trusty InRelease      
Get:1 http://archive.ubuntu.com trusty Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty Release
Ign http://archive.ubuntu.com trusty Release
Ign http://archive.ubuntu.com trusty/main Sources/DiffIndex
Ign http://archive.ubuntu.com trusty/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com trusty/universe Sources/DiffIndex
Ign http://archive.ubuntu.com trusty/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty/main Sources  
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/universe Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 933 B in 9s (98 B/s)                                                   
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-security/InRelease  


W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  


W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'archives.ubuntu.com'


W: Failed to fetch http://archives.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'archives.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.
darko@darko:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darko@darko:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darko@darko:~$ 



```
What next?

---

### Post by ajgreeny on 2015-02-24
I was assuming all those non-standard repos were sitting in /etc/apt/sources.list.d where they normally are, but perhaps in your case they are not.

To satisfy my curiosity how did you get such a strange lot of repos enabled?  And why?

Can you show the output of ```
ls /etc/apt/sources.list.d
``` If that says there is no such file or directory we are going to have to dig a lot deeper to get rid of those errant repos, as they must all be within the /etc/apt/sources.list file itself and will have to be commented out (to start with) by adding a # at the beginning of each line for those non-standard repos in that plain text file.

---

### Post by darko6 on 2015-02-24
ajgreeny,
"cannot access /etc/apt/sources.list.d: No such file or directory"

I was curios of Ubuntu and wanted to try a lot of programs(if that are the repos ). Dont know exactly what I have been instaling and from were. Dont remember.

---

### Post by ajgreeny on 2015-02-24
OK, so your /etc/apt/sources.list file must be long and very cluttered if those repos are not listed in a separate **sources.list.d** folder.

Can you please attach either a copy of the file renamed as **sources.list.txt** or just copy it and add it to your reply, in code-tags this time, not html-tags.  I will then try to look through it and comment out all the bad bits (as far as I can tell) and send it back to you.

Alternatively you could go to [Sources List Generator]("http://repogen.simplylinux.ch/") and make a completely new sources.list file yourself, but this time avoid some of the ppa repos that you can add even with that site.

If you want to try a few ppa repos stick with the more well known ones such as libreoffice, which I also use.  You can always add others later if you want by searching in either [www.googlubuntu.com](www.googlubuntu.com) or my own custom google search site [Ubu-Search]("https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao") as they usually come up with possible additions, but this time use fewer.

---

### Post by darko6 on 2015-02-24
Glad to, but I dont know what is repo. I will look your website for sure.
Do you mean etc/apt/sources.list.dbackup ?
Here it is:

```
/etc/apt/sources.list.dbackup/adilson-experimental-trusty.list.disable/etc/apt/sources.list.dbackup/adilson-experimental-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/adilson-experimental-trusty.list.save
/etc/apt/sources.list.dbackup/alexmurray-indicator-sensors-trusty.list.disable
/etc/apt/sources.list.dbackup/alexmurray-indicator-sensors-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/alexmurray-indicator-sensors-trusty.list.save
/etc/apt/sources.list.dbackup/appgrid-stable-trusty.list.disable
/etc/apt/sources.list.dbackup/appgrid-stable-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/appgrid-stable-trusty.list.save
/etc/apt/sources.list.dbackup/atareao-atareao-trusty.list.disable
/etc/apt/sources.list.dbackup/atareao-atareao-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/atareao-atareao-trusty.list.save
/etc/apt/sources.list.dbackup/atareao-sunflower-trusty.list.disable
/etc/apt/sources.list.dbackup/atareao-sunflower-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/atareao-sunflower-trusty.list.save
/etc/apt/sources.list.dbackup/audience-members-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/audience-members-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/audience-members-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/claudiocn-slm-trusty.list.disable
/etc/apt/sources.list.dbackup/claudiocn-slm-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/claudiocn-slm-trusty.list.save
/etc/apt/sources.list.dbackup/costales-folder-color-trusty.list.disable
/etc/apt/sources.list.dbackup/costales-folder-color-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/costales-folder-color-trusty.list.save
/etc/apt/sources.list.dbackup/docky-core-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/docky-core-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/docky-core-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/ehoover-compholio-trusty.list.disable
/etc/apt/sources.list.dbackup/ehoover-compholio-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/ehoover-compholio-trusty.list.save
/etc/apt/sources.list.dbackup/fyrmir-compiz-plugins-trusty.list.disable
/etc/apt/sources.list.dbackup/fyrmir-compiz-plugins-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/fyrmir-compiz-plugins-trusty.list.save
/etc/apt/sources.list.dbackup/fyrmir-livewallpaper-daily-trusty.list.disable
/etc/apt/sources.list.dbackup/fyrmir-livewallpaper-daily-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/fyrmir-livewallpaper-daily-trusty.list.save
/etc/apt/sources.list.dbackup/google-chrome.list.disable
/etc/apt/sources.list.dbackup/google-chrome.list.distUpgrade
/etc/apt/sources.list.dbackup/google-chrome.list.save
/etc/apt/sources.list.dbackup/google-earth.list.disable
/etc/apt/sources.list.dbackup/google-earth.list.distUpgrade
/etc/apt/sources.list.dbackup/google-earth.list.save
/etc/apt/sources.list.dbackup/google-webdesigner.list.disable
/etc/apt/sources.list.dbackup/google-webdesigner.list.distUpgrade
/etc/apt/sources.list.dbackup/google-webdesigner.list.save
/etc/apt/sources.list.dbackup/ingalex-super-boot-manager-trusty.list.disable
/etc/apt/sources.list.dbackup/ingalex-super-boot-manager-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/ingalex-super-boot-manager-trusty.list.save
/etc/apt/sources.list.dbackup/intellinuxgraphics.list.disable
/etc/apt/sources.list.dbackup/intellinuxgraphics.list.distUpgrade
/etc/apt/sources.list.dbackup/intellinuxgraphics.list.save
/etc/apt/sources.list.dbackup/kubuntu-ppa-backports-trusty.list.disable
/etc/apt/sources.list.dbackup/kubuntu-ppa-backports-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/kubuntu-ppa-backports-trusty.list.save
/etc/apt/sources.list.dbackup/lookit-daily-trusty.list.disable
/etc/apt/sources.list.dbackup/lookit-daily-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/lookit-daily-trusty.list.save
/etc/apt/sources.list.dbackup/maarten-baert-simplescreenrecorder-trusty.list.disable
/etc/apt/sources.list.dbackup/maarten-baert-simplescreenrecorder-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/maarten-baert-simplescreenrecorder-trusty.list.save
/etc/apt/sources.list.dbackup/mc3man-trusty-media-trusty.list.disable
/etc/apt/sources.list.dbackup/mc3man-trusty-media-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/mc3man-trusty-media-trusty.list.save
/etc/apt/sources.list.dbackup/medibuntu.list
/etc/apt/sources.list.dbackup/mefrio-g-plymouthmanager-trusty.list.disable
/etc/apt/sources.list.dbackup/mefrio-g-plymouthmanager-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/mefrio-g-plymouthmanager-trusty.list.save
/etc/apt/sources.list.dbackup/moka-stable-trusty.list.disable
/etc/apt/sources.list.dbackup/moka-stable-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/moka-stable-trusty.list.save
/etc/apt/sources.list.dbackup/mozillateam-firefox-next-trusty.list.disable
/etc/apt/sources.list.dbackup/mozillateam-firefox-next-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/mozillateam-firefox-next-trusty.list.save
/etc/apt/sources.list.dbackup/mqchael-pipelight-trusty.list.disable
/etc/apt/sources.list.dbackup/mqchael-pipelight-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/mqchael-pipelight-trusty.list.save
/etc/apt/sources.list.dbackup/nilarimogard-webupd8-trusty.list.disable
/etc/apt/sources.list.dbackup/nilarimogard-webupd8-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/nilarimogard-webupd8-trusty.list.save
/etc/apt/sources.list.dbackup/nitrux-nitrux-artwork-trusty.list.disable
/etc/apt/sources.list.dbackup/nitrux-nitrux-artwork-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/nitrux-nitrux-artwork-trusty.list.save
/etc/apt/sources.list.dbackup/noobslab-apps-trusty.list.disable
/etc/apt/sources.list.dbackup/noobslab-apps-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/noobslab-apps-trusty.list.save
/etc/apt/sources.list.dbackup/noobslab-icons2-trusty.list.disable
/etc/apt/sources.list.dbackup/noobslab-icons2-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/noobslab-icons2-trusty.list.save
/etc/apt/sources.list.dbackup/noobslab-icons-trusty.list.disable
/etc/apt/sources.list.dbackup/noobslab-icons-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/noobslab-icons-trusty.list.save
/etc/apt/sources.list.dbackup/noobslab-themes-trusty.list.disable
/etc/apt/sources.list.dbackup/noobslab-themes-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/noobslab-themes-trusty.list.save
/etc/apt/sources.list.dbackup/numix-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/numix-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/numix-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/opera.list.disable
/etc/apt/sources.list.dbackup/opera.list.distUpgrade
/etc/apt/sources.list.dbackup/opera.list.save
/etc/apt/sources.list.dbackup/peterlevi-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/peterlevi-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/peterlevi-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/pipelight-stable-trusty.list.disable
/etc/apt/sources.list.dbackup/pipelight-stable-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/pipelight-stable-trusty.list.save
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.disable
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.distUpgrade
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.save
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.disable
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.distUpgrade
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.save
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.disable
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.distUpgrade
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.save
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.disable
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
/etc/apt/sources.list.dbackup/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
/etc/apt/sources.list.dbackup/ravefinity-project-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/ravefinity-project-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/ravefinity-project-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/screenlets-dev-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/screenlets-dev-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/screenlets-dev-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/shimmerproject-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/shimmerproject-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/skunk-pepper-flash-trusty.list.disable
/etc/apt/sources.list.dbackup/skunk-pepper-flash-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/skunk-pepper-flash-trusty.list.save
/etc/apt/sources.list.dbackup/spideroak.com.sources.list.disable
/etc/apt/sources.list.dbackup/spideroak.com.sources.list.distUpgrade
/etc/apt/sources.list.dbackup/spideroak.com.sources.list.save
/etc/apt/sources.list.dbackup/steam.list.disable
/etc/apt/sources.list.dbackup/steam.list.distUpgrade
/etc/apt/sources.list.dbackup/steam.list.save
/etc/apt/sources.list.dbackup/team-xbmc-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/team-xbmc-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/team-xbmc-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/thebernmeister-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/thebernmeister-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/thebernmeister-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/thefanclub-ubuntu-after-install-trusty.list.disable
/etc/apt/sources.list.dbackup/thefanclub-ubuntu-after-install-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/thefanclub-ubuntu-after-install-trusty.list.save
/etc/apt/sources.list.dbackup/ubuntuhandbook1-corebird-trusty.list.disable
/etc/apt/sources.list.dbackup/ubuntuhandbook1-corebird-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/ubuntuhandbook1-corebird-trusty.list.save
/etc/apt/sources.list.dbackup/ubuntu-wine-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/ubuntu-wine-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/ubuntu-wine-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/vala-team-ppa-trusty.list.disable
/etc/apt/sources.list.dbackup/vala-team-ppa-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/vala-team-ppa-trusty.list.save
/etc/apt/sources.list.dbackup/webupd8team-atraci-trusty.list.disable
/etc/apt/sources.list.dbackup/webupd8team-atraci-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/webupd8team-atraci-trusty.list.save
/etc/apt/sources.list.dbackup/webupd8team-java-trusty.list.disable
/etc/apt/sources.list.dbackup/webupd8team-java-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/webupd8team-java-trusty.list.save
/etc/apt/sources.list.dbackup/webupd8team-popcorntime-trusty.list.disable
/etc/apt/sources.list.dbackup/webupd8team-popcorntime-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/webupd8team-popcorntime-trusty.list.save
/etc/apt/sources.list.dbackup/webupd8team-tor-browser-trusty.list.disable
/etc/apt/sources.list.dbackup/webupd8team-tor-browser-trusty.list.distUpgrade
/etc/apt/sources.list.dbackup/webupd8team-tor-browser-trusty.list.save
/etc/apt/sources.list.dbackup/webupd8team-y-ppa-manager-trusty.list.disable
```

---

### Post by ajgreeny on 2015-02-24
Whoops!  Sorry, I had forgotten that my first command renamed your **sources.list.d** folder when I asked you to run that **ls** command, so, of course, you no longer have that folder; it's now **sources.list.dbackup**.

Thanks for the listing of that renamed folder, however, which shows the repos (**repos** is the short name for **repositories** of ubuntu software which are the target of apt-get commands) you had enabled.
As I said, I have never seen anyone with so many and I don't think it is advisable to have all of them; just choose the few that really help you add software otherwise not available.

Having now got rid of all of those extra repositories for apt-get to use, you should now be able to run ```
sudo apt-get update
sudo apt-get upgrade
``` with out any problems and you may find that you can also now use the link given for linconnect, though it is possible that some package version conflicts may have appeared as a result of all those non-standard repositories you did have enabled before.

Sorry to say this but you really did drop yourself in a great big hole with all those extras, and it may be very difficult to overcome every conflict that you have.

Take care, and good luck!

---

### Post by darko6 on 2015-02-24
Tnx man. How to delete these repos?

---

### Post by ajgreeny on 2015-02-24
With that folder renamed you don't need to do anything else as the repos are already disabled and therefore not being used any more.

---

### Post by darko6 on 2015-02-25
I am affraid that problem still persist. I can not install nothing from Software Center. It keeps saying me " Requires installation of untrusted packages".  Should I reinstall it?

---

### Post by ajgreeny on 2015-02-25
I begin to think that a reinstall may be the simplest way out of this problem for you because adding all those extra repositories could mean that you have now far too many packages that are not the defaults for trusty, and the conflicts they have with other default packages, or other packages in non-standard repositories, may be causing all these difficulties for you.  There are also seem to be some repositories for which you do not have the security keys set up and with the number you had it will be impossible to sort this out quickly or figure out which ones, I think.

You could spend a lot more time trying to repair this than the time it would take to backup your files and reinstall the OS, so if it were my choice, I would bite the bullet and start again.  This time, however, please do not add masses of extra repositories with no thought to the problems it might add to your setup; just add the ones you really need.

As an example I use extra or ppa repos for:-
 
[LIST=1]
[*]get-iplayer for UK BBC TV & radio catch-up services
[*]libreoffice
[*]simple-screen-recorder
[*]audio-recorder
[*]indicator-keylock
[/LIST]
and even then I watch carefully the packages that they add and only install or upgrade the ones that are dependencies of the actual packages I installed, and for which I added the repositories.

Your sources were, I believe, totally unmanageable, as you had all those extra repositories just in case they were useful, but they added far too many packages which themselves gave you all those difficulties.

---

### Post by darko6 on 2015-02-25
What linux distribution do you recomend me? I am thinking of Elementary or Mint...

---

### Post by ajgreeny on 2015-02-25
I can't help with that as I have not seen either of them in action.

I much prefer Xubuntu to anything else I've tried.

---

### Post by darko6 on 2015-02-25
[COLOR=#000000][FONT=Arial]Thank you for all your assistance. It was helpfull. [/FONT][/COLOR]

---

