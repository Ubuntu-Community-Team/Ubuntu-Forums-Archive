---
title: "Trying to upgrade my gnome to use extensions."
date: 2018-02-27
forum: Installation &amp; Upgrades
---

### Post by Silhorn on 2018-02-27
Hi,

I am using Ubuntu 17.10 standard flavour.
I am using the gnome extension website: extensions.gnome.org. Some extensions work and some don't. I figured because my gnome version 3.26.2 is lower than the required for most extensions. I am trying to update gnome to latest version from instructions I found on this page:
[URL="https://wiki.ubuntu.com/UbuntuGNOME/HowTo/UpgradeGnomeShell"]https://wiki.ubuntu.com/UbuntuGNOME/HowTo/UpgradeGnomeShell
[/URL]I do everything but it is still version 3.26.2
I see an error message near the bottom about artful not having a release file. I think that could be why it is not updating properly? How can I fix?

```
tvbox@tvbox:~$ gnome-shell --versionGNOME Shell 3.26.2
tvbox@tvbox:~$ sudo add-apt-repository ppa:gnome3-team/gnome3
[sudo] password for tvbox: 
 Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 16.04 to 16.10), you should run 'ppa-purge ppa:gnome3-team/gnome3' first.


*** You need to run 'sudo apt-get dist-upgrade' to avoid problems. ***
Please read the output before entering 'Y' to make sure important packages won't be removed.


=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA


=== End of Life ===
This PPA is no longer updated for releases older than Ubuntu 17.04. If you are using an older release, please ppa-purge this PPA and consider upgrading to a newer Ubuntu release.
Unless otherwise posted, updates will only be provided in this PPA for 7 months from the original release of the associated Ubuntu series.
https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html
 More info: https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3
Press [ENTER] to continue or Ctrl-c to cancel adding it.


gpg: keybox '/tmp/tmpqc8ej4yn/pubring.gpg' created
gpg: /tmp/tmpqc8ej4yn/trustdb.gpg: trustdb created
gpg: key F1773AF13B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
OK
tvbox@tvbox:~$ sudo add-apt-repository ppa:gnome3-team/gnome3-staging


 This PPA will be used to test uploads before they are uploaded to the main archive for the coming Release.


=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!


If they break your system, you get to keep both halves.


=== Installing ===
To use this PPA, you should enable the main GNOME3 PPA.


- You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.


=== Removing ===
Use ppa-purge to remove this PPA. It is *particularly* important to do this before upgrading to a new release!


ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3


=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA


=== End of Life ===
This PPA is no longer updated for releases older than Ubuntu 17.10. If you are using an older release, please ppa-purge this PPA and consider upgrading to a newer Ubuntu release.
Unless otherwise posted, updates will only be provided in this PPA for 7 months from the original release of the associated Ubuntu series.
https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html
 More info: https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging
Press [ENTER] to continue or Ctrl-c to cancel adding it.


gpg: keybox '/tmp/tmp_zot22el/pubring.gpg' created
gpg: /tmp/tmp_zot22el/trustdb.gpg: trustdb created
gpg: key F1773AF13B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
OK
tvbox@tvbox:~$ 
tvbox@tvbox:~$ sudo apt-get update
Hit:1 http://repo.steampowered.com/steam precise InRelease
Hit:2 http://au.archive.ubuntu.com/ubuntu artful InRelease                     
Get:3 http://au.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]   
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Err:5 http://au.archive.ubuntu.com/ubuntu artful-backports InRelease           
  403  Forbidden [IP: 202.158.214.106 80]
Hit:6 http://linux.teamviewer.com/deb stable InRelease                         
Hit:7 http://linux.teamviewer.com/deb preview InRelease                        
Get:8 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]    
Hit:9 http://ppa.launchpad.net/fixnix/netspeed/ubuntu artful InRelease         
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                    
Ign:11 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu artful InRelease     
Hit:13 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu artful InRelease
Hit:14 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu artful InRelease   
Err:15 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu artful Release       
  404  Not Found
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tvbox@tvbox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.



```

---

### Post by kerry_s on 2018-02-27
the extensions are in ubuntu software-> add-ons->extensions
there's no need to use the browser

hmm, funny thing is in ubuntu 18 the extension section is missing.
nevermind it just showed.
[ATTACH=CONFIG]278707[/ATTACH]

---

### Post by deadflowr on 2018-02-28
> I figured because my gnome version 3.26.2 is lower than the required for most extension
Far more likely the opposite.
You're using a version too new for most extensions.
Not all extension developers keep them going, so quite a few have probably lapsed their ability to run on new versions of gnome.

---

### Post by Silhorn on 2018-02-28
Didn't know could add and manage extensions from ubuntu software I use that from now on. Thanks.

The reason why I thought my gnome version was too low is if you have a look at the page for this extension:
[https://extensions.gnome.org/extension/336/hardware-sensors-indicator/](https://extensions.gnome.org/extension/336/hardware-sensors-indicator/)
I have installed it from ubuntu software app but it does not show up on the top panel tray at all.

If you have a look at the shell version list you can see all version numbers are higher than 3.26.2

And on comments section you can see someone saying it does not work on his linux and a replying saying he needs to update to gnome 3.8?

---

### Post by deadflowr on 2018-02-28
> **Silhorn said:**
> Didn't know could add and manage extensions from ubuntu software I use that from now on. Thanks.

The reason why I thought my gnome version was too low is if you have a look at the page for this extension:
[https://extensions.gnome.org/extension/336/hardware-sensors-indicator/](https://extensions.gnome.org/extension/336/hardware-sensors-indicator/)
I have installed it from ubuntu software app but it does not show up on the top panel at all.

If you have a look at the shell version list you can see all version numbers are higher than 3.26.2

And on comments section you can see someone saying it does not work on his linux and a replying saying he needs to update to gnome 3.8?

As I posted, your version is too new.
the extension you linked only goes to gnome 3.8.
3.8 is older than 3.26.
It's not like 3.80, but more like 3.08

---

### Post by kerry_s on 2018-02-28
make sure your using gnome xorg, wayland breaks a lot of apps.

those extensions are trial & error, the popular 1's seem to work, like dash to dock, dash to panel, drop down terminal(i use), etc...

the 1's that are suppose to show in the top panel can't be trusted at all, you'll get stuck in a crash loop. i had to boot into live, go into .config/autostart and delete the extension just to get back to the desktop.

---

### Post by Silhorn on 2018-02-28
Yeah. I was thinking 3.8 would be 3.80...
That explains it then. Very misleading they write it like that.

Now gnome xorg, is that something I have to install or I already have but don't know how to switch to?

---

### Post by Silhorn on 2018-02-28
Nevermind found it. 
Thanks everyone for help.

---

