---
title: "Problem installing Adobe Flash Player Version 10.1"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by tanya_814 on 2010-07-21
Hi,

(I'm not too good with computers, so please excuse my inappropriate language!)
I installed the package for Adobe Flash Player (version 10.1) but I can't seem to run it or something. The Adobe site told me:
Double-click on the .deb package and follow the instructions to complete installation.

-or-
Issue one of the following commands from the terminal:

    * dpkg --install [filename].deb
    * dpkg -i [filename].deb

------------
I tried the first thing, and it says its installed (asks me if I want to reinstall). Then I tried putting the commands in the terminal and for both commands, it says "dpkg: requested operation requires superuser privilege"
Should I try downloading the other versions (tar.gz, .rpm, via APT, YUM)? I have no clue what to do!
Any help would be MUCH appreciated! Thank you in advance!

-Tanya

---

### Post by snowpine on 2010-07-21
The short answer is that you need to use "sudo" to execute the command as root:

```
sudo dpkg -i [filename].deb
```

The long answer is that, in Ubuntu, we do not typically download and install stuff from the Internet. If you go to the Ubuntu Software Center and search for "flash", you can one-click-install the correct version of Flash for your Ubuntu release.

---

### Post by tommcd on 2010-07-21
> **tanya_814 said:**
> 
    * dpkg --install [filename].deb
    * dpkg -i [filename].deb

------------
... for both commands, it says "dpkg: requested operation requires superuser privilege"

You should first uninstall any flash you may have previously installed.
You will need to run those dkkg commands with sudo to gain super user privileges.

What version of Ubuntu are you using??? Are you using 32bit or 64bit Ubuntu???
 If you are using the current version (lucid 10.04) the flash 10.01 is in the Ubuntu repos:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)
So just open a terminal and run:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install flashplugin-installer

```
The packages from the Ubuntu repos should always be your first choice, especially if you are "not too good with computers".

---

