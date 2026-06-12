---
title: "weird apt-get /aptitude behaviour probably simple explanation."
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by funkyade on 2006-10-30
Whenever I remove or install new packages I get this -
```
The following packages were automatically installed and are no longer required:
  xfprint4 libchewing3-data libgoffice-gtk-0-3 libgoffice-0-common libxine-extracodecs libots0 xfce4-xkb-plugin scim-chewing xfce4-verve-plugin
  xfce4-panel libtagc0 system-config-printer libaiksaurusgtk-1.2-0c2a xfce4-taskmanager xfce4-mailwatch-plugin libaiksaurus-1.2-0c2a scim-hangul
  falconseye-data xfce4-notes-plugin gnumeric-common orage xubuntu-artwork-usplash python-exo xfce4-appfinder gnumeric-gtk xfce4-battery-plugin
  libchewing3 apt-howto-common xfce4-weather-plugin libwpd-stream8c2a xfce4-netload-plugin thunar-archive-plugin libt1-5 libaiksaurus-1.2-data thunar
  xfce4-icon-theme libgdome2-0 xfce4-screenshooter-plugin xfce4-systemload-plugin thunar-media-tags-plugin mousepad xfce4-dict-plugin
  xfce4-fsguard-plugin xfce4-cpugraph-plugin xfce4-smartbookmark-plugin xfdesktop4 libgdome2-cpp-smart0c2a python-cups libanthy0
  xfce4-quicklauncher-plugin scim-pinyin xfce4-utils xubuntu-docs xfce4-mixer-alsa libgtkmathview0c2a apt-howto-en xfce4-mount-plugin xfburn
  xfce4-session xfce4-mixer xfce4-clipman-plugin liballegro4.2 libthunar-vfs-1-2 libxine1
Use 'apt-get autoremove' to remove them.

```

a bit weird because I am running xubuntu!

I reinstalled the ubuntu-desktop package via aptitude (to use with Beryl incidentally) and this 'problem' went away. However, I then used apt-get (just out of absent mindedness as I usually use aptitude) and voila, it is back in apt-get, but not in aptitude!!!!!!

It doen't affect anything as far as I know but it is a bit disconcerting, is this a bug in the apt backend? I've googled it etc... but not found anything.

Any ideas...?:-k

---

### Post by blind0wl on 2006-10-30
Have you tried running apt-get autoremove?

---

### Post by mixmaster on 2006-10-30
I believe aptitude and apt-get maintain different information about installed software, so it is possible for one to be bad without the other.  Try running the suggested fixup command.

---

### Post by funkyade on 2006-10-30
```
apt-get autoremove
``` does what it says on the tin!

Removes xfwm, leaving me with no xubuntu!

a simple -

```
sudo aptitude install xubuntu-desktop
``` gets it back. However, apt-get is still showing the same autoremove thing.

I know about aptitude and apt-get keeping track of packages differently that's whhy I use aptitude as it handles dependencies better...

Anyway, I will stay away from apt-get for now...

Is there a way to clear this from apt-get, flushing its cache or something? I don't fancy pinning all these packages as that may affect upgrades.

Thanks

---

### Post by skorpio11 on 2006-11-19
Any help with this issue. Experiencing it myself

---

### Post by elettronicha on 2006-11-19
Generally I use aptitude and have the same issue with apt-get:
```
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc krfb kscd kppp konversation krita-data ksvg
  kaffeine-xine kio-locate ksnapshot liblockdev1 kdebluetooth wlassistant
  krita qca-tls adept-batch kde-icons-mono adept kubuntu-konqueror-shortcuts
  kaffeine skim kdenetwork-kfile-plugins kbstate kio-apt arts
  libjasper-runtime amarok-xine amarok libskim0 kpf bogofilter-bdb kdnssd
  kdemultimedia-kfile-plugins kdenetwork-filesharing kubuntu-docs bogofilter
  libifp4 libgsl0 gtk2-engines-gtk-qt kmailcvt rdiff-backup
  language-selector-qt qobex scim-qtimm kwalletmanager kopete karm keep
  adept-notifier bogofilter-common kde-systemsettings librsync1 kmousetool
  libnjb5 kmag kdepim-kresources kdepim-wizards kmilo kmix
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by funkyade on 2006-11-20
I have managed to 'solve' the issue, although I am not entirely clear which part of what I did solved it. This is for xubuntu but I am sure the process will be the same.

Firstly I did 
```
sudo apt-get autoremove
```
Then I did
```
sudo aptitude install xubuntu-desktop
```

As long as you don't purge anything like config files etc..., then your desktop is the same as before.

Not sure what caused this problem in the first place, would really like to track that down.

For now I am only using aptitude from the command-line.

EDIT: I hazard a guess that all of these packages come up as dependencies of something that has already been removed which is why the are flagged as not used. What that is is unclear, possibly a meta-package that was removed when something else was removed.

---

### Post by amrypma on 2006-12-05
What i want to know is who does apt records this information. I don't like totem on which ubuntu-desktop depends. but I definitely want to keep the rest. But never the less it gets kicked out if I run autoremove.

Does it use debfoster or deborphan or is this an entierly "new" apt-get thingie? Neither is installed on my system.

trying to 'ínstall' a package again doesn't seem to work.

A.Y.

---

### Post by amrypma on 2007-04-19
I tried auto remove but... it removes a lot of stuf I'm using. So for now I'm just ignoring it.

---

