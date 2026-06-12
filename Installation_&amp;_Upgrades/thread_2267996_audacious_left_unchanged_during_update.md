---
title: "audacious left unchanged during update"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2015-03-05
Hi all, 

I tried to run update as always: 

```
$ sudo apt-get update; sudo apt-get upgrade -V; sudo apt-get clean; sudo apt-get autoremove
```

and here is what I've got this time: 

> Packages left unchanged: 
   audacious (3.5.2.really.3.5.2-1 => 3.6-1~webupd8~trusty3)
   audacious-plugins (3.5.2.really.3.5.2-1.1 => 3.6-1~webupd8~trusty0)
updated 0, installed 0 new, 0 marked for delete and 2 not updated.

What is it and how to solve? 
Thanks ahead.

---

### Post by tgalati4 on 2015-03-05
Did you install audacity through a PPA or perhaps a *.deb file?  Look through the dependencies and see if any are stuck on an old version:

> 
tgalati4@Mint17 ~ $ apt-cache policy audacious
audacious:
  Installed: 3.4.3-1
  Candidate: 3.4.3-1
  Version table:
 *** 3.4.3-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
tgalati4@Mint17 ~ $ apt-cache depends audacious
audacious
  Depends: audacious-plugins
  Depends: dbus
    dbus:i386
  Depends: dbus-x11
    dbus-x11:i386
  Depends: gtk2-engines-pixbuf
  Depends: libaudclient2
  Depends: libaudcore1
  Depends: libc6
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libguess1
  Recommends: unzip
    unzip:i386
  Replaces: <libaudutil1>
  Replaces: <libaudutil1:i386>
  Replaces: <libsad2>
  Replaces: <libsad2:i386>
  Conflicts: audacious:i386


---

### Post by marchello_lippi2 on 2015-03-05
As far as I can remember, I installed audacious using apt-get install... 

> user1@pc:~$ apt-cache policy audacious
audacious:
  Installed: 3.5.2.really.3.5.2-1
  Candidate:    3.6-1~webupd8~trusty3
  Table of versions:
     3.6-1~webupd8~trusty3 0
        500 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) trusty/main i386 Packages
 *** 3.5.2.really.3.5.2-1 0
        100 /var/lib/dpkg/status
     3.4.3-1 0
        500 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages

What should I do now to solve it?

---

### Post by tgalati4 on 2015-03-05
Remove audacious:

```
sudo apt-get purge audacious
```

Then

```
sudo apt-get update
sudo apt-get upgrade

```

Pay attention to any messages.

Try to install audacious:
```
sudo apt-get install audacious
```

Verify the version:

```
apt-cache policy audacious
```

Then run it to make sure it works.  

In the future, run your script one command at a time so you can see what is going on.  One-line update scripts are convenient, but then you miss out on what is happening.

---

### Post by marchello_lippi2 on 2015-03-05
> user1@pc:~$ sudo apt-get purge audacious
[sudo] password for user1: 
Reading packages list... Done
Building dependencies tree
Reading information about state... Done
Packages to be REMOVED:
  audacious* lubuntu-desktop*
updated 0, installed 0 new, 2 marked for deleting and 1 not updated.
After this operation 1 655 kB will be free.
Proceed? [Y/n] n
Interrupted.

It is possible to remove only audacious but not the lubuntu-desktop ? 
Thanks.

---

### Post by tgalati4 on 2015-03-05
*lubuntu-desktop* is probably a meta package that pulls in everything that comes with the default lubuntu setup.

```
apt-cache depends lubuntu-desktop
```

Since you already have* lubuntu-desktop* installed, presumably, try removing lubuntu-desktop just by itself and see what gets removed.  Use the -s switch to simulate the action.

```
sudo apt-get -s remove lubuntu-desktop
```

