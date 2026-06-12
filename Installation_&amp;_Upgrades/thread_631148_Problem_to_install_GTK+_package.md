---
title: "Problem to install GTK+ package"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Fanatico on 2007-12-04
I have Ubuntu 7.10 and I am trying to compile utility RutilTv0.16 and receive the following errors:

[B]$:~/Installations/RutilTv0.16$ ./configure.sh --launcher=external
Using helper_launcher.sh as launcher proxy, you may need or want to tune this script.
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Please install (or upgrade to) GTK+ 2.6.0, at least.[/B]

I understand that I have to install gtk+-2.0.pc package

I downloaded libgtk2.0-dev_2.8.20-0ubuntu1.1_i386.deb
When I tried to install it Package Installer says: **"Dependency is not satisfiabe: libgtk2.0-0"**

I downloaded libgtk2.0-0_2.8.20-0ubuntu1.1_i386.deb
When I tried to install it Package Installer says: **"A later version is already installed"**

What is wrong? Please help! Thanks

---

### Post by briandu on 2007-12-04
MayI suggest you fire off apt-get update _**[COLOR=Red]first[/COLOR]**_ then use Synaptic to get the GTK files.

You may find you have dependencies problems.

---

### Post by Fanatico on 2007-12-04
> **briandu said:**
> MayI suggest you fire off apt-get update _**[COLOR=Red]first[/COLOR]**_ then use Synaptic to get the GTK files.

You may find you have dependencies problems.

Thank you for your response. I am newbie in Linux. Could you provide more details?

---

### Post by briandu on 2007-12-04
OK so start with

open a terminal session and enter sudo apt-get update

wait for it to finish

THEN

under System / Administration look for Synaptic. Click it (you will have to put in a pwd)

THEN find search button and enter GTK and get a list of files, Search for the file you are looking for and then press tickbox "mark for installation¨ and then apply

then wait for install to complete

---

### Post by Fanatico on 2007-12-04
> **briandu said:**
> OK so start with

open a terminal session and enter sudo apt-get update

wait for it to finish

THEN

under System / Administration look for Synaptic. Click it (you will have to put in a pwd)

THEN find search button and enter GTK and get a list of files, Search for the file you are looking for and then press tickbox "mark for installation¨ and then apply

then wait for install to complete

Thanks

---

