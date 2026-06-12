---
title: "Can't install recommended update: Human-Theme"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by moloch16 on 2008-11-19
Running 8.10 (upgraded from 8.04).  When I run update manager there is a "recommended update" that is grayed out and cannot be installed.  I'm just wondering why it can't be installed?

[IMG]http://farm4.static.flickr.com/3247/3043594194_9e8fbeac4d.jpg[/IMG]

---

### Post by yang on 2008-12-24
I'm running into this same problem but with the openmovieeditor package as well.

---

### Post by Pumalite on 2008-12-24
Looks like it's your choice to do it.

---

### Post by yang on 2008-12-24
No.  Read the original post again.  The checkboxes are disabled.

---

### Post by Pumalite on 2008-12-24
Have you ran in the Terminal?:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by yang on 2008-12-24
Hm, not sure what to do about this.  (In the following, there's a lot more than 200 lines of output.)

```

$ yes n | sudo aptitude dist-upgrade | head -200
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages are BROKEN:
  blubuntu-theme libavcodec-unstripped-51 
The following NEW packages will be installed:
  libavcodec51{a} 
The following packages will be REMOVED:
  gtk2-engines-ubuntulooks{a} jackd{u} libavcodec1d{u} libavformat1d{u} 
  libavutil1d{u} libdc1394-13{u} libqt4-core{u} libqt4-gui{u} qjackctl{u} 
The following packages will be upgraded:
  human-theme openmovieeditor 
2 packages upgraded, 1 newly installed, 9 to remove and 0 not upgraded.
Need to get 2156kB of archives. After unpacking 2212kB will be freed.
The following packages have unmet dependencies:
  libavcodec-unstripped-51: Conflicts: libavcodec51 but 3:0.svn20080206-12ubuntu3 is to be installed.
  blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
libavcodec-unstripped-51

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
human-theme [0.18 (now)]

Leave the following dependencies unresolved:
ubuntu-restricted-extras recommends libavcodec-unstripped-51
Score is 560

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
human-theme
libavcodec-unstripped-51
ubuntu-artwork
ubuntu-desktop

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]

Leave the following dependencies unresolved:
ubuntu-restricted-extras recommends libavcodec-unstripped-51
Score is 197

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
openmovieeditor

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
human-theme [0.18 (now)]
libavcodec51 [Not Installed]

Score is 769

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
human-theme
openmovieeditor
ubuntu-artwork
ubuntu-desktop

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
libavcodec51 [Not Installed]

Score is 406

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme
libavcodec-unstripped-51

Leave the following dependencies unresolved:
ubuntu-restricted-extras recommends libavcodec-unstripped-51
Score is 57

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme
openmovieeditor

Keep the following packages at their current version:
libavcodec51 [Not Installed]

Score is 266

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme

Keep the following packages at their current version:
jackd [0.109.2-3ubuntu1 (intrepid, now)]
libavcodec1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavcodec51 [Not Installed]
libavformat1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavutil1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libdc1394-13 [1.1.0-5ubuntu1 (intrepid, now)]
libqt4-core [4.4.3-0ubuntu1.1 (intrepid-updates, now)]
libqt4-gui [4.4.3-0ubuntu1.1 (intrepid-updates, now)]
openmovieeditor [0.0.20071118-1 (now)]
qjackctl [0.3.2-1ubuntu1 (intrepid, now)]

Score is 833

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme

Keep the following packages at their current version:
jackd [0.109.2-3ubuntu1 (intrepid, now)]
libavcodec1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavcodec51 [Not Installed]
libavformat1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavutil1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libdc1394-13 [1.1.0-5ubuntu1 (intrepid, now)]
openmovieeditor [0.0.20071118-1 (now)]

Leave the following dependencies unresolved:
jackd recommends qjackctl
Score is 420

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
human-theme
ubuntu-artwork
ubuntu-desktop

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
jackd [0.109.2-3ubuntu1 (intrepid, now)]
libavcodec1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavcodec51 [Not Installed]
libavformat1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavutil1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libdc1394-13 [1.1.0-5ubuntu1 (intrepid, now)]
libqt4-core [4.4.3-0ubuntu1.1 (intrepid-updates, now)]
libqt4-gui [4.4.3-0ubuntu1.1 (intrepid-updates, now)]
openmovieeditor [0.0.20071118-1 (now)]
qjackctl [0.3.2-1ubuntu1 (intrepid, now)]

Score is 973

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
human-theme [0.18 (now)]
jackd [0.109.2-3ubuntu1 (intrepid, now)]
libavcodec1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavcodec51 [Not Installed]
libavformat1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavutil1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libdc1394-13 [1.1.0-5ubuntu1 (intrepid, now)]
openmovieeditor [0.0.20071118-1 (now)]

Leave the following dependencies unresolved:
jackd recommends qjackctl
Score is 923

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
human-theme
ubuntu-artwork
ubuntu-desktop

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (intrepid, now)]
jackd [0.109.2-3ubuntu1 (intrepid, now)]
libavcodec1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavcodec51 [Not Installed]
libavformat1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libavutil1d [3:0.cvs20070307-5ubuntu7.1 (now)]
libdc1394-13 [1.1.0-5ubuntu1 (intrepid, now)]
openmovieeditor [0.0.20071118-1 (now)]

Leave the following dependencies unresolved:
jackd recommends qjackctl
Score is 560

Accept this solution? [Y/n/q/?] The following actions will resolve these dependencies:

Remove the following packages:
blubuntu-look
blubuntu-theme

```

---

### Post by Pumalite on 2008-12-24
Run:
sudo apt-get -f install

---

### Post by yang on 2008-12-24
I ran it:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

But I'm still stuck in the same broken-package state.

---

