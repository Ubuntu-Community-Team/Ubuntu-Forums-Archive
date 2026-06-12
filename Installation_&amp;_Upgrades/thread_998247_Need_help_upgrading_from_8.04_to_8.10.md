---
title: "Need help upgrading from 8.04 to 8.10"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by vegetarianshrimp on 2008-11-30
For some reason, the update manager isn't showing that 8.10 is available. 
Even when I set the "show distribution releases" to "normal releases" (in System > Preferences > Software Sources > Updates) update manager still doesn't show an option to upgrade to 8.10. Sometimes when I click the check for updates button in Update Manager, I get some error message about not being able to "fetch" this thing that has to do with Dell (I have a the Dell Inspiron Mini 9 laptop that came with Ubuntu). I don't think Dell is blocking it, but they might be.

Is there any way I can upgrade to 8.10 through the Update Manager, and if there isn't, how can I without using a CD (The mini 9 doesn't have a CD reader thingy)?

---

### Post by oilchangeguy on 2008-11-30
if your computer came pre-loaded with 8.04, you maybe should leave it alone. have you checked with dell support to see if it suggest an operating system change be done?

---

### Post by vegetarianshrimp on 2008-11-30
> **oilchangeguy said:**
> if your computer came pre-loaded with 8.04, you maybe should leave it alone. have you checked with dell support to see if it suggest an operating system change be done?

Maybe you're right, but I still want 8.10, so I'll keep trying. :)

---

### Post by crazyness003 on 2008-12-07
hello. i just noticed you need help from the 'stuck in an elevator..." thread.

