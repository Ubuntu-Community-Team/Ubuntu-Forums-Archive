---
title: "how to install Gnome 3 on 10.04 LTS"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2011-06-11
hey people!!
I intend to install Gnome 3 on My Ubuntu 10.04 LTS and have found these instructions by goggling around a bit.

need to verify if this is fine and will not break anything.

1) Install Dependencies
Run this command to install the GNOME Shell dependencies.
$ sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev
2) Download the Source
Get the script to setup your jhbuild environment.
$ wget [http://git.gnome.org/browse/gnome-sh...build-setup.sh](http://git.gnome.org/browse/gnome-sh...build-setup.sh)
Make the script executable.
$ chmod +x gnome-shell-build-setup.sh
Execute the script. This will install jhbuild.
$ ./gnome-shell-build-setup.sh
3) Build GNOME 3
This command will download the latest source code and build GNOME 3. GNOME Shell includes 40+ packages that need to be downloaded and built. This can take a significant amount of time to complete so be patient.
$ jhbuild build
4) Keep GNOME 3 Up to Date
You are running the bleeding edge version of GNOME 3 and because of this the code in the git repositories will be constantly changing. To test the latest changes after your initial insallation simply run the following command. This automatically update your local copy of the source code and rebuild if there are any changes to GNOME 3 package or its dependencies.
$ jhbuild build
Starting GNOME Shell
Alt+F2 and enter:
$ ~/gnome-shell/install/bin/gnome-shell –-replace
Stopping GNOME Shell
To exit and return to your default Gnome 2 hit Alt+F2 and enter:
debugexit


Thanks for your assistance!

---

### Post by richlyn9 on 2011-06-11
I ran the first 3 steps and it gave me this erros


richlyn@richlyn-lucid:~$ sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev
[sudo] password for richlyn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtiff4-dev is already the newest version.
libtiff4-dev set to manually installed.
build-essential is already the newest version.
E: Couldn't find package autopoint
richlyn@richlyn-lucid:~$ wget [http://git.gnome.org/browse/gnome-sh...build-setup.sh](http://git.gnome.org/browse/gnome-sh...build-setup.sh)
--2011-06-11 18:17:15--  [http://git.gnome.org/browse/gnome-sh...build-setup.sh](http://git.gnome.org/browse/gnome-sh...build-setup.sh)
Resolving git.gnome.org... 209.132.180.173
Connecting to git.gnome.org|209.132.180.173|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `gnome-sh...build-setup.sh.1'

    [  <=>                                  ] 2,843       6.95K/s   in 0.4s    

2011-06-11 18:17:21 (6.95 KB/s) - `gnome-sh...build-setup.sh.1' saved [2843]

richlyn@richlyn-lucid:~$ chmod +x gnome-shell-build-setup.sh
chmod: cannot access `gnome-shell-build-setup.sh': No such file or directory
richlyn@richlyn-lucid:~$

---

### Post by dino99 on 2011-06-11
install it only if you need/want headache, otherwise stay with gnome2 (its far better)

That said, only use gnome3-team & ricotz/testing ppas on launchpad, thats all

---

### Post by richlyn9 on 2011-06-13
Thats a wise advise....
I am aware the perils of installing Gnome3 on Lucid however was excited of installing the latest to get the new feel and look. Guess its better to wait and see what happens in Ubuntu's next release 6 months later.

Gnome3 will have to wait for me.

---

