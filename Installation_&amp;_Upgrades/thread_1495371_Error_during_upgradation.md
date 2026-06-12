---
title: "Error during upgradation"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by debojyoti on 2010-05-28
I tried to upgrade from Karmic to Lucid by an alternate CD during which some problem occurred and the upgradation process stopped. Later, I found an error message in the right side of the top bar which reads as:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount>0'This usually means that your installed packages have unmet dependencies"

When I tried with the package manager I got the following error message:

(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `human-theme' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on compiz-core (= 1:0.8.4-0ubuntu15); however:
  Version of compiz-core on system is 1:0.8.4-0ubuntu2.1.
 compiz-gnome depends on compiz-plugins (= 1:0.8.4-0ubuntu15); however:
  Version of compiz-plugins on system is 1:0.8.4-0ubuntu2.1.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-gnome

Can anyone please suggest me how to resolve the issue? 

Please help......

Kunal

---

