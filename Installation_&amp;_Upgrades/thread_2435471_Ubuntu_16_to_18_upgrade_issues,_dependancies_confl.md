---
title: "Ubuntu 16 to 18 upgrade issues, dependancies conflicts"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by gus20 on 2020-01-21
Hello,

I'm new to Linux and was trying to upgrade Ubuntu 12 on a virtual server for a friend. It upgraded to 14 and 16 without major issues, I used "apt-get -f install" at one point and it fixed itself. I followed a lot of tutorials and forum posts God bless those people :)

Issues arised during upgrade from 16 to 18. It gave some error with a very long report, and now shows dependancies error and "apt-get -f install" cannot fix it, it's running in circles giving same error.

It seems when I log in via SSH it says Welcome to Ubuntu 18.04.3 LTS. But then also "New release '16.04.6 LTS' available. Run 'do-release-upgrade' to upgrade to it."

It also has Webmin and Webmin says reboot is pending but it cannot reboot there (nothing happens) or in terminal (command is missing). I'm not sure it would even boot up in current state. I tried:

```

sudo shutdown -r now
sudo: shutdown: command not found


sudo reboot now
sudo: reboot: command not found


sudo systemctl reboot
sudo: systemctl: command not found

```

Does anyone know what the issue might be and ways to fix it?

I didn't try removing/auto cleaning dependancies yet as was afraid it might remove some important stuff like some people mentioned.

Here is the error about dependancies, it appears regularly and [COLOR=#000000][FONT=Helvetica]"[/FONT][/COLOR]apt-get install systemd --dry-run" is just an example"

```
apt-get install systemd --dry-run
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 console-setup : Depends: keyboard-configuration (= 1.108ubuntu15.5) but 1.178ubuntu2.9 is to be installed
 console-setup-linux : Depends: keyboard-configuration (= 1.108ubuntu15.5) but 1.178ubuntu2.9 is to be installed
 indicator-session : Depends: systemd-services
                     Recommends: unity-control-center-signon but it is not installable or
                                 gnome-control-center-signon but it is not installable
 initramfs-tools : Depends: initramfs-tools-core (= 0.122ubuntu8.16) but 0.130ubuntu3.9 is to be installed
 libc-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1 is to be installed
 libc-dev-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1 is to be installed
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu11) but 2.27-3ubuntu1 is to be installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu11) but 2.27-3ubuntu1 is to be installed
 locales : Depends: libc-bin (> 2.27)
 systemd : Conflicts: upstart but 1.13.2-0ubuntu21.1 is to be installed
           Recommends: networkd-dispatcher but it is not going to be installed
 ubuntu-desktop : Depends: gdm3 but it is not going to be installed
                  Depends: gnome-shell but it is not going to be installed
                  Depends: gnome-shell-extension-appindicator but it is not going to be installed
                  Depends: gnome-shell-extension-ubuntu-dock but it is not going to be installed
                  Depends: gstreamer1.0-packagekit but it is not going to be installed
                  Depends: libu2f-udev but it is not going to be installed
                  Depends: spice-vdagent but it is not going to be installed
                  Recommends: dirmngr
                  Recommends: fonts-indic but it is not going to be installed
                  Recommends: fonts-noto-cjk but it is not going to be installed
                  Recommends: fonts-noto-color-emoji but it is not going to be installed
                  Recommends: fonts-ubuntu but it is not going to be installed
                  Recommends: fwupd
                  Recommends: fwupdate
                  Recommends: fwupdate-signed
                  Recommends: gnome-calendar but it is not going to be installed
                  Recommends: gnome-getting-started-docs but it is not going to be installed
                  Recommends: gnome-initial-setup but it is not going to be installed
                  Recommends: gnome-software-plugin-snap but it is not going to be installed
                  Recommends: gnome-todo but it is not going to be installed
                  Recommends: gpg-agent
                  Recommends: kerneloops but it is not going to be installed
                  Recommends: libreoffice-style-breeze but it is not going to be installed
                  Recommends: network-manager-config-connectivity-ubuntu but it is not going to be installed
                  Recommends: orca but it is not going to be installed
                  Recommends: packagekit
                  Recommends: printer-driver-brlaser but it is not going to be installed
                  Recommends: printer-driver-m2300w but it is not going to be installed
                  Recommends: snapd but it is not going to be installed
                  Recommends: system-config-printer but it is not going to be installed
                  Recommends: ubuntu-report but it is not going to be installed
                  Recommends: ubuntu-software but it is not going to be installed
                  Recommends: ubuntu-web-launchers but it is not going to be installed
                  Recommends: xdg-desktop-portal-gtk
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

Information on upstart:

```

sudo dpkg -P upstart
**dpkg:** dependency problems prevent removal of upstart:
 ubuntu-minimal depends on upstart; however:
  Package upstart is to be removed.
 avahi-daemon depends on upstart (>= 0.6.7-4).


**dpkg:** error processing package upstart (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 upstart

```

I was planning to try removing avahi-daemon, then upstart, then install systemd, ubuntu-minimal and avahi-daemon, and upstart again and then try to reboot but not sure it would work and I'm concerned it wouldn't boot up and since it's virtual server if it breaks I would probably have to delete it and create a new one but would prefer to keep it as it has some data.

Thank you!

---

### Post by mörgæs on 2020-01-22
> **gus20 said:**
> ...I would probably have to delete it and create a new one

Yes, the safe approach is to create a new virtual server and just transfer the data from old to new. The Ubuntu 12-14-16-18   family reunion is hardly worth keeping.

---

