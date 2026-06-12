---
title: "Can't boot after software updates"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by quietphoks on 2007-07-11
Just downloaded and installed some new packages using the built-in 'Software updates' tool, and I get the following error when booting up:
> Starting up ...
ran out of input data
-- System halted

My only OS is Edgy Eft.  I haven't made any modifications to it, except maybe a few previous software updates when prompted.  I boot from the same partition that contains the rest of the filesystem.  

There were a couple of errors during the upgrade.  Unfortunately, I don't know where to look for a log of the upgrades I just made and errors that occured.

I've googled this and read a few of the posts, which suggest rerunning lilo or cleaning up the boot partition and installing a new kernel.  Since ubuntu uses grub instead of lilo (right?) I tried reinstalling grub following these instructions ([http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")) to no avail.  I'm not really sure how to go about reinstalling the kernel.  Is that the next step I should take?  If so, how should I do it? Thanks!

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **quietphoks said:**
> There were a couple of errors during the upgrade.

Try:
>dpkg --configure -a
This should fix these installation-errors, I hope. ;)

---

### Post by quietphoks on 2007-07-11
How do I do this from the live CD? I've tried this (below), but nothing prints to the console when I run dpkg, and
I get the same "ran out of input data" error when restarting.
/>mount /dev/hda1 mnt/hda1
/> cd mnt/hda1/usr/bin
/mnt/hda1/usr/bin> ./dpkg --configure -a

---

### Post by Odrodzona-Sarmacja on 2007-07-11
Try booting ubuntu in a recovery mode and hope to get a maintance shell. There in shell you type that command.

---

### Post by quietphoks on 2007-07-11
Thanks.  At the grub menu I have the following options:
2.6.17-11-generic
2.6.17-11-generic (recovery mode)
2.6.17-10-generic
2.6.17-10-generic (recovery mode)

2.6.17-11 doesn't boot (same error as before) in either normal or recovery modes.  I can boot into 2.6.17-10 normally.
When I do and run 
> dpkg --configure -a 
I get the following response:

> dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-common on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on evolution-data-server-common (= 1.8.1-0ubuntu5.1); however:
  Version of evolution-data-server-common on system is 1.8.1-0ubuntu5.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default:
 openoffice.org-style-default depends on openoffice.org-common (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-common on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
 openoffice.org-gtk depends on openoffice.org-style-industrial; however:
  Package openoffice.org-style-industrial is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 2.0.0.4+0dfsg-0ubuntu0.6.10); however:
  Version of firefox on system is 2.0.0.3+0dfsg-0ubuntu0.6.10.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.0.4-0ubuntu6); however:
  Version of openoffice.org-core on system is 2.0.4-0ubuntu5.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-style-industrial
 evolution-data-server
 openoffice.org-base
 openoffice.org-style-default
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 firefox-gnome-support
 openoffice.org-writer
 python-un

Also, the update manager displays the following when I try to check for updates;> 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I ran 
>sudo apt-get install -f
I got the following output:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  evolution-data-server-common firefox gimp openoffice.org-calc
  openoffice.org-common openoffice.org-core
Suggested packages:
  latex-xft-fonts libthai0 gimp-help-en gimp-help libgimp-perl
  gimp-data-extras
Recommended packages:
  gimp-svg openoffice.org-style-crystal openoffice.org-style-hicontrast
The following packages will be upgraded:
  evolution-data-server-common firefox gimp openoffice.org-calc
  openoffice.org-common openoffice.org-core
6 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
14 not fully installed or removed.
Need to get 0B/62.3MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 109176 files and directories currently installed.)
Preparing to replace evolution-data-server-common 1.8.1-0ubuntu5 (using .../evolution-data-server-common_1.8.1-0ubuntu5.1_all.deb) ...
Unpacking replacement evolution-data-server-common ...
dpkg: error processing /var/cache/apt/archives/evolution-data-server-common_1.8.1-0ubuntu5.1_all.deb (--unpack):
 unable to make backup link of `./usr/share/evolution-data-server-1.8/zoneinfo/Pacific/Enderbury.ics' before installing new version: Operation not permitted
Preparing to replace firefox 2.0.0.3+0dfsg-0ubuntu0.6.10 (using .../firefox_2.0.0.4+0dfsg-0ubuntu0.6.10_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace openoffice.org-calc 2.0.4-0ubuntu5 (using .../openoffice.org-calc_2.0.4-0ubuntu6_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
Preparing to replace openoffice.org-common 2.0.4-0ubuntu5 (using .../openoffice.org-common_2.0.4-0ubuntu6_all.deb) ...
Unpacking replacement openoffice.org-common ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3360
Wrote literal globs at 3360 - 33c4
Wrote suffix globs at 33c4 - 674c
Wrote full globs at 674c - 6770
Wrote magic at 6770 - bd80
Wrote namespace list at bd80 - bd90
***
Preparing to replace openoffice.org-core 2.0.4-0ubuntu5 (using .../openoffice.org-core_2.0.4-0ubuntu6_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Preparing to replace gimp 2.2.13-1ubuntu3 (using .../gimp_2.2.13-1ubuntu3.2_i386.deb) ...
Unpacking replacement gimp ...
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-data-server-common_1.8.1-0ubuntu5.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks for all your help so far!

---

### Post by quietphoks on 2007-07-12
Maybe I'm running into several problems at once.  Perhaps there's something wrong with my HD?
There were a two files that were somehow corrupted in the evolution-data-server package (which I wasn't able to reinstall)--permissions had the capital S instead of 'x' or '-' in a few places, seemingly random numbers in the place of the normal user and group id's, and a question mark instead of 'd' or '-'.  
I ran fsck which reported several errors (mostly inodes with the incorrect number of blocks), all of which I fixed. 
Now evolution-data-server installs successfully, but the GNOME clock and network manager applets fail to start when I log in ("Panel encountered a problem while loading OAFIID:GNOME_ClockApplet..."; "The network manager cannot find some required resources..."). I reinstalled gnome-applets and gnome-applets-data, but that hasn't helped.  

Does anyone have any ideas?  Thanks again--

---

