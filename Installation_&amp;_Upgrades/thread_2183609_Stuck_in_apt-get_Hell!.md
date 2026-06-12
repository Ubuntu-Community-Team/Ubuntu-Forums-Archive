---
title: "Stuck in apt-get Hell!"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by bswilson on 2013-10-25
Friends, I cannot seem to update or remove any software from my systems due to some whacky apt-get issue related to Libreoffice. When I attempt to upgrade anything, I see the following message: 

```
root@eminem:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
[COLOR="#FF0000"]The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.1.2~rc3) but it is not installed
 libreoffice-ogltrans : Depends: libreoffice-common but it is not installed
E: Unmet dependencies. Try using -f.[/COLOR]
```

So, OK, I'll try that: 

```
root@eminem:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gdm libebackend-1.2-6 libedata-book-1.2-17 libedata-cal-1.2-20
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
13 not fully installed or removed.
Need to get 0 B/26.9 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 386232 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.2~rc3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.2~rc3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9702
rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: Directory not empty
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: Directory not empty
rmdir: failed to remove ‘/var/lib/libreoffice’: Directory not empty
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for gnome-menus ...
[COLOR="#FF0000"]Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.2~rc3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

No matter what I've tried, I can't fix this. I have deleted **/var/cache/apt/archives/*** and that doesn't do anything. I looked at **/var/log/dpkg.log**, and that doesn't have anything useful that I can tell. 

Help?!

---

### Post by ian-weisser on 2013-10-25
> **bswilson said:**
> 
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.2~rc3-0ubuntu1_all.deb (--unpack):
 [COLOR=#ff0000]trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9702[/COLOR]


You have at least one non-Ubuntu package installed: openoffice-debian-menus
Remove it, then try apt-get update && apt-get upgrade again. Post the result here.

There are other errors, too, but let's fix them one at a time.

---

### Post by su:bhatta on 2013-10-25
This might be way off target, 

But once I had problems with unmet dependencies which were sorted out with the help of Synaptic Package Manger. 
Once opened It told me what I had to do to resolve the issues and it worked !

---

### Post by bswilson on 2013-10-25
**ian-weisser**, thanks for your reply. I don't recall exactly when I installed OpenOffice.org, but the problem is, I can't execute _any_ **apt-get** command without being smacked with this error. Also, I absolutely have removed any third party repositories and PPAs...

```
root@eminem:~# apt-get remove openoffice-debian-menus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.1.2~rc3) but it is not going to be installed
 libreoffice-ogltrans : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by ian-weisser on 2013-10-25
Try the following and post the result:
```
apt-get autoremove openoffice-debian-menus libreoffice-core libreoffice-ogltrans
```

Due to the autoremove, it may ask to remove a lot of libreoffice packages. If apt asks to remove much more than libreoffice, abort the removal.

---

### Post by bswilson on 2013-10-28
Thanks again, **ian-weisser**, for being willing to help me. I ran the command you recommended. Seems like no luck...

```
**root@eminem:~# apt-get autoremove openoffice-debian-menus libreoffice-core libreoffice-ogltrans**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-calc : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 libreoffice-pdfimport : Depends: libreoffice-core but it is not going to be installed
 libreoffice-presentation-minimizer : Depends: libreoffice-core but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
 python3-uno : Depends: libreoffice-core (= 1:4.1.2~rc3-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@eminem:~# 
```

---

### Post by ian-weisser on 2013-10-28
Well, it's still progress.

You can try removing your old version of LibreOffice with dpkg

```
dpkg --remove libreoffice-base-core
dpkg --remove libreoffice-calc 
dpkg --remove libreoffice-draw
dpkg --remove libreoffice-gnome
dpkg --remove libreoffice-gtk
dpkg --remove libreoffice-impress
dpkg --remove libreoffice-math
dpkg --remove libreoffice-pdfimport
dpkg --remove libreoffice-presentation-minimizer
dpkg --remove libreoffice-writer
dpkg --remove libreoffice-ogltrans
dpkg --remove libreoffice-core
dpkg --remove openoffice-debian-menus
dpkg --remove libreoffice-common
apt-get autoremove
apt-get update && apt-get upgrade
```

When using dpkg, the order of removal is important to avoid orphaning.
The apt-get commands clean up orphans left behind by the removal of LibreOffice
If this works, your package manager should be working and LibreOffice should be uninstalled.
Let us see how the session goes....

---

### Post by bswilson on 2013-10-29
**ian-weisser**, thank you! I did what you recommend, and that solved my problem. I had to purge a few packages dependancies, but that was no big deal. I'm now able to update my system correctly with no errors. One question for you; you stated:

```
When using dpkg, the order of removal is important to avoid orphaning.
```

I understand that, and it appears that the list you shared is alphabetical. Where did you come up with this list? Did you run an **apt-cache** command to list out the packages that match "libreoffice*"?

Thanks once more for the help.

---

### Post by ian-weisser on 2013-10-29
I created the list from your own error messages.
Those error messages list the problem packages and their problem dependencies.
I simply put the known dependencies last (libreoffice-core and libreoffice-common).

Not magic, just a few moments of diagramming the relationships.

Quite happy to see the problem resolved!

---

### Post by bswilson on 2013-10-29
Me, too! Thanks again.

---

