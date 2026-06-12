---
title: "1/18/2008 Update for Gutsy doesn't work"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by beckejc on 2008-01-18
Hi;
I tried to use the update manager to install my normal periodic update of the software.

The update for me has something like:

xserver-xorg-core
linxfont1
 and a bunch of avahi stuff

I get message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

This is not transient, as I know it has been doing it for over 5 hrs.  I have never had trouble of this kind updating my system before

Any help appreciated.

---

### Post by grEnAlEins on 2008-01-18
I was just coming to post the same thing.  I tried it a few hours after my initial attempt and still no dice...
I wish I knew what to do/what was wrong.  Regrettably, I have no idea what the problem is or how to go about resolving it.

---

### Post by Fraktyl on 2008-01-18
It's hanging from the older broken update from earlier today.

Do the following:
Close the update manager
Open a terminal
sudo apt-get update

Rerun the update manager and it should download with no problem.

---

### Post by beckejc on 2008-01-18
That worked perfectly,  You're a freaking genius and deserve a medal.

Thanks

---

