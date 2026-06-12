---
title: "installArchives() failed 11.04 Natty"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by StepNjump on 2012-04-19
Hi guys,

For a few days now, something happened... I can no longer download any updates and/or install new applications.

When I try sudo apt-get update, everything terminates normally in the terminal.

Here is what I get in the details of the error when I tried to install a package dos emulator. Thanks for your help guys.

installArchives() failed: Selecting previously deselected package dosemu.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 312564 files and directories currently installed.)
Unpacking dosemu (from .../dosemu_1.4.0+svn.1999-2_i386.deb) ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.UTF8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up nvidia-173 (173.14.30-0ubuntu1.1) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up dosemu (1.4.0+svn.1999-2) ...
Processing triggers for menu ...
Errors were encountered while processing:
 nvidia-173
Setting up nvidia-173 (173.14.30-0ubuntu1.1) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1

Here is what I get when I try to run the update manager:

installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 312875 files and directories currently installed.)
Preparing to replace libva-x11-1 1.0.12-1~xorgedgers (using .../libva-x11-1_1.0.14-1~xup1_i386.deb) ...
Unpacking replacement libva-x11-1 ...
Preparing to replace libva1 1.0.12-1~xorgedgers (using .../libva1_1.0.14-1~xup1_i386.deb) ...
Unpacking replacement libva1 ...
Preparing to replace libva-glx1 1.0.12-1~xorgedgers (using .../libva-glx1_1.0.14-1~xup1_i386.deb) ...
Unpacking replacement libva-glx1 ...
Preparing to replace nvidia-current 295.20-0ubuntu1~xedgers~natty1 (using .../nvidia-current_295.40-0ubuntu1~natty~xup1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Preparing to replace nvidia-settings 295.20-0ubuntu1~xedgers~natty1 (using .../nvidia-settings_295.40-0ubuntu1~natty~xup1_i386.deb) ...
Unpacking replacement nvidia-settings ...
dpkg: warning: unable to delete old directory '/usr/lib/nvidia-settings/include/NVCtrl': Directory not empty
dpkg: warning: unable to delete old directory '/usr/lib/nvidia-settings/include': Directory not empty
dpkg: warning: unable to delete old directory '/usr/lib/nvidia-settings': Directory not empty
Processing triggers for man-db ...
Setting up nvidia-173 (173.14.30-0ubuntu1.1) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up libva-x11-1 (1.0.14-1~xup1) ...
Setting up libva1 (1.0.14-1~xup1) ...
Setting up libva-glx1 (1.0.14-1~xup1) ...
Setting up nvidia-current (295.40-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up nvidia-settings (295.40-0ubuntu1~natty~xup1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-173
 nvidia-current
Setting up nvidia-173 (173.14.30-0ubuntu1.1) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nvidia-current (295.40-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2

---

### Post by zvacet on 2012-04-19
```
sudo dpkg --configure -a
```

---

### Post by StepNjump on 2012-04-20
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

Thanks for your help. Here is what I received now doing the dpkg commands you suggested:

Setting up nvidia-173 (173.14.30-0ubuntu1.1) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nvidia-current (295.40-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-173
 nvidia-current

Is there a problem with my nvidia drivers?

---

### Post by zvacet on 2012-04-21
It looks like it.I don´t use nvidia so I have no experience,but on [this]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_manually_review.2BAC8-tweak_alternatives_settings") page maybe you can find solution.

---

