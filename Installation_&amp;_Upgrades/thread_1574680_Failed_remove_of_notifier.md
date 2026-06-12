---
title: "Failed remove of notifier"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by CorruptDNA on 2010-09-14
Hi guys,

I am currently having problems with my ubuntu system and would like help of any kind. thanks.
So i am experiencing a broken package.. i tried to fix it and remove it (the package is update-notifier) but could not.

here is what i tried to do

> 
root@umair-desktop:/home/umair# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  ubuntu-desktop update-notifier
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 373kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 23216 package `update-notifier':
 `Depends' field, reference to `libice6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)



I would like to know if there is any way of forcible removing the program.. i cannot downgrade libice6 because it is affecting almost all the programs installed. So i dropped that option.
Please, any help would be great, i do not want to change to windows and i might have to if i do not get this right. (because of this i cannot install or remove any kind of program.)

---

### Post by plucky on 2010-09-16
> I would like to know if there is any way of forcible removing the program.. i cannot downgrade libice6 because it is affecting almost all the programs installed. So i dropped that option.
Please, any help would be great, i do not want to change to windows and i might have to if i do not get this right. (because of this i cannot install or remove any kind of program.) 

Be very careful using this method,this might break your system.

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```

This makes a backup copy just in case you mess up.

```
gksudo gedit /var/lib/dpkg/status
``` then go to  **Search > Go to Line** and input **23216** and you should find ```
Package: update-notifier
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 312
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: i386
Version: 0.99.3
Depends: libc6 (>= 2.7), libdbus-glib-1-2 (>= 0.78), libgconf2-4 (>= 2.27.0), libgdu0 (>= 0.2), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.0), libgudev-1.0-0 (>= 147), libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libx11-6 (>= 0), gconf2 (>= 2.10.1-2), update-notifier-common (= 0.99.3), python, update-manager, notification-daemon, gksu
Recommends: apport-gtk
Suggests: ubuntu-system-service
Conffiles:
 /etc/xdg/autostart/update-notifier.desktop e175f85780befc1ff9a1cc7862540ccd
Description: Daemon which notifies about package updates
 Puts an icon in the user's notification area when package updates are
 available.
```

If you find the update-notifier package you can delete the status information and dpkg should start to work.If anything goes wrong you can copy back the status.backup file to status and you should be back to where you were before.

Good luck

---

### Post by CorruptDNA on 2010-10-09
Reading package lists... Error!
E: Malformed Status line
E: Error occurred while processing update-notifier (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
umair@umair-desktop:~$ sudo apt-get remove wine
Reading package lists... Error!
E: Malformed Status line
E: Error occurred while processing update-notifier (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


lol.. what should i do now? i fixed it back and now im back to the original problem, any suggestions?

---

### Post by CorruptDNA on 2010-10-09
i took out the 6 and added > to the   =1:1.1.1 
and i fixed it.. thanks for your help,,

---

