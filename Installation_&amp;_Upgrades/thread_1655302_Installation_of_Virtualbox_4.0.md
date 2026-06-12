---
title: "Installation of Virtualbox 4.0"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by gdawg on 2010-12-29
Hello everybody, during  an installation of virtualbox 4.0 I encountered the following errors:
Setting up virtualbox-4.0 (4.0.0-69151~Ubuntu~maverick) ...
Adding group `vboxusers' (GID 123) ...
Done.
update-rc.d: warning: vboxdrv stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
Setting up libhal1 (0.5.14-0ubuntu6) ...
Setting up libsdl-ttf2.0-0 (2.0.9-1build1) ...
Processing triggers for python-central ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
[U] linux-image-2.6.35-24-generic
 linux-image-generic
 linux-generic[/U]
_E: Sub-process /usr/bin/dpkg returned an error code (1)_

How can I correct these errors?
I'm running Ubuntu 10.10, PinguyOS, PCLinux, and Win 7 on a Dell Desktop 530S. Any help will be appreciated.

---

### Post by sikander3786 on 2010-12-29
Please post the complete output of these commands.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -a
```

```
sudo apt-get update && sudo apt-get install virtualbox-4.0
```

While posting, click the # icon in post menu and paste your text in between the generate [code] tags to make it easier to read.

---

