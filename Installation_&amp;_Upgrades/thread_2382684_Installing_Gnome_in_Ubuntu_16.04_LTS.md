---
title: "Installing Gnome in Ubuntu 16.04 LTS"
date: 2018-01-16
forum: Installation &amp; Upgrades
---

### Post by opale7001 on 2018-01-16
Hello Linux fans

I am wondering if I did not install the proper linux distro. I simply wish to have the GNOME desktop however when I try to install via terminal i get

```

sudo add-apt-repository ppa:gnome3-team/gnome3-staging
[sudo] password for opale7000: 
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
This PPA is no longer updated for releases older than Ubuntu 17.04. If you are using an older release, please ppa-purge this PPA and consider upgrading to a newer Ubuntu release.
Unless otherwise posted, updates will only be provided in this PPA for 7 months from the original release of the associated Ubuntu series.
https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html
 More info: https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging
Press [ENTER] to continue or ctrl-c to cancel adding it
^CTraceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 143, in <module>
    sys.stdin.readline()
KeyboardInterrupt




```

---

### Post by TheFu on 2018-01-16
"staging" isn't stable.  If you aren't a gnome3 developer, you probably don't want this.

---

### Post by opale7001 on 2018-01-16
I think I got the proper command

sudo apt-get install ubuntu-gnome-desktop

---

### Post by opale7001 on 2018-01-16
I think I got the proper command

sudo apt-get install ubuntu-gnome-desktop

[https://paste.ubuntu.com/26398211/](https://paste.ubuntu.com/26398211/)

---

