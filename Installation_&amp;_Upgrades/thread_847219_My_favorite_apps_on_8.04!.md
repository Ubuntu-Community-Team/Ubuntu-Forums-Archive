---
title: "My favorite apps on 8.04!"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by Etamami on 2008-07-02
**OFFICE**
[Adobe Reader]("http://www.adobe.com") - opens PDF files (original)
Open in browser:
```
http://www.adobe.com/products/acrobat/readstep2_allversions.html
```

[Gnome Commander]("http://www.nongnu.org/gcmd/") - like Total Commander for windows!
Install in terminal:
```
sudo apt-get install gnome-commander
```

[Gnome Do]("http://do.davebsd.com/") - intelligent launcher tool!
Open in browser or download with synaptic:
```
http://do.davebsd.com/
```

[PeaZip]("http://peazip.sourceforge.net/") - WinRAR for linux, extracts almost everything
Download and install .deb here:
```
http://peazip.sourceforge.net/
```

[KompoZer]("http://www.kompozer.net/") - web author!
Download and install .deb file:
```
http://www.kompozer.net/download.php
```

[Nero Linux 3]("http://www.nero.com/eng/linux3.html") - Burning Rom, you have buy it! ;)
Or download this:
```
###
```

[Gmount-Iso]("http://www.crans.org/Syst%C3%A8meLinux/GmountIso") - like deamon tools for linux
```
sudo apt-get install gmountiso
```

[VirtualBox]("http://www.virtualbox.org") - running several virtual os
```
sudo apt-get install virtualbox
```

[WineHQ]("http://www.winehq.org/") - emulate windows
1st in terminal:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
then type:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
Now click and install it: [Install WineHQ]("apt://wine")

**AUDIO**
[Sondbird]("http://getsongbird.com/") - kind of iTunes for linux, based on mozilla!
Type in browser:
```
http://www.getdeb.net/app/Songbird
```

[Amarok]("http://amarok.kde.org/") - beloved music player!
```
sudo apt-get install amarok
```

[Last.FM]("http://last.fm") - Radio and music scrobbling!
Type in browser:
```
http://apt.last.fm/
```
or download this:
```
http://cdn.last.fm/client/Linux/lastfm_1.4.2.58240_i386.deb
```

[Audacity]("http://audacity.sourceforge.net/") - easy 2 use sound editor!
```
sudo apt-get install audacity
```

**VIDEO**
[VideoLAN]("http://www.videolan.org") (VLC) - plays everething without codecs required
```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

[SMPlayer]("http://smplayer.sourceforge.net/") - MPlayer with a well done GUI!
Download and install:
```
http://downloads.sourceforge.net/smplayer/smplayer_0.6.1_i386.deb
```

[Miro]("http://www.getmiro.com/") - internet TV!
```
sudo apt-get install miro
```

**INTERNET**
[Skype]("http://www.skype.com") - chat and talk over VoIP
Open in browser:
```
http://www.skype.com/go/getskype-linux-ubuntu
```

[aMSN]("#") - alternative to windows live messenger
Open in browser:
```
http://getdeb.net/release/2875
```

[Opera]("http://www.opera.com") - alternative to no mozilla
Open in browser:
```
http://getdeb.net/release/2867
```

[Seamonkey]("http://www.seamonkey-project.org/") - all-in-one browser!
```
sudo apt-get install seamonkey
```

[Flock]("http://flock.com/") - alternative to Firefox, with more social functions
Open in browser:
```
http://www.getdeb.net/release/2867
```

[FileZilla]("http://filezilla-project.org/") - FTP client
In terminal:
```
sudo apt-get install filezilla
```

[Azureus]("http://azureus.sourceforge.net/") - torrent client
In terminal:
```
sudo apt-get install azureus
```

[MugShot]("http://mugshot.org") - social website app
Update /etc/apt/sources.list with:
```
deb http://www.nighton.net/ hardy main
deb-src http://www.nighton.net/ hardy main