> tgalati4@Mint17 ~ $ apt-cache search lubuntu-desktop
lubuntu-desktop - Lubuntu Desktop environment
tgalati4@Mint17 ~ $ apt-cache depends lubuntu-desktop
lubuntu-desktop
  Depends: abiword
  Depends: apport-gtk
  Depends: apturl
  Depends: audacious
  Depends: audacious-plugins
  Depends: blueman
.
.



Also check for any other issues that need fixing:

```
sudo apt-get install -f
```

There may be a packaging problem with *lubuntu-desktop* or *audacious* (or both).  Removing the existing version and installing the new version of *audacious* may break something else.  Proceed carefully.

---

### Post by marchello_lippi2 on 2015-03-05
Well, I prefer to stay with old audacious then. 

Could you please suggest any other idea how to solve it without touching lubuntu-desktop?

---

### Post by marchello_lippi2 on 2015-03-05
user1@pc:~$ apt-cache depends lubuntu-desktop     
lubuntu-desktop
  Dependencies (Depends): abiword
  Dependencies (Depends): apport-gtk
  Dependencies (Depends): apturl
  Dependencies (Depends): audacious
  Dependencies (Depends): audacious-plugins
  Dependencies (Depends): blueman
  Dependencies (Depends): cups-driver-gutenprint
    printer-driver-gutenprint
  Dependencies (Depends): desktop-file-utils
  Dependencies (Depends): dmz-cursor-theme
  Dependencies (Depends): evince
  Dependencies (Depends): ffmpegthumbnailer
  Dependencies (Depends): file-roller
  Dependencies (Depends): firefox
  Dependencies (Depends): fonts-droid
  Dependencies (Depends): fonts-liberation
  Dependencies (Depends): fonts-nanum
  Dependencies (Depends): galculator
  Dependencies (Depends): gdebi
  Dependencies (Depends): gecko-mediaplayer
  Dependencies (Depends): gnome-accessibility-themes
  Dependencies (Depends): gnome-disk-utility
  Dependencies (Depends): gnome-icon-theme-symbolic
  Dependencies (Depends): gnome-keyring
  Dependencies (Depends): gnome-mplayer
  Dependencies (Depends): gnome-system-tools
  Dependencies (Depends): gnome-time-admin
    gnome-system-tools
  Dependencies (Depends): gnumeric
  Dependencies (Depends): gpicview
  Dependencies (Depends): gucharmap
  Dependencies (Depends): guvcview
  Dependencies (Depends): gvfs-backends
  Dependencies (Depends): gvfs-fuse
  Dependencies (Depends): hardinfo
  Dependencies (Depends): ibus
  Dependencies (Depends): indicator-application-gtk2
  Dependencies (Depends): language-selector-gnome
  Dependencies (Depends): leafpad
  Dependencies (Depends): libfm-modules
  Dependencies (Depends): libgtk2-perl
  Dependencies (Depends): libmtp-runtime
  Dependencies (Depends): light-locker
  Dependencies (Depends): light-locker-settings
  Dependencies (Depends): lubuntu-core
  Dependencies (Depends): lubuntu-default-session
  Dependencies (Depends): lubuntu-software-center
  Dependencies (Depends): lxappearance
  Dependencies (Depends): lxappearance-obconf
  Dependencies (Depends): lxinput
  Dependencies (Depends): lxlauncher
  Dependencies (Depends): lxpanel-indicator-applet-plugin
  Dependencies (Depends): lxrandr
  Dependencies (Depends): lxsession-default-apps
  Dependencies (Depends): lxsession-logout
  Dependencies (Depends): lxshortcut
  Dependencies (Depends): lxtask
  Dependencies (Depends): lxterminal
  Dependencies (Depends): mobile-broadband-provider-info
  Dependencies (Depends): modemmanager
    wader-core
  Dependencies (Depends): mtpaint
  Dependencies (Depends): network-manager-gnome
  Dependencies (Depends): ntp
  Dependencies (Depends): obconf
  Dependencies (Depends): pidgin
  Dependencies (Depends): pm-utils
  Dependencies (Depends): python-gudev
  Dependencies (Depends): scrot
  Dependencies (Depends): simple-scan
  Dependencies (Depends): software-properties-gtk
  Dependencies (Depends): sylpheed
  Dependencies (Depends): sylpheed-doc
  Dependencies (Depends): sylpheed-i18n
  Dependencies (Depends): sylpheed-plugins
  Dependencies (Depends): synaptic
  Dependencies (Depends): system-config-printer-gnome
  Dependencies (Depends): transmission
  Dependencies (Depends): ubuntu-release-upgrader-gtk
  Dependencies (Depends): update-notifier
  Dependencies (Depends): usb-creator-gtk
  Dependencies (Depends): usb-modeswitch
  Dependencies (Depends): whoopsie
  Dependencies (Depends): wvdial
  Dependencies (Depends): x11-utils
  Dependencies (Depends): xdg-user-dirs
  Dependencies (Depends): xdg-user-dirs-gtk
  Dependencies (Depends): xfburn
  Dependencies (Depends): xfce4-notifyd
  Dependencies (Depends): xfce4-power-manager
  Dependencies (Depends): xpad
  Dependencies (Depends): xterm
  Dependencies (Depends): xul-ext-ubufox
  Dependencies (Depends): xz-utils

