---
title: "Having problems with install-info &quot;Not a directory: MOZ_DISABLE_PANGO=1.&quot;"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by TrevorBradley on 2011-10-20
Hey there... sometime in the last month, "something" went wrong.  I'm usually very good about determining cause and effect on these problems, but something got borked and I can't track down what the problem is.

Somehow, I can't do anything with the ubuntu-standard package because install-info gives an error, specifically:

```
$ sudo apt-get install ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-standard is already the newest version.
The following packages were automatically installed and are no longer required:
  libfolks-telepathy22 libpanel-applet-4-0 libswscale0 libmono2.0-cil
  guile-1.6 libmono-data-tds2.0-cil libboost-regex1.42.0 libunity4
  gir1.2-vte-0.0 libmono-system-data2.0-cil libxine1-x libindicator3
  libcairo-ruby libtorrent11 wine1.3-gecko libbluray0 libedataserverui1.2-11
  libruby1.9.1 liblinebreak1 g++-4.5 libxine1-misc-plugins libxcb-xv0 phonon
  libatk1-ruby1.8 libmono-system-runtime2.0-cil libdbi0 libcamel1.2-19
  libpostproc51 libsensors-applet-plugin0 libxine1-bin libpod-coverage-perl
  libavformat52 libboost-serialization1.42.0 libfolks22 ruby1.8 guile-1.6-libs
  libmono-messaging2.0-cil libyaml-0-2 libdevel-symdump-perl ruby-gdk-pixbuf2
  libebook1.2-10 ruby libmono-system-messaging2.0-cil librpcsecgss3
  virtualbox-ose-dkms libgdata11 libgwibber1 libecal1.2-8
  libmono-system-data-linq2.0-cil libstdc++6-4.5-dev ruby-glib2
  libmono-sqlite2.0-cil libqthreads-12 libglib2-ruby1.8
  libboost-iostreams1.42.0 hddtemp libavfilter1 libaqhbci19
  libmono-system-web2.0-cil libnunit2.4-cil libcairo-ruby1.8
  gir1.2-appindicator-0.1 libphonon4 libedata-cal1.2-10 virtualbox-ose-qt
  libedata-book1.2-8 libgdk-pixbuf2-ruby1.8 ruby-atk phonon-backend-xine
  ruby-pango python-wsgi-intercept libgtk2-ruby1.8 libunity-misc0 ruby-cairo
  libgtk2-ruby libboost-filesystem1.42.0 libruby1.8 libquicktime1
  guile-1.6-slib libguile-ltdl-1 libebml3 libreadline5 libmpcdec6
  libtest-pod-perl libmono-wcf3.0-cil libboost-system1.42.0 libpango1-ruby1.8
  libmatroska3 gir1.2-panelapplet-4.0 libxine1-console libavdevice52 ruby-gtk2
  libxine1 libntfs-3g79
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-8ubuntu1) ...
Not a directory: MOZ_DISABLE_PANGO=1.
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of info:
 info depends on install-info; however:
  Package install-info is not configured yet.
dpkg: error processing info (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on info; however:
  Package info is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 install-info
 info
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried searching for "MOZ_DISABLE_PANGO", but can't find it.  It's not in any file that's in my home directory.  

Any idea where I should start looking to fix this problem?

---

### Post by TrevorBradley on 2011-10-22
I seem to have "kind of" fixed this by removing the install-info package... it's the only way I can do updated of any kind now, it seems.

---

### Post by MAFoElffen on 2011-10-22
> **TrevorBradley said:**
> Hey there... sometime in the last month, "something" went wrong.  I'm usually very good about determining cause and effect on these problems, but something got borked and I can't track down what the problem is.

Somehow, I can't do anything with the ubuntu-standard package because install-info gives an error, specifically:

```
$ sudo apt-get install ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-standard is already the newest version.
The following packages were automatically installed and are no longer required:
  libfolks-telepathy22 libpanel-applet-4-0 libswscale0 libmono2.0-cil
  guile-1.6 libmono-data-tds2.0-cil libboost-regex1.42.0 libunity4
  gir1.2-vte-0.0 libmono-system-data2.0-cil libxine1-x libindicator3
  libcairo-ruby libtorrent11 wine1.3-gecko libbluray0 libedataserverui1.2-11
  libruby1.9.1 liblinebreak1 g++-4.5 libxine1-misc-plugins libxcb-xv0 phonon
  libatk1-ruby1.8 libmono-system-runtime2.0-cil libdbi0 libcamel1.2-19
  libpostproc51 libsensors-applet-plugin0 libxine1-bin libpod-coverage-perl
  libavformat52 libboost-serialization1.42.0 libfolks22 ruby1.8 guile-1.6-libs
  libmono-messaging2.0-cil libyaml-0-2 libdevel-symdump-perl ruby-gdk-pixbuf2
  libebook1.2-10 ruby libmono-system-messaging2.0-cil librpcsecgss3
  virtualbox-ose-dkms libgdata11 libgwibber1 libecal1.2-8
  libmono-system-data-linq2.0-cil libstdc++6-4.5-dev ruby-glib2
  libmono-sqlite2.0-cil libqthreads-12 libglib2-ruby1.8
  libboost-iostreams1.42.0 hddtemp libavfilter1 libaqhbci19
  libmono-system-web2.0-cil libnunit2.4-cil libcairo-ruby1.8
  gir1.2-appindicator-0.1 libphonon4 libedata-cal1.2-10 virtualbox-ose-qt
  libedata-book1.2-8 libgdk-pixbuf2-ruby1.8 ruby-atk phonon-backend-xine
  ruby-pango python-wsgi-intercept libgtk2-ruby1.8 libunity-misc0 ruby-cairo
  libgtk2-ruby libboost-filesystem1.42.0 libruby1.8 libquicktime1
  guile-1.6-slib libguile-ltdl-1 libebml3 libreadline5 libmpcdec6
  libtest-pod-perl libmono-wcf3.0-cil libboost-system1.42.0 libpango1-ruby1.8
  libmatroska3 gir1.2-panelapplet-4.0 libxine1-console libavdevice52 ruby-gtk2
  libxine1 libntfs-3g79
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[COLOR=Red]3 not fully installed or removed.[/COLOR]
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-8ubuntu1) ...
Not a directory: MOZ_DISABLE_PANGO=1.
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of info:
 info depends on install-info; however:
  Package install-info is not configured yet.
