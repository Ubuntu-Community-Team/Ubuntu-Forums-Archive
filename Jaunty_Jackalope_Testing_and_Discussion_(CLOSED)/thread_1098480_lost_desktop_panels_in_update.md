---
title: "lost desktop panels in update"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zika on 2009-03-17
after today's update (17.03.09.09:00) I lost desktop panels. ```
Mar 17 08:49:02 zika-desktop x-session-manager[3598]: WARNING: Could not launch application 'gnome-panel.desktop': Unable to start application: Failed to execute child process "gnome-panel" (No such file or directory)
```I tried to install it (it is not installed now, was running perfectly last night) but I get```
gnome-panel:
 Depends: gnome-panel-data (<1:2.26) but 1:2.26.0-0ubuntu1 is to be installed
 Recommends: gnome-applets but it is not going to be installed
 Recommends: evolution-data-server but it is not going to be installed
 Recommends: indicator-applet but it is not going to be installed
```it is not a big deal, today's update made screen faster and that counts ... ;) ATI ... :)

---

### Post by taavikko on 2009-03-17
You did an partial upgrade, that's why you have problems...

Wait few hours for repos to sort out, and then fix dependencies
safest bet would be reinstalling ubuntu-desktop meta-pkg

---

### Post by zika on 2009-03-17
> **taavikko said:**
> You did an partial upgrade, that's why you have problems...

Wait few hours for repos to sort out, and then fix dependencies
safest bet would be reinstalling ubuntu-desktop meta-pkg
synaptic did not warn me about that. I just reloaded and marked. in Ibex it did warn about partial upgrades ... thank You.

yes, ubuntu-desktop is now "not installed" ...

what is the best time of day to do updates to avoid similar situations ...?

---

### Post by taavikko on 2009-03-17
Just to be sure check dpkg.log for what have changed...

```
grep "2009-03-17" /var/log/dpkg.log
```

---

### Post by taavikko on 2009-03-17
> **zika said:**
> 
what is the best time of day to do updates to avoid similar situations ...?

It has nothing to do with time of day, when not to update.

I recommended updating via apt-get/aptitude on CLI to see if it is going to be partial upgrade...


```
The following packages will be REMOVED:
  ekiga evolution evolution-data-server evolution-exchange evolution-indicator
  evolution-plugins fast-user-switch-applet gnome-applets gnome-panel
  indicator-applet indicator-messages totem totem-dbg totem-gstreamer
  totem-mozilla totem-plugins ubuntu-desktop
The following packages will be upgraded:
  cpp-4.3 evince evolution-common evolution-data-server-common
  evolution-documentation-en fontconfig fontconfig-config g++-4.3 gcc-4.3
  gcc-4.3-base gnome-icon-theme gnome-panel-data jockey-common jockey-gtk
  libevdocument1 libevview1 libfontconfig1 libgcc1 libgfortran3 libgomp1
  libgweather-common libstdc++6 libstdc++6-4.3-dev libtotem-plparser12
  libwnck-common linux-headers-2.6.28-10-generic linux-image-2.6.28-10-generic
  linux-libc-dev totem-common xserver-xorg-video-ati xserver-xorg-video-radeon
31 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
Need to get 51.9MB of archives.
After this operation, 45.0MB disk space will be freed.
Do you want to continue [Y/n]? n

```

So I'll wait a while and try again when dependencies are sorted out...

synaptic should warn when it's going to remove something...

---

### Post by Nullack on 2009-03-17
Synpatic does warn if you pay attention to the details of the window presented when you hit apply.

---

### Post by zika on 2009-03-17
> **Nullack said:**
> Synpatic does warn if you pay attention to the details of the window presented when you hit apply.
I thought I did but obviously I was not smart enough ... ;)
```
Commit Log for Tue Mar 17 08:38:05 2009


Removed the following packages:
ekiga
evolution
evolution-data-server
evolution-exchange
evolution-indicator
evolution-plugins
fast-user-switch-applet
gnome-applets
gnome-panel
indicator-applet
indicator-messages
totem
totem-gstreamer
totem-mozilla
totem-plugins
ubuntu-desktop