I ran across [this webpage](http://blog.nixternal.com/2007.11.19/dist-upgrade-complete/), check it out. It says upgrade from gutsy -> hardy, but hardy -> intrepid should work the same.

Only caution i give you is the tutorial uses [Vim Editor]("http://en.wikipedia.org/wiki/Vim_editor")...which is a little hard to get used to for newcomers. (it runs from inside the terminal, zomg!)

Give that a shot, and also take a look at this: [http://groups.google.com/group/oalug/browse_thread/thread/d1b8e96bd957b856](http://groups.google.com/group/oalug/browse_thread/thread/d1b8e96bd957b856)

But the best way to do it is to update your Hardy to the latest and greatest, then do a Dist-Upgrade

Have funz

---

### Post by arrancaru on 2008-12-07
Do you have the ubuntu-desktop package still installed?

---

### Post by vegetarianshrimp on 2008-12-07
> **arrancaru said:**
> Do you have the ubuntu-desktop package still installed?
Sorry if I sound stupid, but what is that?

---

### Post by vegetarianshrimp on 2008-12-07
> I ran across this webpage, check it out.
Thanks but, when I do the first step, 

```
$ sudo vi /etc/apt/sources.list
```

I get this:

```
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
```

I think dell is blocking it, like I said before.

I did a search on my files for dell, and I got these results:
> /usr/share/ppd/splix/dell
/usr/share/dell-launcher
/usr/share/doc/dell-launcher
/usr/share/dellvideochat
/etc/pm/sleep.d/1-Dell-Launcher.sh
/usr/share/hal/fdi/policy/10osvendor/10-dell-laptop-brightness.fdi
/usr/share/hal/fdi/information/10freedesktop/10-dell-rfkill-switch-bluetooth.fdi
/usr/share/hal/fdi/information/10freedesktop/10-dell-rfkill-switch-wlan.fdi
/usr/share/hal/fdi/information/10freedesktop/10-dell-rfkill-switch-wwan.fdi
/usr/share/hal/fdi/information/10freedesktop/10-recall-battery-dell.fdi
/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-dell.fdi
/usr/share/hal/fdi/information/10freedesktop/30-keymap-dell.fdi
/etc/X11/xkb/geometry/dell
/usr/share/hotkey-setup/dell.hk
/usr/share/pixmaps/dell.png
/etc/firefox-3.0/dell.properties
/etc/sane.d/dell1600n_net.conf
/usr/share/desktop-switcher/dell-applications.menu
/usr/share/acpi-support/Dell Computer Corporation.config
/etc/xdg/autostart/dell-launcher.desktop
/usr/share/desktop-switcher/dell-launcher.desktop
/usr/share/acpi-support/Dell Inc..config
/usr/bin/dell-launcher
/var/lib/dpkg/info/dell-launcher.conffiles
/var/lib/dpkg/info/dell-launcher.list
/var/lib/dpkg/info/dell-launcher.md5sums
/usr/share/locale/de/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/es/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/fr/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/hu/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/it/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/ja/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/pl/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/pt_BR/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/ru/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/zh_CN/LC_MESSAGES/dell-launcher.mo
/usr/share/locale/zh_TW/LC_MESSAGES/dell-launcher.mo
/usr/share/foomatic/db/source/printer/Dell-M5200.xml
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_main_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_main_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_multiverse_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_multiverse_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_Release
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_Release.gpg
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_restricted_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_restricted_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_universe_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_universe_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_main_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_main_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_multiverse_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_multiverse_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_main_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_main_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_multiverse_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_multiverse_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_Release
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_Release.gpg
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_restricted_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_restricted_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_universe_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_universe_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_Release
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_Release.gpg
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_restricted_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_restricted_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_main_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_main_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_multiverse_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_multiverse_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_Release
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_Release.gpg
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_restricted_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_restricted_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_universe_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_universe_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_universe_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy_universe_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_main_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_main_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_multiverse_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_multiverse_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_Release
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_Release.gpg
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_restricted_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_restricted_source_Sources
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_universe_binary-lpia_Packages
/var/lib/apt/lists/dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_universe_source_Sources
/usr/share/foomatic/db/source/printer/Dell-S2500.xml
/usr/share/desktop-switcher/dell-settings.menu
/dev/disk/by-label/DellUtility
/usr/bin/dellvideochat
/usr/share/dellvideochat/dellvideochat
/var/lib/dpkg/info/dellvideochat.list
/usr/share/icons/dellvideochat.png
/usr/share/pixmaps/dellvideochat.png
/var/lib/dpkg/info/dellvideochat.postrm
/var/lib/dpkg/info/dellvideochat.preinst
/usr/share/applications/dellvideochat.desktop
/etc/xdg/sightspeed.com/Dell Video Chat.conf
/usr/lib/hal/hald-addon-dell-backlight
/usr/share/locale-langpack/en_AU/LC_MESSAGES/kmilo_delli8k.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/kmilo_delli8k.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/kmilo_delli8k.mo
/usr/lib/sane/libsane-dell1600n_net.la
/usr/lib/sane/libsane-dell1600n_net.so.1
/usr/lib/sane/libsane-dell1600n_net.so.1.0.19
/usr/share/dell-launcher/applications/ent-dell-lounge.desktop
/usr/lib/oem-config/post-install/yahoo-localize-dell

should I delete them?

---

### Post by crazyness003 on 2008-12-07
no. Do you have custromer support for your lappy. I'd run it across with them first. Then if they say "no you cannot upgrade to 8.10", then hang up and upgrade anyway :D

Dont delete the dell files. Just try to do what the link i sent you tells you to do.
> [COLOR=#666666]*:%s/gutsy/hardy then press enter*[/COLOR]Basically all you gotta do is change anywhere it says 'hardy' and replace it with 'interpid' (make sure theres no capitalisation)

EDIT: I just realized the vim editor that ships with Ubuntu is the cut-down version (i dont see a point to that. vim is tiny), so the command thing...i dont know how one would do it.
I'd call up dell or contact them somehow and *demand* to know how you could upgrade.

---

### Post by vegetarianshrimp on 2008-12-07
ok, so I downloaded VIM, and I typed in :%s/hardy/intrepid

I get this error:
> E486: Pattern not found: hardy 

what do I do now?

---

### Post by crazyness003 on 2008-12-07
you can do with gedit too. But id make a copy before you do anything (just in case ;) )
Okay, first type this in teminal ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup1
```This makes a backup.
Then ```
sudo gedit /etc/apt/sources.list
```When gedit opens, you can click "search" then "Replace" 
and in the "Search for:" boxy type 'hardy'
in the "Replace with:" box type 'intrepid'
Click find (it will highlight all the hits) then click "Replace All".
Then save and close.

Then in terminal type ```
sudo apt-get update
sudo apt-get dist-upgrade
```This should work (have not tested it, so use at your own risk)

A number of problems may arise: xorg may fail, you may get hickups from your Dell files, and you may void your waranty (possibly). SO, like i said earlier (and even earlier), run the question by Dell tech-support first.

EDIT: In case anything breaks, you can easily recover your old sources.list by issuing this command
```
suco cp /etc/apt/sources.list.backup1 /etc/apt/sources.list
```
This will copy the basckup you made earlier into the original file (restoring the original content)

I hope im right about this, if anyone can spot anything that will cause future trouble, please gimme input!

---

### Post by crazyness003 on 2008-12-07
> **vegetarianshrimp said:**
> ok, so I downloaded VIM, and I typed in :%s/hardy/intrepid

I get this error:


what do I do now?
Sorry, didnt see your post there. Vim is kinda a '1337' thing. I made a little howTo for using gedit instead (a bit more n00b friendly. Dont feel bad, Vim makes me nervous too)

Basically, "E486: Pattern not found: hardy" 			 		 means there's no mention of 'hardy' anywhere so it cant replace it with anything. Did you open the correct file?
would you mind posting your /etc/apt/sources.list file here (just copy and paste the text in a [noparse]```

```[/noparse] block)

---

### Post by vegetarianshrimp on 2008-12-07
ok thanks. I think i'll ask dell...

---

### Post by crazyness003 on 2008-12-07
> **vegetarianshrimp said:**
> ok thanks. I think i'll ask dell...
good choice. If it is something that they did, and you still wanna upgrade, and they wont help you, then the sky is the limit on opportunities (this is called hacking the oem). Good luck

---

### Post by hackel on 2009-01-22
The Dell Mini ships with an lpia (not i386) distribution.  The solution described here will not work.  In order to ugprade to intrepid, you will need to add the following lines to your sources.list file (and comment out any of the existing Dell repositories):

```
deb http://ports.ubuntu.com/ubuntu-ports intrepid main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports intrepid-security main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports intrepid-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports intrepid-backports main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports intrepid-proposed main restricted universe multiverse
```

Also, if you want Ubuntu Netbook Remix, add:
```
deb http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main
```

I've seen too many people struggling with this and upgrading the wrong way, or making it more difficult than it needs to be.  You may have to do some post-upgrade cleanup with this method, since you're not using Ubuntu's upgrade script, but it will work, and I've been happily running Intrepid on my Mini for the past month.

---

