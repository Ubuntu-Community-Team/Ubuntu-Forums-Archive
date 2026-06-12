---
title: "apt-get upgrade fails immedietely"
date: 2015-03-19
forum: Installation &amp; Upgrades
---

### Post by Only1KW on 2015-03-19
A few weeks ago, I got a bad update from Ubuntu which caused apt to crash half way through the upgrade.  Since then, whenever I try to run "sudo apt-get upgrade", I get the following output:

```
user@host:~$ sudo apt-get upgrade
[sudo] password for user: 
Reading package lists... Done
user@host:~$ y tree... 0%

```

I recently rebooted hoping that would fix the issue, but it didn't.  Any ideas what I can do to correct this?  Any logs I can look at to determine why it keeps crashing?

---

### Post by dino99 on 2015-03-19
i suppose you first update, then upgrade (not only upgrade)

you still can run:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade

if the issue persist, then deactivate 'proposed' archive & third party archive(s) (ppa); and update again then upgrade

---

### Post by grahammechanical on 2015-03-19
It is said that we should always run

```
sudo apt-get update
```

before running apt-get upgrade

[http://www.computerhope.com/unix/apt-get.htm](http://www.computerhope.com/unix/apt-get.htm)

You show being asked for the password. That makes me think that you have not run apt-get update, which would have required password authorisation. What happens when you use Update Manager to update?

If the updating/upgrading process was interrupted then it is mostly likely that we will have broken packages. We can try 

```
sudo apt-get install -f
```

or to fix the package system

```
sudo dpkg --configure -a
```

Regards.

---

### Post by Only1KW on 2015-03-19
An update followed by an upgrade fixed the issue. Thanks all!  

I wasn't aware that an update was always required before an upgrade.  Per the [official documentation]("https://help.ubuntu.com/community/AptGet/Howto"):

> [LEFT]apt-get update

[FONT=inherit]Run this command after changing [FONT=inherit]/etc/apt/sources.list[/FONT] or [FONT=inherit]/etc/apt/preferences[/FONT] . For information regarding [FONT=inherit]/etc/apt/preferences[/FONT], see [PinningHowto]("https://help.ubuntu.com/community/PinningHowto"). Run this command periodically to make sure your source list is up-to-date. This is the equivalent of "Reload" in Synaptic or "Fetch updates" in Adept.[/FONT]
[/LEFT]


---

### Post by deadflowr on 2015-03-19
Package versions can be in constant flux.
Going from version 1234, to 1235 when ever a update, fix comes through. Usually this new version can overwrite/replace the old version.
 
When you run apt-get update, it finds the name of the new version. And your system's package database reflects that the new package version name. 
If you don't run apt-get update, then the system looks for the old, now non-existent, package.

Ubuntu resolved this problem by forcing the software updater(update manager) to run an apt-get update every time it starts.
I suppose the Software Center is suppose to do the same, but I've never paid attention.
So from a gui point of view this should be a non-issue.

---

### Post by Only1KW on 2015-03-19
The GUI insists on doing a dist-upgrade instead of just an upgrade, and doesn't differentiate between packages that are only part of the dist-upgrade.  I switched to command line upgrades awhile ago as I didn't want to be forced to reboot whenever an update occurred and found that my system often became unstable if I applied the dist-upgrade packages without rebooting.

---

