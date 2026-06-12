---
title: "Broken package and unmet dependencies..."
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by v1cho on 2008-01-03
While I was installing **kolourpaint4-kde4** on my Ubuntu 7.10 the electricity suddenly stopped. Ever since I get this message when I try to install software: 
```
vicho@vicho:~$ sudo apt-get install kde4base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kde4base is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kolourpaint4-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                     Depends: kdebase-runtime-bin but it is not going to be installed
                     Depends: kdebase-runtime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



vicho@vicho:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde-icons-oxygen kdebase-runtime-bin kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common
Suggested packages:
  kdebase-kde4
The following NEW packages will be installed:
  kde-icons-oxygen kdebase-runtime-bin kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/58.6MB of archives.
After unpacking 87.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 108089 files and directories currently installed.)
Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/oxygen/128x128/apps/phonon-xine.png', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data-common (from .../kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/crystalsvg/scalable/apps/hwinfo.svgz', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/applications/kde4/knetattach.desktop', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-bin-kde4 (from .../kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kdebugdialog', which is also in package kde4base
Unpacking kdebase-runtime-bin (from .../kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kde4-menu', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data-common_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.96.0-1ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin_4%3a3.96.0-1ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
vicho@vicho:~$ 

```

Any ideas what should I do? :confused:

---

### Post by tech9 on 2008-01-03
try installing it through synaptic

System>Administration>Synaptic Package Manager

---

### Post by v1cho on 2008-01-03
> **tech9 said:**
> try installing it through synaptic

System>Administration>Synaptic Package Manager

When I tried installing it through synaptic I ended up with the same error. Then I found all the packages that were listed in the error report and completely removed them. I've just installed them again and everything works fine :)
Thanks anyway!

---

### Post by tech9 on 2008-01-03
> **v1cho said:**
> When I tried installing it through synaptic I ended up with the same error. Then I found all the packages that were listed in the error report and completely removed them. I've just installed them again and everything works fine :)
Thanks anyway!

cool :) - also, I forgot to mention that you should run

```
sudo apt-get update
```

before installs - this way your system will be up-to-date

---

