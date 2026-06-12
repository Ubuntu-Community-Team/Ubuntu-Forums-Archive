---
title: "[SOLVED] Kubuntu dependencies"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by SkonesMickLoud on 2008-07-04
When I tried to install KDE this morning, all seemed to go well until I tried to log in.  Got the standard Ubuntu brown screen and a message popped up telling me that my session lasted less than 10 seconds, and I should contact my sysadmin (well, me).  Tried 2 more times and got the same message.

I logged back into gnome and ran "sudo aptitude remove kubuntu-desktop" and all was removed (except for the kubuntu shutdown splash screen).  Restarted and ran "sudo aptitude update && install kubuntu-desktop" and got the following error:

```
skones@skones-laptop ~: sudo aptitude update && sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kmplayer-konq-plugins: Depends: konqueror but it is not installed
  konq-plugins: Depends: konqueror (>= 4:3.5.8-1) but it is not installed
  konqueror-nsplugins: Depends: konqueror but it is not installed
  strigi-applet: Depends: konqueror but it is not installed
E: Unmet dependencies. Try using -f.

```

"apt-get/aptitude -f install" both return the same thing:

```
skones@skones-laptop ~: sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  konqueror
Suggested packages:
  gij-4.1 libgcj7-awt libjessie-java
The following NEW packages will be installed:
  konqueror
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/1967kB of archives.
After this operation, 5390kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166016 files and directories currently installed.)
Unpacking konqueror (from .../konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[aptitude returns a much much longer version which says essentially the same thing]

I get the same error when running "sudo aptitude remove -f kubuntu-desktop".

---

### Post by Partyboi2 on 2008-07-04
Looks like you may need to use the force option. Here are a few bug reports with people having same problem
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/192889](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/192889)
[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/119664](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/119664)

---

### Post by SkonesMickLoud on 2008-07-04
> **Partyboi2 said:**
> Looks like you may need to use the force option. Here are a few bug reports with people having same problem
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/192889](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/192889)
[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/119664](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/119664)

Force returns the same result, and I caught those bug reports 5 minutes after I posted this, but I'll keep this thread up in case someone knows.

Thanks though.

[edit]  Copypasta'd wrong.  One of the links in the bug report had a random % in it.

Anyone else with this problem, try:

```
sudo dpkg -i --force-all /var/cache/apt/archives/konqueror_*.deb && sudo aptitude *whatever you were trying to do before*
```

---

