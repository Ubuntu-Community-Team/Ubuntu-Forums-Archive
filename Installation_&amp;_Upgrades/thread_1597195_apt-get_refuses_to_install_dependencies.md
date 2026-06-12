---
title: "apt-get refuses to install dependencies"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by dathui on 2010-10-15
I'm running Kubuntu 10.10 and am trying to change my bootscreen so I installed StartUp-Manager and then I tried to install usplash, but I get this error which makes me slightly confused:

sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnupg-agent : Depends: pinentry-gtk2 but it is not going to be installed or
               pinentry-curses but it is not going to be installed or
               pinentry
 usplash : Depends: upstart-job
           Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be     installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
E: Broken packages

Previously apt-get has been happy to install dependencies. I'm new to Linux so if you need any more information just shout and I'll edit that in.

---

### Post by garvinrick4 on 2010-10-15
Is plymouth being used in kubuntu? Making usplash obsolete.
With plymouth have a variety of different themes.
Install the one or a variety of plymouth themes. 
Run first piece of code and choose which one you desire then
after run second piece of code to update.
```
sudo update-alternatives --config default.plymouth
``` 
```
sudo update-initramfs -u
```

---

### Post by garvinrick4 on 2010-10-15
```
ick@rick-HP-G71-Notebook-PC:~$ aptitude show plymouth
Package: plymouth                 
State: installed
Automatically installed: no
Version: 0.8.2-2ubuntu5
Priority: required
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 475k
Depends: libc6 (>= 2.8), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1 (>=
         2.4.20-3~), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3),
         libplymouth2 (= 0.8.2-2ubuntu5), upstart-job, udev (>= 149-2), mountall
         (>= 2.0), initramfs-tools
Recommends: plymouth-theme-ubuntu-text | plymouth-theme
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4), kdm (< 4:4.4.2-0ubuntu6),
        lubuntu-plymouth-theme (<= 0.4), ubuntustudio-plymouth-theme (<= 0.38),
        xubuntu-plymouth-theme (< 10.04.4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background.

rick@rick-HP-G71-Notebook-PC:~$ 

```

---

