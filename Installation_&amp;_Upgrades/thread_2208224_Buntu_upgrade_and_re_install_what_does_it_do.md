---
title: "Buntu upgrade and re install: what does it do?"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by eric152 on 2014-02-27
Hello!

General question about LTS and Ubuntu: 
I am more used to the Debian  "dist upgrade" which allow distribution upgrade without re installation.  I read in many places that the Ubuntu variants require a re install, but  they also offer distribution upgrade, so I am a little confused,  especially about the consequences of "re install".  
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)  propose a re install without loosing /home and settings.
But what does a "re install or an upgrade exactly"? Does the computer settings in /etc get overwritten/reset? What about the own installed programs in /opt or /var? Everything gone?
More links to documentation will be welcome, but so far, I did not find much about the details...

---

### Post by sudodus on 2014-02-27
Before upgrading to the next version, make sure your present system is up to date.

```
sudo apt-get update
sudo apt-get upgrade
```

will make your present system up to date except when conflicts and concerning the kernel.

```
sudo apt-get dist-upgrade
```

will try to solve conflicts and update the kernel (within the current Ubuntu version).

See ```
man apt-get
```

-o-

The GUI tool for updates/upgrades will offer upgrades to the next version. The following command line will do it (in Ubuntu based flavours)

```
sudo do-release-upgrade
``` 

Add the option **-d** if you upgrade to the development release (today if you upgrade to Trusty Tahr).

Generally you can upgrade to the next version except for LTS versions, that can also upgrade directly to the next LTS version when available.

---

### Post by mastablasta on 2014-02-27
upgrade --- upgrades the system leaving your personal settings and files intact. PPA's, external repos... may not work after upgrade so it's better to disable them before doing the upgrade. i believe this is now done automaticly as i witnessed it in last upgrade.
reinstall ---- reinstalls the os, keeps any additional files and porgrams that were added after vanilla OS was installed (so it will keep files in /home). resets settings and such to defaults.

---

