---
title: "initramfs-tools-bin apt-get hell"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by davidrod on 2013-12-09
Boot partition full, failed install, cleaned up, now I get:

runner@EPA:/var/lib/dpkg$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not installed
 initramfs-tools : Depends:** initramfs-tools-bin** (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is installed

I've tried:
[B][SIZE=4]1. [/SIZE]
sudo dpkg --purge intramfs-tools-bin[/B]
**sudo dpkg --clear-avail**
**sudo apt-get update**
**sudo apt-get install [B]intramfs-tools-bin**[/B]
**sudo apt-get dist-upgrade**

[SIZE=4]**2. **[/SIZE]
Open the following file;
  sudo gedit /var/lib/dpkg/status
  Remove all entries related to initramfs.
  Open synaptic and remove all packages relating to initramfs.
  sudo apt-get update(or reload the repos in synaptic)
  Try installing once more.
 
[SIZE=4]**3.**[/SIZE]
Open the following file;
  sudo gedit /var/lib/dpkg/status
  Remove all entries related to initramfs.
  Open synaptic and remove all packages relating to initramfs.
  sudo apt-get update(or reload the repos in synaptic)
  Try installing once more.
 
[SIZE=4]**4.**[/SIZE]
curl -O [http://mirrors.kernel.org/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13_i386.deb)
sudo dpkg -i initramfs-tools-bin_0.99ubuntu13_i386.deb

Can't get initramfs-tools purged and then installed correctly.  

Please help.  Thanks,

---

### Post by davidrod on 2013-12-09
Here's some more info:
Building complete list of updates ..
 Now updating curl ..


[LIST]**Installing package(s) with command apt-get -y  install curl ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating libcurl3 ..

[LIST]**Installing package(s) with command apt-get -y  install libcurl3 ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating libcurl3-gnutls ..

[LIST]**Installing package(s) with command apt-get -y  install libcurl3-gnutls ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating libpixman-1-0 ..

[LIST]**Installing package(s) with command apt-get -y  install libpixman-1-0 ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating linux-firmware ..

[LIST]**Installing package(s) with command apt-get -y  install linux-firmware ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating linux-headers-generic-lts-quantal ..

[LIST]**Installing package(s) with command apt-get -y  install linux-headers-generic-lts-quantal ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-44-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating linux-libc-dev ..

[LIST]**Installing package(s) with command apt-get -y  install linux-libc-dev ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!** 
[/LIST]

Now updating rsyslog ..
**Installing package(s) with command apt-get -y  install rsyslog ..** 
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on kpartx-boot; however:
  Package kpartx-boot is not installed.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-42-generic:
 linux-image-3.5.0-42-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-42-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-41-generic:
 linux-image-3.5.0-41-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-41-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.5.0-43-generic:
 linux-image-3.5.0-43-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.5.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-41-generic; however:
  Package linux-image-3.5.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dmraid
 linux-image-3.5.0-42-generic
 linux-image-3.5.0-41-generic
 mdadm
 linux-image-3.5.0-43-generic
 linux-image-generic-lts-quantal
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dmraid : Depends: kpartx-boot but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!**

---

### Post by ian-weisser on 2013-12-09
I think you figured out that the same problems are preventing your package actions, no matter how cleverly you try to work around them.
You seem to have more than one problem.

For example, you seem to be running trying to install 12.10 kernels (linux-image-3.5.0-41-generic),
But you're running a 12.04 version of initramfs-tools-bin (0.99ubuntu13.4)

Usually, this means you had a partial upgrade, or you installed a PPA or other Non-Ubuntu software. Do you recall either of those actions?
Perhaps you could show us your /etc/apt/sources.list and /etc/apt/sources.list.d?

I agree that initramfs-tools-bin is key. The tilde (~) in the package name, and the less-than symbol (<) (< 0.99ubuntu13.1~) makes a PPA seem likely. 

If you discover a few PPAs among your sources, simply disable them. Comment them out with a #.
After you have scrubbed your sources, try to remember what you wanted to install from those packages. Remove that top-level package and work down through it's dependencies. Don't start at the bottom - it will remove a lot more than you expect (and may leave your system unbootable).

For example, seems like you wanted mdadm. If that was the PPA that started the problem, then disable the PPA first. Then:
```
sudo dpkg --remove mdadm
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
```
See how the error messages change.

---

