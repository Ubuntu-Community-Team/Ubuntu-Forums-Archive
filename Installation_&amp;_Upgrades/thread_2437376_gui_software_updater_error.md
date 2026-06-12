---
title: "gui software updater error"
date: 2020-02-22
forum: Installation &amp; Upgrades
---

### Post by artunix on 2020-02-22
ubuntu 18.04.4 lts 64bit

will not upgrade/update the downloaded upgrades/updates because of this error:


dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libreoffice-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

how do get apt to delete the downloaded upg/upd(s) and redownload?.

or how do i fix the above error to get the gui software updater to work again?

and how do i get rid of this file?
/var/crash/_usr_lib_update-notifier_apt_check.py.0.crash

thanks.

edit:

current kernel: 4.15.0-76-generic [so said: ls /boot | grep vmlinuz]

i think part of the upd/upg has kernel 5

---

### Post by mörgæs on 2020-02-23
First let's forget about using the GUI. Please close all applications, reboot, run ```
sudo apt update
``` and ```
sudo apt dist-upgrade
``` and post their output in CODE tags.

---

### Post by Impavidus on 2020-02-23
Also try```
sudo apt clean
```That will remove the locally stored packages, forcing the package manager to download them again. It looks like some files got damaged.

---

### Post by artunix on 2020-02-23
sudo apt update =
35 packages can be upgraded. Run 'apt list --upgradable' to see them.

sudo apt dist-upgrade =
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  fwupd-signed libxmlb1 linux-headers-4.15.0-88
  linux-headers-4.15.0-88-generic linux-image-4.15.0-88-generic
  linux-modules-4.15.0-88-generic linux-modules-extra-4.15.0-88-generic
The following packages will be upgraded:
  apport apport-gtk dmidecode fwupd fwupdate fwupdate-signed
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libfwupd2
  libjavascriptcoregtk-4.0-18 libnautilus-extension1a libnss-myhostname
  libnss-systemd libpam-systemd libpq5 libsystemd0 libudev1
  libwebkit2gtk-4.0-37 linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev nautilus nautilus-data ppp python3-apport
  python3-problem-report systemd systemd-sysv udev xserver-common
  xserver-xephyr xserver-xorg-core xserver-xorg-legacy xwayland
35 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/95.6 MB of archives.
After this operation, 338 MB of additional disk space will be used.
Do you want to continue?

sudo apt clean =
nothing, no output.

already tried clean, and update before posting here; did not work. looks like 'sudo apt dist-upgrade' might work never saw the 338mb load with other internet tries.

will try it tomorrow.

something else now when i shutdown laptop have to use sudo password because some program is running that would like to not shutdown laptop.

thanks for the help.

---

### Post by artunix on 2020-02-23
tried 'sudo apt dist-upgrade'; does not fix problem, gets packages (42), starts install process, and dies like before:

Get:42 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 xwayland amd64 2:1.19.6-1ubuntu4.4 [863 kB]
Fetched 95.6 MB in 54s (1,762 kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libreoffice-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


there is something in 'libreoffice-common' it does not like.

---

### Post by Impavidus on 2020-02-23
Try this one:```
sudo apt-get clean
```That should really remove the cache. apt-get, as opposed to apt, is a bit more predictable (as in, has a better manual page).

BTW, you do keep good backups of your files, I hope? If a package file can get corrupted, so can your holiday pictures.

---

### Post by artunix on 2020-02-24
fixed 
clean reinstall of OS

---

