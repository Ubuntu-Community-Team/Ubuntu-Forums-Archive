---
title: "Problem on upgrading ubuntu from 9.04 to 9.10"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by gtmroy on 2009-11-26
I am trying to upgrade ubuntu from 9.04 to 9.10. Among the total 1420 files, 1418 files are already been downloaded but when it reached to the 1419th, it failed to download. The follow message is shown. It's probably server related problem but I have changed the server from main server to server from united states or to another. But the problem is not yet solved. I also tried to do it from command line but failed. Could you please help me in this regard? Thanks all.

Message:

goutam@Goutam:~$ do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool  19s 4s
Done downloading           
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg'

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading           
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information

Third party sources disabled

Some third party entries in your sources.list were disabled. You can
re-enable them after the upgrade with the 'software-properties' tool
or your package manager.

Done downloading           

Checking package manager
Reading package lists: Donearmic-updates/universe Packages: 95     
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Support for some applications ended

Canonical Ltd. no longer provides support for the following software
packages. You can still get support from the community.

If you have not enabled community maintained software (universe),
these packages will be suggested for removal at the end of the
upgrade.

Demoted:
acl, binutils-static, bluez-gnome, contact-lookup-applet, cpp-4.3,
cupsddk, epiphany-browser, epiphany-browser-data,
epiphany-browser-dbg, epiphany-extensions, epiphany-gecko, g++-4.3,
gcc-4.3, gcc-4.3-base, gfortran-4.3, gnome-mount,
gnome-user-guide-en, gstreamer0.10-gnomevfs, human-icon-theme, klogd,
libglew1.5, libgnome-speech7, libgnomevfs2-bin, libmono-data2.0-cil,
libmysqlclient15off, libpolkit-gnome0, libsmbios2,
libstdc++6-4.3-dev, nvidia-180-modaliases, phonon,
phonon-backend-gstreamer, policykit-gnome, python-gdata,
python-launchpad-bugs, python-usb, qt4-qtconfig, rss-glx, scim-m17n,
sysklogd, tangerine-icon-theme, ttf-kochi-gothic,
ttf-sazanami-gothic, ubuntu-gdm-themes, w3c-dtd-xhtml

Calculating the changes

Do you want to start the upgrade?

26 packages are going to be removed. 236 new packages are going to be
installed. 1181 packages are going to be upgraded.

You have to download a total of 34.2k. This download will take about
1 second with a 1Mbit DSL connection and about 4 seconds with a 56k
modem.

Fetching and installing the upgrade can take several hours. Once the
download has finished, the process cannot be cancelled.

Continue [yN]  Details [d]y

Fetching
Done downloading           
Done downloading           
Done downloading           

Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or
installation media and try again. All files downloaded so far are
kept.

Failed to fetch
[http://archive.ubuntu.com/ubuntu/pool/m](http://archive.ubuntu.com/ubuntu/pool/m) … 1_i386.deb
403 Forbidden

Restoring original system state

Aborting
Reading package lists: Doneunty/main Packages: 95  ackages: 94     
Reading state information: Done
Reading state information: Done
Reading state information: Done

---