```
Run in terminal:
```
sudo apt-get update && sudo apt-get install mugshot
```

**STYLE**
Compiz Fusion
```
sudo apt-get install compiz compiz-backend-gconf compizconfig-settings-manager compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compiz-gnome
```

[Cairo-dock]("http://www.cairo-dock.org/") - dock for your Ubuntu
Open in terminal:
```
Cairo-Dock has its own repository. So, to install it, you just have to edit your sources (sudo gedit /etc/apt/sources.list) and add the repository:

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock 
or 
deb http://repository.cairo-dock.org/ubuntu gutsy cairo-dock (if you are under gutsy)

wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

[Avant Window Navigator]("#") - dock-like bar!
Run in terminal:
```
sudo gedit /etc/apt/sources.list

[I]add these at the bottom of the file and save it:
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main[/I]

sudo aptitude update

sudo aptitude install avant-window-navigator-bzr awn-core-applets-bzr
```

[Ubuntu Tweak]("http://ubuntu-tweak.com") - obviously
Run in terminal:
```
sudo gedit /etc/apt/sources.list
```
Add&save:
```
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
```
Run:
```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```


***Updated***

---

### Post by Etamami on 2008-07-02
**FIREFOX 3.0 EXTENSIONS**
[Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") - user scripts to change the look of websites
[Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108") - like greasemonkey
[All-in-One Sidebar]("https://addons.mozilla.org/en-US/firefox/addon/1027") - no more ext or dl windows
[Fast Dial]("https://addons.mozilla.org/en-US/firefox/addon/5721") - like Opera's fast dial
[Prism]("https://addons.mozilla.org/en-US/firefox/addon/6665") - mozilla lab project, enables to export web applications
[PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") - pdfs on web
[PrintPDF]("https://addons.mozilla.org/en-US/firefox/addon/5971") - enables to print websites to pdf file
[Gmail Manager]("https://addons.mozilla.org/en-US/firefox/addon/1320") - if you have gmail
[Yahoo! Mail Notifier]("https://addons.mozilla.org/en-US/firefox/addon/1264") - if you have yahoo
[GA?]("https://addons.mozilla.org/en-US/firefox/addon/5631") - is google analytics installed?
[Firefox Showcase]("https://addons.mozilla.org/en-US/firefox/addon/1810") - thumbnails of your tabs open

**FIREFOX 3.0 THEMES**
[Personas]("https://addons.mozilla.org/services/install.php?addon_id=personas") - let's you add images to window background
[Vista on XP]("https://addons.mozilla.org/en-US/firefox/addon/6839") (or Ubuntu) ;)

***Updated***

---

### Post by Etamami on 2008-07-22
**LATEST SCREENSHOT**
[[IMG]http://tn3-1.deviantart.com/fs32/300W/f/2008/200/1/b/Ubuntu804_20080718_by_smaci.png[/IMG]]("http://smaci.deviantart.com/art/Ubuntu804-20080718-92082871")

---

### Post by kajillin on 2008-07-23
DONT POST LINKS TO "PIRATED" COPYRIGHTED MATERIAL. That is illegal......

---

### Post by Etamami on 2008-07-23
> **kajillin said:**
> dont post links to "pirated" copyrighted material. That is illegal......

ok!

---

### Post by Karlos on 2008-07-23
> [Nero Linux 3]("http://www.nero.com/eng/linux3.html") - Burning Rom, you have buy it!

Why not use K3b or one of the other open source alternatives...

---

### Post by Etamami on 2008-07-23
> **Karlos said:**
> Why not use K3b or one of the other open source alternatives...

Well, under windows I was used to Nero, so that why, but now also someone recommended K3b to me, so I give it a shoot! :KS

---

### Post by Etamami on 2009-02-28
Updated for Ubuntu 8.10! :popcorn:

---

### Post by jens-mct on 2009-07-23
thx for miro en peazip :)

---

