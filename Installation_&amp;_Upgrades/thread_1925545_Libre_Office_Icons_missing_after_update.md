---
title: "Libre Office Icons missing after update"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by smilingfrog on 2012-02-14
Hi,
This is more an FYI. I searched pretty hard for anyone else having this problem, but I couldn't find evidence of it.

I updated my kernel to 2.6.32-38, and after that I noticed that all my libreoffice icons had been replaced with text. Even going to the Tools>Customize>Toolbars all the icons were missing.

For whatever reason, the system deleted the icons during the update. This was fixed by running
```
sudo apt-get install libreoffice-gnome
```
which re-installs the base interface (including icons) for libreoffice to run on gnome. No need to reinstall everything.

Problem is now fixed for me. I hope that if anyone else loses their icons this post may help them.

---

### Post by ABitTooSpicy on 2012-08-10
I am having the same issue and I tried the command however it didn't work... =(

I am using 11.10 and just upgraded from Libre 3.4 to 3.5 and lost all the icons, they all turned into plain text.

Here is the message I get when I run the command:

```
username@computername:~$ sudo apt-get install libreoffice-gnome
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice-gnome is already the newest version.
The following package was automatically installed and is no longer required:
  libreoffice-l10n-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 69 not upgraded.
N: Ignoring file '50unattended-upgrades.distrib' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

Any ideas what I should try next? 

I've been Ubuntu for a couple of releases but still a newbie anytime I run into issues... 

> **smilingfrog said:**
> Hi,
This is more an FYI. I searched pretty hard for anyone else having this problem, but I couldn't find evidence of it.

I updated my kernel to 2.6.32-38, and after that I noticed that all my libreoffice icons had been replaced with text. Even going to the Tools>Customize>Toolbars all the icons were missing.

For whatever reason, the system deleted the icons during the update. This was fixed by running
```
sudo apt-get install libreoffice-gnome
```
which re-installs the base interface (including icons) for libreoffice to run on gnome. No need to reinstall everything.

Problem is now fixed for me. I hope that if anyone else loses their icons this post may help them.

---

### Post by SENSHES on 2012-09-04
Hi,

FYI - I run into the same issue (Xubuntu 12.04 32bit, LibreOffice 3.5.4). My solution: Switch to another symbol style in the option menu, for example from 'tango' to 'oxygen'. 
By simply doing that all my icons suddenly appeared :-)

BTW: If there is no choice available install a second symbol style. And if you like your original style most simply switch back. Hope this hint will save some time for somebody else.

Regards,
Ulrich

---

