---
title: "Can't get update/upgrade to install"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-03-31
This happened last evening when I ran my usual updates.

I chroot to all my installs and run apt-get update.  The last two also get apt-get upgrade run.  This way they have all possible updates for the time frame.

Then I boot to them to make sure they work and if everything is cool I upgrade the rest.

In both my "throw away" installations the install end of the upgrade was a wreck centered on the upgraded "gconf2".  All sorts of things could not be configured because of gconf2 not being configured.

I can,t boot to either OS.  Normally or recovery.  Almost solid freeze as the only thing that works is Alt-SysRq-b.

I have tried, in this order, the following to no avail;
```

dpkg-reconfigure gconf2

dpkg-reconfigure -a

apt-get remove gconf2

apt-get install --reinstall gconf2

apt-get -f install gconf2

update-initramfs -u

apt-get update

apt-get -f upgrade

apt-get _f install

```
The abbreviated result of all this is
```

Package gconf2 is not configured yet.

 dbus
 gconf2-common
 libgconf2-4
 dbus-x11
 gconf2
 gnome-games-common
 aisleriot
 libatspi1.0-0
 at-spi
 bluez
 brasero-common
 libbrasero-media0
 brasero
 capplets-data
 empathy
 eog
 evince
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 evolution-couchdb
 file-roller
 gconf-defaults-service
 gconf-editor
 gedit
 gnome-bluetooth
 libgnome-window-settings1
 gnome-settings-daemon
 gnome-control-center
 gnome-keyring
 gnome-mahjongg
 gnome-media-common
 libgnome-media0
 libsoup-gnome2.4-1
 gstreamer0.10-plugins-good
 gnome-media
 python-pyatspi
 gnome-orca
 nautilus-data
 nautilus
 gnome-session-bin
 libgweather-common
 libgweather1
 libpanel-applet2-0
 gnome-panel-data
 gnome-panel
 gnome-session
 gnome-screensaver
 gnome-sudoku
 gnome-user-share
 gnomine
Processing was halted because there were too many errors.

```
I am a little nervous about updating the rest of my installs due to this.

If anyone has a clue please share it with me.

---

### Post by dino99 on 2010-03-31
few days ago we had a grub2 upgrade and the boot menu was redesign. When i validate the default developper's settings , i've seen that my hdd has been renamed and reordered.

previous name  --> next (actual)
  
        sdc         sdb
        sda         sdc
        sdb         sda

that's make me nervous but when i rebooted there were no issue.

---

### Post by ranch hand on 2010-03-31
I use custom entries of the symbolic type for all my debian based OS' and am not having any trouble at all with that issue.  I have 11 OS' on this external and none of them are having any trouble except these 2.

---

### Post by ranch hand on 2010-03-31
Finding no better solution I update/upgraded another installation.

Seeing that the problem seemed to be gconf2 I apt-get installed it first.  This helped some.
```

Package dbus-x11 is not configured yet.

Errors were encountered while processing:
 dbus
 bluez
 bluetooth
 bluez-utils
 dbus-x11
 gnome-keyring
 gnome-session-bin
 gnome-session
 gdm
 gnome-bluetooth
 gnome-screensaver
 hal
 totem-mozilla

```
The first line is the error on the setting up of all the problem packages.

Unfortunately the result is another unbootable OS.
The only message that I get before the total freeze is
> 
init: ureadahead-other main process (723) terminated with status 4

I may have to try this again on yet another installation installing gconf2 first and then dbus-X11 before upgrading the rest of the packages.

I just can not think of anything to try other than that.

---

### Post by ranch hand on 2010-03-31
I am currently trying to ruin another installation.

Installed gconf2, then dbus-x11.  This went well so I tried dbus gconf-editor gconf2-common gconf-defaults-service.

