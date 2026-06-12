---
title: "Problem on running  sudo apt-get update ; sudo apt-get upgrade"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by satimis on 2016-01-24
Hi all,

Ubuntu 14.04 desktop

On running
&#10219; sudo apt-get update ; sudo apt-get upgrade

it complained```

....
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'google-chrome.list.spare' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.spare' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

&#10219; ls /etc/apt/sources.list.d/```

google-chrome.list.spare  peterlevi-ppa-trusty.list

```

&#10219; cat /etc/apt/sources.list.d/google-chrome.list.spare ```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

```

&#10219; cat /etc/apt/sources.list.d/peterlevi-ppa-trusty.list ```

deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main

```

comment out```

# deb http://dl.google.com/linux/chrome/deb/ stable main

```

It still complained on running "sudo apt-get update ; sudo apt-get upgrade" ```

....
N: Ignoring file 'google-chrome.list.spare' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.spare' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

Please advise how to fix the problem?

What will be the use of;
/etc/apt/sources.list.d/peterlevi-ppa-trusty.list

Thanks

Regards
satimis

---

### Post by CantankRus on 2016-01-25
Any idea why the file has a ".spare" extension?

The file here is...
```
/etc/apt/sources.list.d/google-chrome.list
```

Do you have that file?
```
cat  /etc/apt/sources.list.d/google-chrome.list
```

If not you can rename your **.spare** file....
```
sudo mv /etc/apt/sources.list.d/google-chrome.list.spare /etc/apt/sources.list.d/google-chrome.list
```

PS: The error isn't coming from peterlevi-ppa-trusty.list which is the ppa for Variety wallpaper changer.

---

### Post by satimis on 2016-01-25
> **CantankRus said:**
> Any idea why the file has a ".spare" extension?

The file here is...
```
/etc/apt/sources.list.d/google-chrome.list
```

Do you have that file?
```
cat  /etc/apt/sources.list.d/google-chrome.list
```

If not you can rename your **.spare** file....
```
sudo mv /etc/apt/sources.list.d/google-chrome.list.spare /etc/apt/sources.list.d/google-chrome.list
```

PS: The error isn't coming from peterlevi-ppa-trusty.list which is the ppa for Variety wallpaper changer.

Hi,

Thanks for your advice.

I have no idea how and when it came?  This is the host OS of VirtualBox

On VM Ubuntu 14.04 desktop there is no such a file.

VM
&#10219; ls /etc/apt/sources.list.d/```

mc3man-trusty-media-trusty.list

```

&#10219; cat /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list ```

deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

```


Performed following steps as advised.
&#10219; sudo mv /etc/apt/sources.list.d/google-chrome.list.spare /etc/apt/sources.list.d/google-chrome.list

Reboot PC

&#10219; sudo apt-get update ; sudo apt-get upgrade```

....
....
Ign http://extras.ubuntu.com trusty/main Translation-en_HK
Ign http://extras.ubuntu.com trusty/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```

The error message gone.  Thanks

Regards
satimis

---

### Post by CantankRus on 2016-01-25
You will get different outputs for 
 ```
ls /etc/apt/sources.list.d/
```
on different installs because these are third party ppas you have added (enabled or disabled)

