---
title: "Updater Won't Work - Broken Software Index"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by chaser209 on 2007-09-04
Please help; I've tried everything and cannot figure out how to fix my updater. When i go to updates, it says software index broken, please use package manager synaptic to fix or sudo apt-get install -f.

I can't seem to find what's broken in Synaptic.

When i do the code in terminal, i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  screenlets-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.8kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 159472 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.1.2-bzr78-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Someone please help before I destroy this!!!:mad::mad:

---

### Post by Pumalite on 2007-09-04
Try this: sudo dpkg --remove --force-remove-<packagename>
Or:
dpkg-divert --remove /usr/lib/<packagename>

You have to find out which package is broken. Have you tried Synaptic>Edit>Fix Broken Packages?

What about: sudo dpkg --configure -a

---

### Post by chaser209 on 2007-09-04
Everytime I try to fix the broken package in synaptic i get this:

E: /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0

Neither of the two commands you posted seemed to work. I just cannot figure this out.

---

### Post by Pumalite on 2007-09-04
Let's try this:

To manually abort the error so you can have a functioning package manager again (but with a bum package), edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

---

### Post by Pumalite on 2007-09-04
aptitude show <package_name> will give you a detailed description including installation status and dependencies.

---

