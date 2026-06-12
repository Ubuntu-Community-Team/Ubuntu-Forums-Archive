---
title: "Software management Error"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2008-02-18
Whenever I try to go into Add.Remove applications, it gives me this error message: > Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I tried running the command, and got this output:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1376kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 147272 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


So, I tried going into Synaptic and selecting the option to fix broken packages, and got this error message:

> E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins


I remember that I was trying to install compiz-fusion on feisty when this happened. Does anybody have any ideas on how I could fix this?

---

### Post by aysiu on 2008-02-18
Maybe try deleting the offending package? ```
sudo rm /usr/lib/compiz/libgconf.so
``` Or, the safer way would be Alt-F2 ```
gksudo nautilus
``` and then navigate to /usr/lib/compiz and move the libgconf.so file to the trash.

---

### Post by amtur_poet on 2008-02-19
No, that didn't work. Any other suggestions, please? :(

---

### Post by aysiu on 2008-02-19
> **amtur_poet said:**
> No, that didn't work. Any other suggestions, please? :(
No other suggestions, but can you be more specific than "that didn't work"? What error message did you get?

---

### Post by amtur_poet on 2008-02-19
Whoops, sorry. I should have been more specific. Nothing has changed in the error messages. I tried restarting Ubuntu, but it froze the boot at a screen with a blinking " _ " symbol.

---

