---
title: "Warty to Hoary upgrade error??"
date: 2005-03-29
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-03-29
Following the instructions in the "HOW-TO" I changed my sources.list, ran apt-get update and the apt-get dist-upgrade.

It seems to find everything, but after it runs "checking changelogs" I get the following:

> 937 upgraded, 168 newly installed, 25 to remove and 1 not upgraded.
Need to get 0B/606MB of archives.
After unpacking 241MB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg-deb: file `/var/cache/apt/archives/diveintopython_5.4-1ubuntu1_all.deb' contains ununderstood data member data.tar.bz2    , giving up


The terminal buffer then clears itself and I get the following:

> alsa-lib (1.0.7-1) unstable; urgency=high

  Some users might encounter problems getting their sound cards to work
  when using alsa-lib version 1.0.6 or 1.0.7 along with Linux kernel
  2.6.8.1.  (The latter is the kernel that Debian plans to ship with
  sarge.  Users of Linux 2.4 are not affected by this problem because
  Linux 2.4 does not contain any ALSA drivers.)  The reason is that
  Linux 2.6.8.1 includes ALSA drivers at version level 1.0.4 and these
  appear to be incompatible in some cases with the ALSA libraries at
  version 1.0.6.  As of this writing, we know the emu10k driver is
  affected by this, but for all we know there might be others.

  There is an easy fix for the problem with the emu10k driver.  Simply
  do one of the following:

  - Use Linux 2.4.x and a matching alsa-modules package.
  - Use Linux 2.6.8.1 but don't use the ALSA drivers that come with it.
    Instead, create an alsa-modules package for Linux 2.6.8.1 using
    the make-kpkg utility and the alsa-source package.
  - Use Linux 2.6.9 or higher.  These kernels include the latest ALSA drivers.
  - Apply the following patch to fix the configuration file for emu10k:

    --- /usr/share/alsa/cards/EMU10K1.conf~ 2004-09-26 19:17:05.000000000 +0200
/tmp/tmpwgWDA2

 +++ /usr/share/alsa/cards/EMU10K1.conf  2004-10-08 22:29:14.000000000 +0200
    @@ -223,7 +223,7 @@
            slave.pcm {
                    type hw
                    card $CARD
    -               device 2
    +               device 3
            }
            hooks.0 {
                    type ctl_elems


  See [http://bugs.debian.org/275573](http://bugs.debian.org/275573) for more information.

 -- Jordi Mallach <jordi@debian.org>  Wed, 18 Nov 2004 10:00:00 +0200
bogofilter (0.93.1-2) unstable; urgency=medium

  * If this is a new installation, or if you are upgrading from a
    version prior to 0.93.0-1, you should have no problems.  If,
    on the other hand, you are unfortunate enough to be upgrading
    from 0.93.0-1 or 0.93.0-2, you must manually upgrade each of
    your wordlist databases before it will function again.
  - To do so, first make sure you have the db4.2-util package
    installed, then
    1. Stop invocation of bogofilter
    2. db4.2_recover -h ~/.bogofilter
    3. rm ~/.bogofilter/lockfi*
    4. cd ~/.bogofilter && rm $(db4.2_archive -h .)
    5. Resume invocation of bogofilter
  - Repeat this upgrade procedure for each relevant bogofilter
    wordlist database, substituting the directory name for
    "~/.bogofilter".
  * Alternately, if you don't want to upgrade your database, you
    may move or delete it and rebuild your wordlist from scratch.

 -- Clint Adams <schizo@debian.org>  Sat, 27 Nov 2004 16:29:00 -0500

bogofilter (0.93.0-1) unstable; urgency=low

  * For more detailed information, read
    /usr/share/doc/bogofilter/RELEASE.NOTES-0.93 .
  * bogofilter's defaults have changed.  All users should be made aware
    that depending on their configurations, the words in the header added
    to messages by bogofilter in passthrough mode may abruptly change from
    "Yes" and "No" to "Spam", "Ham", and "Unsure"; and this may render
    useless any filtering based on these headers.
  * bogofilter has switched to use the Berkeley DB Transactional Data
    Store.  bogofilter will read databases created by previous versions,
    though rebuilding the database is recommended to take advantage of all
    features.  Currently transaction log files need to be archived or
    deleted manually.

 -- Clint Adams <schizo@debian.org>  Sat,  6 Nov 2004 23:05:11 -0500
eog (2.8.1-1) experimental; urgency=low

:

* The Nautilus "View as Collection" component isn't available anymore.

  The release note explanations:

  The by far biggest change for the default GNOME image viewer is the removal
  of the bonobo components. It comes now as a monolithic program again and
  makes use of the new wonderful GtkUIManager API. This change leads to great
  speed improvements and a much better user interface. On the shadow side the
  Nautilus "View as Collection" component isn't available anymore. It's
  planned to provide a new Nautilus extension in the future as a replacement.

 - Sebastien Bacher <seb128@debian.org>  Mon, 25 Oct 2004 22:03:56 +0200
gnome-volume-manager (1.1.2-3) unstable; urgency=low

  As of this version gnome-volume-manager uses pmount for mounting and
  unmounting devices. To be able to use pmount, the user must be a
  member of the plugdev group. If a user isn't part of this group,
  gnome-volume-manager will be unable to mount devices!

  For more information about pmount and its policy see the pmount manpage.

-- Sjoerd Simons <sjoerd@debian.org>  Wed, 24 Nov 2004 11:21:31 +0100
mozilla (2:1.7.6-2) unstable; urgency=low

  * Executable name was changed to mozilla-suite.
    Please update property of your personal desktop icons.

 -- Takuo KITAME <kitame@debian.org>  Wed, 23 Mar 2005 20:14:42 +0900

End


My /etc/apt/sources.list contains the following:

> 
## deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted


I simply cannot do the update.

Now, I have tried this several times and I did have some other sources in my sources.list file which I have now deleted. (actually I made a copy of the old one) Can I clear the cache in apt-get and start over? Could I have picked up some conflicting packages?

---

### Post by Psquared on 2005-03-29
I cleared the cache and tried again. Another 1 hr 47 mins and it still will not upgrade. Same error.

I believe the problem is this line:

> dpkg-deb: file `/var/cache/apt/archives/diveintopython_5.4-1ubuntu1_all.deb' contains ununderstood data member data.tar.bz2 , giving up 

I think the upgrade is aborting/choking on this file and will not continue. What does it mean?

---

