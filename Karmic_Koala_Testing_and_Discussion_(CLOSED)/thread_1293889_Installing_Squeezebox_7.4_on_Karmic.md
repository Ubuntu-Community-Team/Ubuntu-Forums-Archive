---
title: "Installing Squeezebox 7.4 on Karmic"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mavros on 2009-10-17
Has anyone successfully installed Squeezebox 7.4 on Karmic? The Deb package installation breaks of with an error stating that Mysql 5.0 can not be installed. I noticed that Karmic has Mysql 5.1 in the repository but it is not installed by default.

---

### Post by kvarley on 2009-10-17
Did you run the deb as sudo?

---

### Post by mavros on 2009-10-17
Used both "Open with Gdebi" in the GUI and ran in the terminal with "sudo gdebi .."

This is what I get:
sudo gdebi squeezeboxserver_7.4.0_all.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Cannot install 'mysql-server-5.0'

---

### Post by clayton on 2009-10-18
Same issue here.

---

### Post by kvarley on 2009-10-20
Have you tried installing the mysql package from the Jaunty repositories? Then run the installer and it should work.

---

### Post by imaca on 2009-10-21
Yes I have it installed and running.
How long ago did you try installing it?
From memory I think there was a fix to mysql recently - something about it actually being 5.0 even though it was called 5.1 so changing the name to 5.0 or something.
Anyway, it does work.

---

### Post by kvarley on 2009-10-21
I haven't tried to install it. Just guessing. Usually if it say you haven't got x package or there was an error with x package, check you have it installed.

Glad I could help xD [SOLVED]

---

### Post by imaca on 2009-10-22
this is what I have in synaptic:

---

### Post by kvarley on 2009-10-22
Remove all mysql then install the correct version?

---

### Post by mavros on 2009-10-24
I removed MySql 5.1 and installed 5.0.  The installen runs a ltille longer but finally fails due to dependency resolution problems. This is what happens

[COLOR=RoyalBlue]Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 145457 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb[/COLOR]

as mentioned there indeed seems to be a mixup in the 5.0 package it also contains 5.1 elements. 

Independent if it is already there or not the Squeezebox Deb wants to install MySql 5.0 and can't (according to the initial error message) and iIf I install it before running the SC Deb it crashes on dependency problems.  I will contact the Logitech and for now back to Windows I suppose.

---