---

### Post by marchello_lippi2 on 2015-03-05
user1@pc:~$ sudo apt-get -s remove lubuntu-desktop
Reading packages list... Done
Building dependencies tree 
Reading information about state... Done 
Packages to be REMOVED: 
  lubuntu-desktop
updated 0, installed 0 new, 1 marked for deleting and 2 not updated.
Remv lubuntu-desktop [0.55]

---

### Post by marchello_lippi2 on 2015-03-05
user1@pc:~$ sudo apt-get install -f
Reading packages list... Done
Building dependencies tree 
Reading information about state... Done 
updated 0, installed 0 new, 0 marked for deleting and 2 not updated.



Any suggestions?

---

### Post by mc4man on 2015-03-05
go - 
```
sudo apt-get purge audacious audacious-plugins
```
```
sudo apt-get update
```
```
sudo apt-get install audacious lubuntu-desktop
```

Edit - what you could/should have done is this, aud 3.6 has a new libaudcore version (libaudcore3) vs. 3.5 which produced/used libaudcore2
apt-get upgrade does not handle that well, synaptic would of likely been fine

```
sudo apt-get dist-upgrade
```

---

### Post by marchello_lippi2 on 2015-03-05
- Doctor, something is wrong with my eye, could you please look at it? 
- Yes, sure, we need to cut your head, to change your eye and then put your head back! 

I will stay with my old audacious then... 
Thanks.

---

### Post by mc4man on 2015-03-05
> **marchello_lippi2 said:**
> - Doctor, something is wrong with my eye, could you please look at it? 
- Yes, sure, we need to cut your head, to change your eye and then put your head back! 

I will stay with my old audacious then... 
Thanks.
Not sure what you're implying but if one chooses to use a ppa(s) then it's on the user to understand that apt-get upgrade is often the wrong command
(I do attempt to make that known to any users of ppa's I have, whether they choose to actually read the page is out of my or any other ppa's control & to some extent caring.

---

### Post by marchello_lippi2 on 2015-03-05
[**[COLOR=#DD4814][B]mc4man**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=320715"),

> sudo apt-get dist-upgrade

This solved my problem completely. That was just my bad understanding of how does ppa work. 

Thank you very much.

---

### Post by marchello_lippi2 on 2015-03-05
P.S.: I should add that attempt to remove all desktop with audio player was very confusing... I do not pretend to look like advanced user.

---

### Post by mc4man on 2015-03-05
That's ok - 
 Whenever an apt-get upgrade declines to upgrade a package(s) then see what apt-get dist-upgrade does.  If desired you can always simulate the upgrade to see if it works out ok. 
Ex.
```
sudo apt-get -s dist-upgrade
```
It it completes ok without error or removing something that it should then you can re-run removing the -s to actually upgrade

---