eg I have added many ppas over time while only a couple are still enabled...
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] ls /etc/apt/sources.list.d/**
alessandro-blarco-ppa-trusty.list
alessandro-blarco-ppa-trusty.list.save
alexmurray-indicator-sensors-daily-trusty.list
alexmurray-indicator-sensors-daily-trusty.list.save
atareao-atareao-trusty.list
atareao-atareao-trusty.list.save
atareao-nautilus-extensions-trusty.list
atareao-nautilus-extensions-trusty.list.save
bhdouglass-indicator-remindor-trusty.list
bhdouglass-indicator-remindor-trusty.list.save
bytr-concise-trusty.list
bytr-concise-trusty.list.save
costales-anoise-trusty.list
costales-anoise-trusty.list.save
costales-folder-color-trusty.list
costales-folder-color-trusty.list.save
dockbar-main-ppa-trusty.list
dockbar-main-ppa-trusty.list.save
dwrj87-mmex-test-trusty.list
dwrj87-mmex-test-trusty.list.save
elementary-os-daily-trusty.list
elementary-os-daily-trusty.list.save
elementary-os-unstable-upstream-trusty.list
elementary-os-unstable-upstream-trusty.list.save
evolve-os-ppa-trusty.list
evolve-os-ppa-trusty.list.save
ffmulticonverter-stable-trusty.list
ffmulticonverter-stable-trusty.list.save
fixnix-indicator-systemtray-unity-trusty.list
fixnix-indicator-systemtray-unity-trusty.list.save
fontforge-fontforge-trusty.list
fontforge-fontforge-trusty.list.save
fyrmir-livewallpaper-daily-trusty.list
fyrmir-livewallpaper-daily-trusty.list.save
geogebra.list
geogebra.list.save
getdeb.list
getdeb.list.save
google-chrome.list
google-chrome.list.save
google.list
google.list.save
graphics-drivers-ppa-trusty.list
graphics-drivers-ppa-trusty.list.save
gurqn-systray-trusty-trusty.list
gurqn-systray-trusty-trusty.list.save
hda-me-xscreensaver-trusty.list
hda-me-xscreensaver-trusty.list.save
jon-severinsson-ffmpeg-trusty.list
jon-severinsson-ffmpeg-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
kupfer-team-ppa-trusty.list
kupfer-team-ppa-trusty.list.save
landronimirc-skippy-xd-daily-trusty.list
landronimirc-skippy-xd-daily-trusty.list.save
linvinus-altyo-trusty.list
linvinus-altyo-trusty.list.save
lubuntu-dev-lubuntu-daily-trusty.list
lubuntu-dev-lubuntu-daily-trusty.list.save
maarten-baert-simplescreenrecorder-trusty.list
maarten-baert-simplescreenrecorder-trusty.list.save
mjasnik-ppa-trusty.list
mjasnik-ppa-trusty.list.save
msclrhd-gmail-cainteoir-trusty.list
msclrhd-gmail-cainteoir-trusty.list.save
mscore-ubuntu-mscore-stable-trusty.list
mscore-ubuntu-mscore-stable-trusty.list.save
niko2040-e19-trusty.list
niko2040-e19-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
noobslab-apps-trusty.list
noobslab-apps-trusty.list.save
noobslab-deepin-sc-trusty.list
noobslab-deepin-sc-trusty.list.save
noobslab-indicators-trusty.list
noobslab-indicators-trusty.list.save
noobslab-nemo-trusty.list
noobslab-nemo-trusty.list.save
noobslab-themes-trusty.list
noobslab-themes-trusty.list.save
opera-beta.list.save
opera-developer.list
opera-developer.list.save
opera.list
opera.list.save
oscam-ppa-trusty.list
oscam-ppa-trusty.list.save
pachulo-redshift-backports-trusty.list
pachulo-redshift-backports-trusty.list.save
peterlevi-ppa-trusty.list
peterlevi-ppa-trusty.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list.save
ricotz-docky-trusty.list
ricotz-docky-trusty.list.save
rvm-smplayer-trusty.list.save
team-xbmc-ppa-trusty.list
team-xbmc-ppa-trusty.list.save
teejee2008-ppa-trusty.list
teejee2008-ppa-trusty.list.save
ubuntu-mate-dev-ppa-trusty.list
ubuntu-mate-dev-ppa-trusty.list.save
ubuntu-mate-dev-trusty-mate-trusty.list
ubuntu-mate-dev-trusty-mate-trusty.list.save
ubuntu-wine-ppa-trusty.list
ubuntu-wine-ppa-trusty.list.save
umang-indicator-stickynotes-trusty.list
umang-indicator-stickynotes-trusty.list.save
videolan-stable-daily-trusty.list
videolan-stable-daily-trusty.list.save
vincent-c-conky-trusty.list
vincent-c-conky-trusty.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.save
webupd8team-nemo-trusty.list
webupd8team-nemo-trusty.list.save
webupd8team-themes-trusty.list
webupd8team-themes-trusty.list.save
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.save
xorg-edgers-ppa-trusty.list
xorg-edgers-ppa-trusty.list.save
yktooo-ppa-trusty.list
yktooo-ppa-trusty.list.save
yorba-ppa-trusty.list
yorba-ppa-trusty.list.save
ytvwld-syncthing-trusty.list
ytvwld-syncthing-trusty.list.save

```

---

### Post by satimis on 2016-01-25
> **CantankRus said:**
> You will get different outputs for 
 ```
ls /etc/apt/sources.list.d/
```
on different installs because these are third party ppas you have added (enabled or disabled)

eg I have added many ppas over time while only a couple are still enabled...
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] ls /etc/apt/sources.list.d/**
alessandro-blarco-ppa-trusty.list
alessandro-blarco-ppa-trusty.list.save
alexmurray-indicator-sensors-daily-trusty.list
alexmurray-indicator-sensors-daily-trusty.list.save
atareao-atareao-trusty.list
atareao-atareao-trusty.list.save
atareao-nautilus-extensions-trusty.list
atareao-nautilus-extensions-trusty.list.save
bhdouglass-indicator-remindor-trusty.list
bhdouglass-indicator-remindor-trusty.list.save
bytr-concise-trusty.list
bytr-concise-trusty.list.save
costales-anoise-trusty.list
costales-anoise-trusty.list.save
costales-folder-color-trusty.list
costales-folder-color-trusty.list.save
dockbar-main-ppa-trusty.list
dockbar-main-ppa-trusty.list.save
dwrj87-mmex-test-trusty.list
dwrj87-mmex-test-trusty.list.save
elementary-os-daily-trusty.list
elementary-os-daily-trusty.list.save
elementary-os-unstable-upstream-trusty.list
elementary-os-unstable-upstream-trusty.list.save
evolve-os-ppa-trusty.list
evolve-os-ppa-trusty.list.save
ffmulticonverter-stable-trusty.list
ffmulticonverter-stable-trusty.list.save
fixnix-indicator-systemtray-unity-trusty.list
fixnix-indicator-systemtray-unity-trusty.list.save
fontforge-fontforge-trusty.list
fontforge-fontforge-trusty.list.save
fyrmir-livewallpaper-daily-trusty.list
fyrmir-livewallpaper-daily-trusty.list.save
geogebra.list
geogebra.list.save
getdeb.list
getdeb.list.save
google-chrome.list
google-chrome.list.save
google.list
google.list.save
graphics-drivers-ppa-trusty.list
graphics-drivers-ppa-trusty.list.save
gurqn-systray-trusty-trusty.list
gurqn-systray-trusty-trusty.list.save
hda-me-xscreensaver-trusty.list
hda-me-xscreensaver-trusty.list.save
jon-severinsson-ffmpeg-trusty.list
jon-severinsson-ffmpeg-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
kupfer-team-ppa-trusty.list
kupfer-team-ppa-trusty.list.save
landronimirc-skippy-xd-daily-trusty.list
landronimirc-skippy-xd-daily-trusty.list.save
linvinus-altyo-trusty.list
linvinus-altyo-trusty.list.save
lubuntu-dev-lubuntu-daily-trusty.list
lubuntu-dev-lubuntu-daily-trusty.list.save
maarten-baert-simplescreenrecorder-trusty.list
maarten-baert-simplescreenrecorder-trusty.list.save
mjasnik-ppa-trusty.list
mjasnik-ppa-trusty.list.save
msclrhd-gmail-cainteoir-trusty.list
msclrhd-gmail-cainteoir-trusty.list.save
mscore-ubuntu-mscore-stable-trusty.list
mscore-ubuntu-mscore-stable-trusty.list.save
niko2040-e19-trusty.list
niko2040-e19-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
noobslab-apps-trusty.list
noobslab-apps-trusty.list.save
noobslab-deepin-sc-trusty.list
noobslab-deepin-sc-trusty.list.save
noobslab-indicators-trusty.list
noobslab-indicators-trusty.list.save
noobslab-nemo-trusty.list
noobslab-nemo-trusty.list.save
noobslab-themes-trusty.list
noobslab-themes-trusty.list.save
opera-beta.list.save
opera-developer.list
opera-developer.list.save
opera.list
opera.list.save
oscam-ppa-trusty.list
oscam-ppa-trusty.list.save
pachulo-redshift-backports-trusty.list
pachulo-redshift-backports-trusty.list.save
peterlevi-ppa-trusty.list
peterlevi-ppa-trusty.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list.save
ricotz-docky-trusty.list
ricotz-docky-trusty.list.save
rvm-smplayer-trusty.list.save
team-xbmc-ppa-trusty.list
team-xbmc-ppa-trusty.list.save
teejee2008-ppa-trusty.list
teejee2008-ppa-trusty.list.save
ubuntu-mate-dev-ppa-trusty.list
ubuntu-mate-dev-ppa-trusty.list.save
ubuntu-mate-dev-trusty-mate-trusty.list
ubuntu-mate-dev-trusty-mate-trusty.list.save
ubuntu-wine-ppa-trusty.list
ubuntu-wine-ppa-trusty.list.save
umang-indicator-stickynotes-trusty.list
umang-indicator-stickynotes-trusty.list.save
videolan-stable-daily-trusty.list
videolan-stable-daily-trusty.list.save
vincent-c-conky-trusty.list
vincent-c-conky-trusty.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.save
webupd8team-nemo-trusty.list
webupd8team-nemo-trusty.list.save
webupd8team-themes-trusty.list
webupd8team-themes-trusty.list.save
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.save
xorg-edgers-ppa-trusty.list
xorg-edgers-ppa-trusty.list.save
yktooo-ppa-trusty.list
yktooo-ppa-trusty.list.save
yorba-ppa-trusty.list
yorba-ppa-trusty.list.save
ytvwld-syncthing-trusty.list
ytvwld-syncthing-trusty.list.save

```
Hi,

Your advice noted.  Thanks

Regards
satimis

---

