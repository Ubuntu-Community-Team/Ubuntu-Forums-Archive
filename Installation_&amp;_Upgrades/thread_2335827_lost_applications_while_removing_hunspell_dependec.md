---
title: "lost applications while removing hunspell dependecies"
date: 2016-09-01
forum: Installation &amp; Upgrades
---

### Post by pyslice on 2016-09-01
Spelling was not working in LibreOffice (4.2.8) so I tried reinstalling libhunspell (1.3)
There was a dependency warning that I didn't take too seriously - it referred to 2 items I didn't know
I started worrying when I saw uninstall took sensibly longer than I expected
It took out about 70 other applications and packages (including software-center, update-manager, gedit, gimp etc., as well as the whole libreoffice package) mostly everything I installed myself, but also thing that came within the OS (I think gedit was already there, software-center, update-manager certainly were)
I reinstalled software-center so I can now see the list of removed items.

1. What happened? Is there a way I can retrieve the dependency warning that popped up before the libhunspell uninstall? (is there a system/warning events log?)

2. Is there a way to reinstall lost apps in bulk / restore applications to a certain moment. 

Thank you.

Ubuntu 14.04.5 LTS, Gnome

---

### Post by ajgreeny on 2016-09-01
Command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
``` will show you all that has recently be removed and may allow you to list everything that was removed at that time and reinstall it all, though why a "reinstall" would remove anything I am not sure.

Did you use the **reinstall** option available with apt-get (or synaptic) or did you remove libhunspell then install it; the two will work in a totally different manner as far as dependencies are concerned.

---

### Post by mook765 on 2016-09-01
Look in  /var/log/apt/term.log  too.

---

### Post by pyslice on 2016-09-02
Thank you.
I don't have synaptic, I used Software-Center to remove libhunspell. Then I had to reinstall first Software-Center, then LibreOffice.
It is not the reinstall that removed my programs, but the uninstall; when libhunspell was uninstalled, somehow, a bunch of my programs were deemed needles dependencies and removed as well. 
So, regarding reinstalling, there is no such thing as "restore to a previous state of the system"...

---

### Post by ajgreeny on 2016-09-02
That ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
``` command I suggested will show all that was removed (uninstalled) whether by apt-get, synaptic, software-center, or even dpkg, so run it as I said and then reinstall the packages that were removed at the same time as libhunspell.

If I try to remove libhunspell the list of packages removed with it is shown below. You could try using that list to replace those packages, less any that you know you did not have and do not want.
```
zenity
libhunspell-1.3-0
libreoffice-pdfimport
libreoffice-base-core
libreoffice
libabiword-3.0
abiword
xubuntu-desktop
kde-runtime
libreoffice-writer
hunspell
libreoffice-impress
libreoffice-avmedia-backend-gstreamer
libreoffice-base
onboard-data
libwebkitgtk-1.0-0
gimp
okular
libreoffice-draw
abiword-plugin-grammar
libreoffice-help-en-gb
kdelibs5-plugins
systemsettings
libreoffice-core
ubuntu-release-upgrader-gtk
libreoffice-sdbc-firebird
libsexy2
libenchant1c2a
abiword-plugin-mathview
goldendict
gnumeric-doc
hexchat
libgtkspell0
digikam
inkscape
gthumb
libreoffice-report-builder-bin
kipi-plugins
gnome-user-guide
update-notifier
libwebkitgtk-3.0-0
libyelp0
python3-uno
filelight
pidgin-libnotify
kmymoney
libreoffice-gtk2
libreoffice-gtk3
scribus
libreoffice-sdbc-hsqldb
qapt-batch:-
enchant
midori
pandora
update-manager
yelp
libwebkit2gtk-3.0-25
libreoffice-base-drivers
gir1.2-webkit-3.0
kubuntu-debug-installer
libreoffice-math
onboard
libreoffice-calc
liblibreofficekitgtk
pidgin
kdepim-runtime
```

---

### Post by pyslice on 2016-09-02
Thank you, this is much appreciated!

---

