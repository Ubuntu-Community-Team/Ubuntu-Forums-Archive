---
title: "Update manager failed to fetch sources"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by bluesdream on 2010-01-04
I'm running 9.04 and trying to use the update manager.  On checking for updates, I get the error message:

W: Failed to fetch [http://mirror.uoregon.edu/ubuntu/archives/dists/jaunty/Release.gpg](http://mirror.uoregon.edu/ubuntu/archives/dists/jaunty/Release.gpg)  Could not connect to 69.219.142.196:21 (69.219.142.196). - connect (111 Connection refused)

W: Failed to fetch [http://mirror.uoregon.edu/ubuntu/archives/dists/jaunty/main/i18n/Translation-en_US.bz2](http://mirror.uoregon.edu/ubuntu/archives/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to 69.219.142.196:21 (69.219.142.196). - connect (111 Connection refused)

(more...)

This used to work, but now it doesn't.  I tried selecting all kinds of different sources in the "Software Sources" GUI.  And this seemed to change my /etc/sources.list accordingly.  **But**, whatever the hostname given (above mirror.uoregon...), that same IP address is shown 69.219.... huh?  I can browse the web, etc fine from this computer.

This happens to be running within VMWare Fusion.  I'm trying to get this to work in order to (among other things) upgrade to 9.10.

thanks.

---

### Post by tachuela on 2010-01-04
Did you use "Select Best Server"?

---

### Post by bluesdream on 2010-01-04
It goes through 291 tests and then says "No suitable download server was found.  Please check your Internet connection".

It's like the update manager's network connection isn't working, but it's working everywhere else.

---

### Post by Resu on 2010-01-04
Try selecting a random server from your country instead of using "Select Best Server".

---

### Post by bluesdream on 2010-01-04
Any server that I select results in a bunch of error messages like I posted in the first post.  It says "failed to fetch", and lists the selected server hostname, but also that same IP address every time.

---

