---
title: "xkeyboard-config prevents upgrade"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by eastern_strider on 2005-11-19
To upgrade to breezy I do the following (after replacing 'hoary' with 'breezy' in sources.list):

sudo apt-get update
sudo apt-get dist-upgrade

It spits out the following error:
> x-window-system-core: Depends: xkeyboard-config but it is not installed
  xlibs: Depends: xkeyboard-config but it is not installed
E: Unmet dependencies. Try using -f.

Then I try:
sudo apt-get -f dist-upgrade

and this time I get:
> dpkg: error processing /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb (--unpack): trying to overwrite `/etc/X11/xkb/compat/basic', which is also in package xlibs
dpkg-deb: subprocess paste killed by signal (Broken pipe)

How can I fix this problem?
Thanks a lot.

---

### Post by rjwood on 2005-11-19
did you change your keeborad layout at some time? Maybe reconfigure your xserver and go with the automatic settings.
```
sudo dpkg-reconfigure xserver -xorg
```

---

### Post by eastern_strider on 2005-11-19
This simply had no effect. I'm still getting the same error.

I'm trying to install xkeyboard-config as:
sudo apt-get install xkeyboard-config

But getting the following message:
> Reading package lists... Done
Building dependency tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python2.3-mpz: Depends: libgmp3c2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then I try
sudo apt-get -f install

it says:
> Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgmp3c2 libgmpxx3 xkeyboard-config
The following packages will be REMOVED:
  libgmp3
The following NEW packages will be installed:
  libgmp3c2 libgmpxx3 xkeyboard-config
0 upgraded, 3 newly installed, 1 to remove and 485 not upgraded.
90 not fully installed or removed.
Need to get 0B/707kB of archives.
After unpacking 2523kB of additional disk space will be used.

But then gives the following error:
> Preconfiguring packages ...
(Reading database ... 106888 files and directories currently installed.)
Unpacking xkeyboard-config (from .../xkeyboard-config_0.6-5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb (--unpack):
 trying to overwrite `/etc/X11/xkb/compat/basic', which is also in package xlibs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Something looks seriously messed up with xkeyboard...

---

### Post by php on 2005-11-29
I have the same problem when trying to update my hoary to breezy. I have a modified swedish dvorak-layout put in the right place under /etc/X11/xkb.

In my case dpkg complains about trying to overwrite /etc/X11/xkb/rules/xorg.lst which it claims is in the xlib package too.

---

### Post by eastern_strider on 2005-12-04
I solved the problem by trying some of the tips given in the following website:
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)
and finished my upgrade by following:
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

As far as I understand, when apt-get starts having problems you need to help it by resolving dependencies manually.

The most helpful command was:
dpkg -r [package_name]

With this command you can forcefully remove "package_name" if it is causing a dependency problem.

Also one of my friends suggested using "aptitude" command instead of "apt-get". I think it has more power to resolve dependencies (may be more
risky at the same time).

Hope this helps.

---

