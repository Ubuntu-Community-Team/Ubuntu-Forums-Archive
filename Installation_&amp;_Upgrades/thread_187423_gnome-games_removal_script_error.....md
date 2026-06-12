---
title: "gnome-games removal script error...."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Rob_Frohne on 2006-06-03
Hi,
I have a what was a Breezy Ubuntu + Kubuntu PPC machine that I upgraded to Dapper with the final release candidate.  It quit in the middle of the upgrade, and I had to manually fsck the disk on reboot and it had to fix a bunch of files, but finally it was fixed and I went back into Synaptic Package Manager and started applying updates again a couple of times and it appears to be working somewhat now.  The problem is that gnome-games has a problem with the removal script and I can't remove it, or upgrade it.  I've tried apt-get -f install and a number of other incantations without any luck.  The errors I get are:


Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following NEW packages will be installed:
  gnome-games-data
The following packages will be upgraded:
  gnome-games
1 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/4242kB of archives.
After unpacking 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 140106 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_powerpc.deb) ...
I/O error : Is a directory
/usr/share/gconf/schemas/blackjack.schemas:1: parser error : Document is empty

^
/usr/share/gconf/schemas/blackjack.schemas:1: parser error : Start tag expected, '<' not found

^
I/O error : Is a directory
Failed to open `/usr/share/gconf/schemas/blackjack.schemas': Is a directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_powerpc.deb (--unpack):
 there is no script in the new version of the package - giving up
Unpacking gnome-games-data (from .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_powerpc.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone with any advice?

Thanks,

Rob

---

