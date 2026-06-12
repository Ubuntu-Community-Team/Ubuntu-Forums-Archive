---
title: "anyone know how to reverse breezy install"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by duck on 2005-11-10
Was just wondering if I can reverse the partial install i have for breezy. I attempted to upgrade to Breezy from a terminal but it did not complete correctly. Programs then started to not work so I restarted hoping that would fix the problem. Instead now the GUI does not load and xstart doesnt work. When I try sudo apt-get -f upgrade I get the following error msg:
Unpacking replacement gvlc ...
dpkg: error processing /var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (--unpack):
trying to overwrite '/usr/share/applications/gvlc.desktop', which is also in package vlc
Errors were encountered while processing:
/var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then it sends me back to $ prompt.

I initially upgraded using the following:

1.

Open up a terminal
2.

sudo gedit /etc/apt/sources.list
3.

Replace with the following:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

1.

sudo apt-get update
2.

sudo apt-get dist-upgrade

Since I need my computer working I would prefer to just have it back to the way it was before the upgrade. Can someone tell me of a way to do this. Massive thanks in advance!

---

### Post by ranf on 2005-11-11
[QUOTE=duck]Was just wondering if I can reverse the partial install i have for breezy. 
[/QUOTE]
I don't think you can "dist-downgrade".

[QUOTE=duck]When I try sudo apt-get -f upgrade I get the following error msg:
Unpacking replacement gvlc ...
dpkg: error processing /var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (--unpack):
trying to overwrite '/usr/share/applications/gvlc.desktop', which is also in package vlc
Errors were encountered while processing:
/var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then it sends me back to $ prompt.
[/QUOTE]
At this stage you can either uninstall `gvlc'. 
Or try the apt-get option --force-yes which is said to be a bit dangerous in the man page.

---