This did not go so well.  Failed on dbus.
> 
Setting up dbus (1.2.16-2ubuntu4) ...
The system user `messagebus' already exists. Exiting.
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
So  I go looking for this "system_bus_socket file".  This was very interesting.  I actually have two test drives and have Lubuntu B1 and three upgraded to 10.04 from Hardy installs on one and Hardy, Mandriva2009-1, Zenix (Xfce using 9.10 respin), StonerEdition1.2 (9.10 respin) Lubuntu A2, a Gnome Desktop using 9.10-mini upgraded to 10.04 and 5 installs of 10.04 in various forms.

The only one with that file is Mandriva.

Edit

Am not able to copy that file for some reason as root.

Edit

Can't copy file even with permissions changed as it is "special".

---

### Post by nanog on 2010-03-31
Are you saying that you chroot and upgrade all your installs from the same install? I would not recommend this because a bad package can hose all your installs.

I would try deleting your cached gconf2 (in /var/cache/apt -- see "currept deb" in my sig). If that does not work you can escalate by using dpkg to force removal/purge and if necessary wipe all traces of the pkg form spkg lists (see my sig for hints).

---

### Post by ranch hand on 2010-03-31
Ok,  I am not sure what you are saying here.

I am running apt-get update in chroot from this installation yes.  Isn't is downloading in the chrooted OS through its connection to the repos?  I use a number of mirrors so I can see which is being used and it all seems to match the OS being updated.

When I upgrade it should be using the updated package list from the update should it not?  Again the adress of the repo seems to bear this out.

---

### Post by ranch hand on 2010-03-31
I can not remove the package because of dependencies.  This was using "dpkg --force-remove-reinstreq -r gconf2".

I can rename them in nautilus but if I try to install them I am told that they are already at the latest version so I am missing some thing somewhere with that method.

---

### Post by ranch hand on 2010-03-31
```

root@sam-desktop:/# dpkg --force-remove-reinstreq -r gconf2
dpkg: dependency problems prevent removal of gconf2:
JUMP A BUNCH
dpkg: error processing gconf2 (--remove):
 dependency problems - not removing

```

---

### Post by nanog on 2010-03-31
You have a cached deb on whatever system you are using to chroot and this deb could be corrupt:

try this on the system/disk you are chrooting from: 

```
sudo rm /var/cache/apt/archives/gconf2
```

it will force a redownload of the package.

---

### Post by ranch hand on 2010-03-31
This is my main "production" OS during the daytime.  I am reluctant to do anything to it at all.

It works great, by the way.

I do not understand how this OS can effect the others.  Can you explain that?  I really am kind of new to this and probably don't understand all I know and what I know is not that much.

EDIT
Right now I am trying to create partitions for 2 more installs.  One  I will update/upgrade booted into it and the other chrooted from here.  It is the last incarnation of the B2 ISO-testing images that I am using.

---

### Post by nanog on 2010-04-01
.

---

### Post by ranch hand on 2010-04-01
This problem seems to have been in the script or what ever it is that controls how packages are installed.

I need to clean up my drive as some installs were just for testing one or two things and so  I booted to one and ran apt-get update and upgrade.

Same problem.  Cooked another install.

Went to another and updated an then apt-get install in this order
gconf2
dbus
gconf-common
dbus-x11

reran update and ran the upgrade with no problem.  Repeated this two more times on 2 other installs.  Every one that I did not do that on is fried.

Beats me.  At least I have the installs I need up to date.

---

### Post by ranch hand on 2010-04-02
I tried rescuing  from the 10.04b1 DVD live session with no good results.

Trying it from the rescue option did work on a number of installs though.  Never fooled with the DVD before.  That is a powerful tool.

Not sure it was quicker than reinstalling but it sure was fun to boot into the busted ones again.

Some of them just wouldn't budge though and I wiped them.  I have plenty for what I am doing although a couple need tweeking to test what I want to abuse them with now.

At least I have enough to go through this kind of thing again with out effecting this, my main install, adversely.

---