Upgraded the following packages:
cpp-4.3 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
evince (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
evolution-common (2.25.92-0ubuntu2) to 2.26.0-0ubuntu1
evolution-data-server-common (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
evolution-documentation-en (2.25.92-0ubuntu2) to 2.26.0-0ubuntu1
fontconfig (2.6.0-1ubuntu4) to 2.6.0-1ubuntu9
fontconfig-config (2.6.0-1ubuntu4) to 2.6.0-1ubuntu9
g++-4.3 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
gcc-4.3 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
gcc-4.3-base (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
gfortran-4.3 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
gnome-icon-theme (2.25.90-0ubuntu1) to 2.26.0-0ubuntu1
gnome-panel-data (1:2.25.92-0ubuntu1) to 1:2.26.0-0ubuntu1
lib32gcc1 (1:4.3.3-5ubuntu3) to 1:4.3.3-5ubuntu4
lib32stdc++6 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
libevdocument1 (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
libevview1 (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
libfontconfig1 (2.6.0-1ubuntu4) to 2.6.0-1ubuntu9
libgcc1 (1:4.3.3-5ubuntu3) to 1:4.3.3-5ubuntu4
libgfortran3 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
libgomp1 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
libgweather-common (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
libstdc++6 (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
libstdc++6-4.3-dev (4.3.3-5ubuntu3) to 4.3.3-5ubuntu4
libtotem-plparser12 (2.25.92-0ubuntu1) to 2.26.0-0ubuntu1
libwnck-common (2.25.5-0ubuntu1) to 2.26.0-0ubuntu1
linux-headers-2.6.28-10-generic (2.6.28-10.32) to 2.6.28-10.33
linux-image-2.6.28-10-generic (2.6.28-10.32) to 2.6.28-10.33
linux-libc-dev (2.6.28-10.32) to 2.6.28-10.33
totem-common (2.25.92-0ubuntu2) to 2.26.0-0ubuntu1
xserver-xorg-video-ati (1:6.11.0+git20090310.945ccbbd-0ubuntu1) to 1:6.12.0-0ubuntu2
xserver-xorg-video-radeon (1:6.11.0+git20090310.945ccbbd-0ubuntu1) to 1:6.12.0-0ubuntu2
```

so, what is Your advice now. should I do anything once repositories get sorted or should I just leave Jaunty to heal itself ...?

---

### Post by zika on 2009-03-17
> **taavikko said:**
> I recommended updating via apt-get/aptitude on CLI to see if it is going to be partial upgrade...

I made myself used to do updates through Synaptic since that way I can see a log of changes made on a given day and I can go through that list days later. since this is my first Alpha testing this is a small bump on the road I hope ... or is it ...? :)

---

### Post by taavikko on 2009-03-17
> **zika said:**
> I made myself used to do updates through Synaptic since that way I can see a log of changes made on a given day and I can go through that list days later. since this is my first Alpha testing this is a small bump on the road I hope ... or is it ...? :)

Not a bad choice, using synaptic.
Logs are written even if you use apt/aptitude (see my post earlier ^^)

On alpha/beta releases there are always danger of something to go haywire.
so no one's safe...

You hit a minor bump on a road, so no worries,

Just install ubuntu-desktop again and you're cleared.
This dependency should solve itself in a short time..

---

### Post by zika on 2009-03-17
I've got out of a mess I've put myself into. ubuntu-desktop is now installed and the only thing missing is evolution (evolution{,-{exchange,indicator,plugins}}) that I really don't even use. I'll wait some time and try to install that also. thank You all very much for all the help!

---

### Post by taavikko on 2009-03-17
> **zika said:**
> I've got out of a mess I've put myself into. ubuntu-desktop is now installed and the only thing missing is evolution (evolution{,-{exchange,indicator,plugins}}) that I really don't even use. I'll wait some time and try to install that also. thank You all very much for all the help!

GNOME packages are going through the grinder at the moment, cause transition for the final release 2.26, should be cleared by tomorrow

Happy testing.

---

### Post by SketchyClown on 2009-03-17
There is no best time of day to upgrade. We're at the mercy of the repositories. If they are slow to update then you may get a ***"partial upgrade"*** warning. 

If this happens just go into **Software Sources** and pick a different repository that does not give you the partial upgrade warning.

I was noticing yesterday and this morning that people were getting updates but when I ran the update manager yesterday I got nothing until I changed to a different repository.

This morning it presented me with the partial option which I declined and again changed to a different repository. I was then able to get a full upgrade.

You are just asking for headaches by doing partials, IMHO.

---

### Post by zika on 2009-03-17
> **SketchyClown said:**
> There is no best time of day to upgrade. We're at the mercy of the repositories. If they are slow to update then you may get a ***"partial upgrade"*** warning. 

If this happens just go into **Software Sources** and pick a different repository that does not give you the partial upgrade warning.

I was noticing yesterday and this morning that people were getting updates but when I ran the update manager yesterday I got nothing until I changed to a different repository.

This morning it presented me with the partial option which I declined and again changed to a different repository. I was then able to get a full upgrade.

You are just asking for headaches by doing partials, IMHO.
I did not get "partial" willingly, it was my mistake, I did not see that some packages were to be removed which would signal me what was going on. synaptic is great tool but in that case I have to pay more attention. apt-get has better warning in such case. thank You for suggestions ...
I've solved that "crisis" and now I have more than 30 packages waiting because nautilus-cd-burner is on list to be removed. I'm waiting to see that situation resolved. there is even a kernel update waiting for that .. :)
```
The following packages have been kept back:
  brasero exiv2 libbrasero-media0
The following packages will be upgraded:
  alacarte base-passwd capplets-data gcalctool gconf-editor gimp gimp-data
  gnome-about gnome-cards-data gnome-control-center gnome-desktop-data
  gnome-games gnome-games-data gnome-menus gnome-mount kdelibs-bin kdelibs5
  kdelibs5-data libeel2-2 libeel2-data libgimp2.0 libgnome-desktop-2-11
  libgnome-menu2 libgnome-window-settings1 libgnomecanvas2-0
  libgnomecanvas2-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common
  libgnomevfs2-extra libvte-common libvte9 linux-headers-2.6.28-10 login
  notify-osd passwd python-cupshelpers python-gmenu python-vte
  system-config-printer-common system-config-printer-gnome tasksel
  tasksel-data tomboy vinagre zenity
46 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 57.0MB of archives.
After this operation, 1667kB of additional disk space will be used.
```

---

### Post by dBuster on 2009-03-17
Wow, after cruising the forums from work I came home after the hosed update this morning and did the following:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Followed up with:

```
sudo apt-get -f install ubuntu-desktop
```

And I am up and running now.  Latest releases including the latest kernel for Jaunty and I even have my panels back!!  

Evolution is even working for me!  Wahoo!!!

---

### Post by scaine on 2009-03-17
This is a handy link to check before you decide to do your upgrades, just to see what the devs are currently building...

[https://launchpad.net/ubuntu/jaunty/+builds](https://launchpad.net/ubuntu/jaunty/+builds)

There's a hell of a lot happening right now.

---

### Post by Vlammetje on 2009-03-21
I too have lost my panels in upgrading to Jaunty, however I am at a complete loss as to how to even open a terminal from  here? What do I do?

---

### Post by zika on 2009-03-21
> **Vlammetje said:**
> I too have lost my panels in upgrading to Jaunty, however I am at a complete loss as to how to even open a terminal from  here? What do I do?
"Ctrl-Alt-F2"->"gnome-terminal"

---

### Post by go7Ul1ai on 2009-03-21
> **Vlammetje said:**
> I too have lost my panels in upgrading to Jaunty, however I am at a complete loss as to how to even open a terminal from  here? What do I do?

Or if you installed GNOME Do then you would just have to summon it using super + space and then typing "terminal" and press enter. It saved me a few times when I was in trouble :)

---

### Post by Bert Mariën on 2009-03-21
> **Vlammetje said:**
> I too have lost my panels in upgrading to Jaunty, however I am at a complete loss as to how to even open a terminal from  here? What do I do?

Sometimes just a reboot does the trick.
Or just loggibg out and in again.

---

### Post by taavikko on 2009-03-21
Alt+F2 open a prompt,

Start terminal entering: **gnome-terminal**


Edit: wrong quote...

---

### Post by zika on 2009-03-21
> **Bert Mariën said:**
> Sometimes just a reboot does the trick.
Or just loggibg out and in again.
reboot can not help in this case because some packages were uninstalled.
Ctrl-Alt-F2->gnome-terminal->sudo apt-get install ubuntu-desktop

---

### Post by zika on 2009-03-22
**update: **I've removed files listed below. no need to loose time reading this but there is no way to erase a post. I was just a bit cautious due to the problems on the beginning of this thread. everything is OK, ubuntu was right, they were not needed any more, ... I hope ... :)

situation: synaptic and update-manager do not report any updates and offer no removals. apt-get recommends removing the following:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  dkms{u} gcj-4.3-base{u} libbackport-util-concurrent-java{u} 
  libcommons-codec-java{u} libdom4j-java{u} libexiv2-4{u} libgcj-bc{u} 
  libgcj-common{u} libgcj9-0{u} libgcj9-jar{u} libjaxen-java{u} 
  libjaxme-java{u} libjaxp1.3-java{u} libjaxp1.3-java-gcj{u} 
  libjdom1-java{u} liblog4j1.2-java{u} liblog4j1.2-java-gcj{u} 
  libsaxonb-java{u} libxerces2-java{u} libxerces2-java-gcj{u} 
  libxom-java{u} libxpp2-java{u} libxpp3-java{u} linux-headers-2.6.28-10{u} 
  linux-headers-2.6.28-10-generic{u} xulrunner-1.9.1{u} 
0 packages upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 204MB will be freed.
Do you want to continue? [Y/n/?]
```as far as I can see these are the packages that are no longer in use but some of them are newer that the ones that are also installed and have ubuntu logo in front of them in synaptic. dkms is left from install-uninstall of fglrx driver, kernel is already updated, many of them might be from Firefox3.1 that is now removed and replaced with FF3.6(nightly) which is just unpacked and not installed. what is Your recommendation: Y or N ... :) (synaptic lists just these 26 files as Installed (auto removable))

---

