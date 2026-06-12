---
title: "Failed upgrade from 10.04 to 10.10"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by reddax on 2011-10-30
Hello people,

I have a problem upgrading to 10.10, I got a message saying that the upgrade failed and the system might have become unusable. When I reboot this is what I get:

```

Verifying DMI Pool Data .........
error: no module specified.
error: no suitable mode found.
error: unknown command 'terminal'. 

``````

Ubuntu 10.10 ivaylo-desktop tty1

Last Login: Sun Oct 30 21:10:31 EET 2011 on tty1

Linux ivaylo-destop 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 15:19:15 UTC 2001 i686 GNU/Linux

Ubuntu 10.10

Welcome to Ubuntu!
* Documentation https://help.ubuntu.com

New relese 'natty' available.

Run 'do-release-upgrade' to upgrade to it.

```After I run the command this is what I get:

```

Broken packages.

Your system contains broken packages that couldn't be fixed with this software. Please fix them first using synaptic or apt-get before proceeding.

Preparing the upgrade failed. Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

=== Command detached from window (Sun Oct 30 18:06:05 2011) ===
=== Command terminated with exit status 1 (Sun Oct 30 18:06:05 2011) ===

```I've read similar problems and I guess it's because of the non-ubuntu repositories that should've been disabled before installation... Is there a way to remove them now and restore the system before the update? I tried booting from CD but didn't work. :confused:

Thanks for your time.

---

### Post by zvacet on 2011-10-31
I think you  have problems,because you didn´t get your 10.10 up-to-date.Only after that you can go for upgrade.Try with 

```
sudo dpkg --configure -a
sudo apt-get -f install
```

If you get any errors from those commands post them here.

---

### Post by reddax on 2011-10-31
Thank you. :KS This is what I get for the first one: 

```

libgnome-desktop-2-17
ibus-gtk
kdebase-workspace
kdesudo
libakonadiprivate1
libplasma-geolocation-interface4
python-gnomeapplet
kdemultimedia-kio-plugins
seahorse
libkmime4
python-mediaprofiles
libdict-1.0-6
libtelepathy-logger1
libgtk-vnc-1.0-0
libwxgtk-2.6.0
libweather1
libgpod4
python-twisted-web
gnome-system-log
avidemux-plugins-common
plasma-widgets-workspace

Processing was halted because there were too many errors.

```And this is for the second one:

```

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by help packages.

E: Unable to correct dependencies.

```

---

### Post by pavi_elex on 2011-11-04
Try to fix broken packages through synaptic package manager.
If still it does not work,
Go in recovery mode and fix broken packages there.

---

