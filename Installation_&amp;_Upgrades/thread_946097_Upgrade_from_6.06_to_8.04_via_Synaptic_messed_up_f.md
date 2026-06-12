---
title: "Upgrade from 6.06 to 8.04 via Synaptic messed up fonts"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by jobix on 2008-10-13
Hi,

I tried to upgrade from 6.06 to 8.04 an hour ago and it aborted after having spent about an hour downloading the packages. I assumed that it hadn't actually installed any of those packages. However,after a reboot, the fonts show up as little square boxes. Not all of them but stuff like the title on Firefox browser, X terminal, etc. Even my login and password were shown as those square boxes. Currently, all the System, Administration, Home, and other tabs are showing up as boxes. So, I have no way to get to anything else but a browser and an X-terminal. FWIW, I did the upgrade by clicking on the "upgrade to 8.04" button in Synaptic.

Any ideas on how to fix this aside from a clean install? 

Thanks.

---

### Post by cariboo on 2008-10-13
Boot up in recovery mode, and at the menu choose drop to a root prompt. at the prompt type:

```
sudo dhclient eth0
```

This will fet networking started, then at the prompt type:

```
sudo apt-get install -f
```

This should allow the installation to continue.

Jim

---

### Post by jobix on 2008-10-15
I tried to do that : sudo apt-get install -f
 
However it failed complaining about dependencies - xfonts-scalable.

So I tried to do an apt-get remove xfonts-scalable.
That failed complaining about dependencies - openoffice.
I tried removing openoffice.
That failed complaining about dependencies - ubuntu-desktop
I tried removing ubuntu-desktop.
That failed complaining about dependencies - xfonts-scalable :) 
Looks like a full circle.

Any ideas on how to proceed? I tried supplying the "-f" in the remove steps above, but it didn't help.

Thanks.

---

### Post by jobix on 2008-10-16
Somehow I got it to remove openoffice. I tried "sudo apt-get install -f" again and get this:

----------------------------------------
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xkb-data
The following NEW packages will be installed:
  xkb-data
0 upgraded, 1 newly installed, 0 to remove and 477 not upgraded.
196 not fully installed or removed.
Need to get 0B/340kB of archives.
After unpacking 4018kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ...
dpkg: serious warning: files list file for package `xfonts-scalable' missing, assuming package has no files currently installed.
126318 files and directories currently installed.)
Unpacking xkb-data (from .../xkb-data_1.1~cvs.20080104.1-1ubuntu6_all.deb) ...
dpkg: error processing /var/cache/apt/archives/xkb-data_1.1~cvs.20080104.1-1ubuntu6_all.deb (--unpack):
 trying to overwrite `/etc/X11/xkb/types.dir', which is also in package xkeyboard-config
Errors were encountered while processing:
 /var/cache/apt/archives/xkb-data_1.1~cvs.20080104.1-1ubuntu6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------

---

### Post by jobix on 2008-10-17
I got it working finally. I just removed a bunch of stuff that it would complain about and reinstall them. It took multiple iterations of this, but it is now working. I had some other issues with the screen resolution but I found stuff on these forums and on the Internet and that is now fixed. So, overall it only took me about 10 days to go from 6.06 to 8.04. :)

---

