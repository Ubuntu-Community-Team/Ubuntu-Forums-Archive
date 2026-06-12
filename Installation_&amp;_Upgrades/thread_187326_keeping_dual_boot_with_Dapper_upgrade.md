---
title: "keeping dual boot with Dapper upgrade??"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by serendipity576 on 2006-06-02
I'm running Breezy and want to update to Dapper but only if I can upgrade(not new install) and keep my dual boot with XP.  Right now GRUB brings up a list of OSs  and I can choose which one I want to load.  I'd like to keep it that way, wi th the only difference being that I'll have Dapper instead of Breezy.  What is the simplest and more importantly, safest, way to accomplish this.  Thanks a lot in advance.  

Clay

---

### Post by johnc4510 on 2006-06-02
First, is your /home file on a separate partion? If not backup all data in the home file just to be safe.
To upgrade:Open a terminal  Applications>Accessories>Terminal
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
In the window that opens, change everything that says breezy to dapper, then save the file and close the window.
sudo apt-get update
sudo apt-get dist-upgrade
This should not affect GRUB

---

### Post by serendipity576 on 2006-06-03
Well I tried the first two commands and they both said that the command was not found.  So, I'm not sure how to proceed now.  Any ideas.?

---

### Post by serendipity576 on 2006-06-03
John, that actually did work, I just didn't type it correctly.  So, Dapper installed and then said something like run "dpkg --configure -a" manually.  So I did that and then it gave me the options and I just used the default, so I typed "n" for keeping current login.  Then it spits out this:

 The default action is to keep your current version.
*** login.defs (Y/I/N/O/D/Z) [default=N] ? n

Setting up libperl5.8 (5.8.7-10ubuntu1) ...

Setting up libc6-i686 (2.3.6-0ubuntu20) ...

dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on pcmciautils; however:
  Package pcmciautils is not installed.
 ubuntu-minimal depends on wpasupplicant; however:
  Package wpasupplicant is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up perl-modules (5.8.7-10ubuntu1) ...
Setting up perl (5.8.7-10ubuntu1) ...

Errors were encountered while processing:
 ubuntu-minimal


So now I'm not sure what to do, and I'm really not even sure if I have Dapper now actually.  How would I tell what version I have.  I changed the source list before running apt-get dist upgrade, and they all say Dapper now in Synaptic, but nothing looks different visually besides that that I can tell.  Can someone help me figure out how to fix this error though?

---

