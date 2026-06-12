---
title: "Hardy upgrade problem"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by TracyO on 2008-07-31
Hi,

I've been running Gutsy that was pre-installed on my Dell, and I am ready to upgrade to Hardy.  I started it yesterday through the Update Manager, and with about 7 minutes left in the installation process, it froze--not my computer, just the upgrade.  (My internet might have gone out during the process.)  I ended up shutting down my computer, and now it appears to be stuck.  I log in, it freezes in booting up--I never get the Ubuntu sound.  

Right now I can get on through Gnome and presumably the other options from the login screen.  

Should I attempt to start the upgrade over completely, or is there something else I should do?

Thank you!
Tracy

---

### Post by Sef on 2008-07-31
At start up, press escape and highlight recovery mode.  Can you get into that?

---

### Post by TracyO on 2008-07-31
Does 2.6.22-15 or 14 matter?  I have recovery modes for both.

---

### Post by tuxxy on 2008-07-31
Selet the one for your current kernel

---

### Post by TracyO on 2008-07-31
To be honest, I'm not sure.  How do I know?

---

### Post by TracyO on 2008-07-31
I am in recovery mode.  It left me off at root@dell-desktop:~#.

A few lines up, it also gives me 
Profile /etc/apparmor.d/usr.sbin.cupsd failed to load.

Another fail for Setting kernel variables
error: "vm.mmap_min_addr" is an unknown key

---

### Post by Sef on 2008-08-02
Here are a couple of bug reports the top one has a possible solution:

[http://www.winehq.org/pipermail/wine-bugs/2008-April/104774.html]("http://www.winehq.org/pipermail/wine-bugs/2008-April/104774.html")

[https://lists.ubuntu.com/archives/ubuntu-mono/2008-January/009663.html]("https://lists.ubuntu.com/archives/ubuntu-mono/2008-January/009663.html")

---

