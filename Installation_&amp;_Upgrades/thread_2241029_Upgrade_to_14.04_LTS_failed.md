---
title: "Upgrade to 14.04 LTS failed"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by Reddoug on 2014-08-23
Hi

I upgraded 12.04 LTS to 14.04 LTS, I can log in but then I get an error message  "System program problem detected  Do you want to report the problem now?" I select report the problem, then it goes to my desktop, it says Ubuntu 14.04 at the bottom and nothing else. No application, icons, clock, shutdown, all missing. Have to hold down power button to turn off computer. Computer is HP Pavalion dv7-1260us, AMD processor Turion X2 DualCore 2.20GHZ with 4GB of ram. Computer is dual booted with Windows 7 Professional and now Windows seems slow to load also. I have restarted the computer several times hoping it might repair itself but no luck. Any ideas what I can do? I do not have any idea where to start short of downloading new IOS and re-install from scratch. 

Thanks, Doug

---

### Post by Reddoug on 2014-08-23
Forgot to state I upgraded from update package manager when I did the upgrade.

Thanks, Doug

---

### Post by kansasnoob on 2014-08-23
Sounds like it could be a graphics driver problem. Do you know how to boot using the nomodeset parameter?

I'm too cooked mentally to help right now but please be patient and someone will help you. If you should need to reinstall you must beware this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by grahammechanical on 2014-08-23
The login screen has the words Ubuntu 14.04 at the bottom left but not the desktop after we login. I am not certain that the login succeeded. If you are at a desktop can you right click and select Change Desktop Background? That will get you to System Settings and from there to Software and Updates and the Additional Drivers tab will let us change video drivers.

to open a terminal we can do Ctrl+Alt+T. If that does not work we can open a Linux command line interface with Ctrl+Alt+F2 and switch back to the desktop with Ctrl+Alt+F7. 

to shut down

```
sudo shutdown -h now
```

to reboot

```
sudo shutdown -r now
```

to reset Compiz

```
dconf reset -f /org/compiz/
```

to restart Unity

```
setsid unity
```

Regards, the F6 option including nomodeset, See section 6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by Reddoug on 2014-08-23
I have a desktop, back ground looks the same as it did before upgrade, just no icons or anything else. 
I ran  dconf reset -f /org/compiz/  and received    error: Cannot autolaunch D-Bus without X11 $DISPLAY
                                                                   Usage:
                                                                        dconf reset {-f} PATH
                                                                   Reset a key or dir.  -f is required for dirs.     

Then I ran setsid untiy and received several screens of compiz (core) -Error: Plugin init failed:ezoom  and a lot of others 
                                                                           compiz (core) - Error: init failed : unityshell

Thanks for the help, Doug

---

### Post by Reddoug on 2014-08-23
When I restarted my computer, when I was at log in screen I did have the clock and shutdown at top right of screen, after I entered my password and logged in, they went away. I tried moving the cursor all around to try and get them to drop down but nothing happened. Had to open terminal to shut down.

Thanks again, Doug

---

### Post by Reddoug on 2014-08-30
Hi
From command line

I ran grub-install -v came back with grub-install: info: ... not found. Looking for /proc/device-tree ...  grub-install: info: ... not found. Then I tried grub -install -v and received  The program 'grub' is currently not installed.
The link above about bugs looked to me more like when installing from cdrom, this was an upgrade. 

Thanks, Doug

---

### Post by Reddoug on 2014-09-15
Hi

Last thing I tried was to create a live cd and run from cd. 14.04LTS runs with no problems that away. I would think that would mean my hardware is compatible with 14.04LTS. I know doing a fresh install would be easier, what fun is that? I might learn something along the way.

Any other ideas?

Thanks, Doug

---

