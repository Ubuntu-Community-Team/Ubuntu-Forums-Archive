---
title: "broke Ubuntu with SimpleBackup/Adobeflash issues"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by nipdatip on 2011-07-02
[FONT=monospace]00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCI


I'm new to Ubuntu.  I am using asus eeepc and installed the most recent ubuntu from the site last week using a flash drive.  There were a few bugs to work out involving power on/off and suspend functions but I followed a few tips to workaround. I also have had some problems with flash.  Yesterday Firefox and chrome would immediately crash when I opened them so I decided to do simple backup revert to on the etc file.  Now I cannot uninstall/install flash and when I try sudo apt-get upgrade I get

nipdatip@nipdatip-1015PEM:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
N: Ignoring file '01autoremove.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '99synaptic.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '99update-notifier.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '00trustcdrom.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20changelog.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '10periodic.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '15update-stamp.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '70debconf.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20archive.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '20dbus.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-audio-dev-ppa-natty.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'zeitgeist-ppa-natty.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-x-swat-x-updates-natty.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-x-swat-x-updates-natty.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'zeitgeist-ppa-natty.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-tweak-stable.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-audio-dev-ppa-natty.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-talkplugin.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-talkplugin.list.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.save.before_restore_2011-07-01_23.44.15.018027' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unmet dependencies. Try using -f.


Any help would definitely be appreciated.
[/FONT]

---

### Post by dino99 on 2011-07-02
thats the way noob learn :(

now you are ready for a fresh install again :)

---

### Post by nipdatip on 2011-07-02
Yep, that's what I was afraid of.  Install gnome or the whole Ubuntu enchilada?

---