dpkg: error processing info (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on info; however:
  Package info is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 install-info
 info
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I've tried searching for "MOZ_DISABLE_PANGO", but can't find it.  It's not in any file that's in my home directory.  

Any idea where I should start looking to fix this problem?
Open a terminal session ( <cntrl><alt><t> )
```

gksudo synaptic

```
go Settings > Filters > Broken Packages
Decide what to do from there.

It says you have 3 packages not fully installed or removed... that should find them.

---

### Post by TrevorBradley on 2011-10-22
The three packages are info, install-info, and ubuntu-standard.  Completely removing install-info makes the errors go away, but I still can't reinstall it - I get the same errors.

---

### Post by MAFoElffen on 2011-10-22
> **TrevorBradley said:**
> The three packages are info, install-info, and ubuntu-standard.  Completely removing install-info makes the errors go away, but I still can't reinstall it - I get the same errors.
Pango is a library for rendering text... Mozilla Firefox and Mozilla Thunderbird use Pango for their font rendering... 
```

export MOZ_DISABLE_PANGO=1

```Used to be a tweak to try to speed up Firefox 3 by turning off it's font rendering.  I haven't really seen it recently, but...

Go to your Home Directory > Press <cntrl><h> to display hidden files. > Look for a file names ".bashrc" > Right click on it and open with the text editor...

Use the editor's text search to search on "DISABLE_PANGO". 

If found, I'm thinking it will be near the end (where that tweak said to put it) in the export section, but if "someone" did it, it could be anyhwere in that file.

A comment character in that file is a "#" character.  If found, add a comment character (#) and a space in front of that line and save.

If it's not in that user profile file... Then it might have been set locally or globally somewhere else in one of these 3 profile files:
/etc/firefox/syspref.js
/usr/lib/firefox-7.0.1/defaults/pref/syspref.js
~/.mozilla/firefox/(profile)/prefs.js

Good luck with that...  Note that those file are in javascript. If you find that in one of those files, post it and I'll help you figure it out.

If you can't find it in all that-- It might be easier to just check the .bashrc file. Delete the profile folder in ~/.mozilla/firefox/ and then reinstall Firefox from sysnaptic.

---

### Post by TrevorBradley on 2011-10-22
It's nowhere in my home directory, or in any of the locations you suggest, but I decided to give /etc/ a full sweep and found it!

set MOZ_DISABLE_PANGO=1

Was in /etc/environment for some bizarre reason.

Searching google:

MOZ_DISABLE_PANGO=1

is the correct line here.  No clue why it's in there... I must have misread something long ago.

---

### Post by MAFoElffen on 2011-10-22
> **TrevorBradley said:**
> It's nowhere in my home directory, or in any of the locations you suggest, but I decided to give /etc/ a full sweep and found it!

set MOZ_DISABLE_PANGO=1

Was in /etc/environment for some bizarre reason.

Searching google:

MOZ_DISABLE_PANGO=1

is the correct line here.  No clue why it's in there... I must have misread something long ago.
Wow... In there, it would get misrep'ed as a directory path setting instead of as a viarable setting.  Looks like you found it.

---

