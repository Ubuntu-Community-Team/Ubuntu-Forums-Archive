---
title: "Can't upgrade to 18.10"
date: 2019-01-08
forum: Installation &amp; Upgrades
---

### Post by drymonitis on 2019-01-08
Hi,
I want to to upgrade from 18.04 to 18.10 but it doesn't work. Trying through the software updater, clicking on "Upgrade now..." nothing happens. Trying with the command line, following this [guideline]("http://https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-18-04-to-ubuntu-18-10") I do the following:
```

sudo apt-get update and sudo apt-get dist-upgrade

```
and the result is this:
```

The following package was automatically installed and is no longer required:
  gyp
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  libboost-filesystem-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
The after installing the update-manager-core and editing /etc/update-manager/release-upgrades, setting the prompt to normal, when typing:
```
do-release-upgrade
```
I get this:
```
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```

Any help appreciated.

---

### Post by Frogs Hair on 2019-01-08
what happened when you ran sudo apt get update again after the last message ?

---

### Post by drymonitis on 2019-01-09
> **Frogs Hair said:**
> what happened when you ran sudo apt get update again after the last message ?
This is what I get
```

Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
Hit:2 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu bionic InRelease     
Hit:3 http://gr.archive.ubuntu.com/ubuntu bionic InRelease                          
Get:4 http://gr.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]        
Get:5 http://gr.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]                
Fetched 247 kB in 1s (234 kB/s)   
Reading package lists... Done

```

---

### Post by Impavidus on 2019-01-09
You have to get all packages up to date before you can start the release upgrade. Your package libboost-filesystem-dev is not up to date. For some reason, it was kept back. So the question is why this package can't be upgraded.

What do you get from```
apt-cache policy libboost-filesystem-dev
sudo apt-get upgrade libboost-filesystem-dev
```

---

### Post by drymonitis on 2019-01-09
> **Impavidus said:**
> You have to get all packages up to date before you can start the release upgrade. Your package libboost-filesystem-dev is not up to date. For some reason, it was kept back. So the question is why this package can't be upgraded.

What do you get from```
apt-cache policy libboost-filesystem-dev
sudo apt-get upgrade libboost-filesystem-dev
```

That did it, thanks!

---

### Post by CatKiller on 2019-01-09
Don't forget that the non-LTS releases have quite a short support period, so you'll be on the upgrade treadmill till 2020.

---

### Post by drymonitis on 2019-12-11
Hi,
Coming back to this thread after some time cause I have the same problem again (can't upgrade from 19.04 to 19.10). Though, the solution provided by @impavidus didn't work this time (also, I don't know how he know it was the libboost-filesystem-dev package that was not up-to-date). Trying through the GUI doesn't do anything when clicking on upgrade, so thought I'd do it in the CLI.
Any help appreciated.

---

### Post by Frogs Hair on 2019-12-11
Post the output on any errors you received in the terminal as before.

---

### Post by drymonitis on 2019-12-11
Just figured it out. This time I had to run sudo apt-get upgrade to get  the information that the calf-plugins were kept back. Didn't notice it the first time, really sorry for the noise. Did a sudo apt-get upgrade calf-plugins and now the upgrade is running without problems.

---

### Post by CatKiller on 2019-12-11
> **drymonitis said:**
> (also, I don't know how he know it was the libboost-filesystem-dev package that was not up-to-date).

The output that you'd posted specifically said so. Even though package management seems like magic sometimes, it isn't; it's *just* an insanely connected set of scripts, file formats, and data structures on remote machines.

---

### Post by Impavidus on 2019-12-11
Yes, apt-get told us that that package was kept back. This means that a new version is available, but for some reason the package manager won't attempt to install that new version. Why, I can't say without more diagnostics.

Package management is complex, but highly modular. There's **apt**, which keeps track of what's available from the repositories, handles dependencies, downloads packages and calls **dpkg**, which in turn unpacks or removes the packages and runs installation or removal scripts provided by these packages, which in turn call other tools residing on your system. The user can also call these lower level tools directly. When something goes wrong, it's a matter of digging down to the root cause of the error and using the lower level tools (but still as high as possible) to fix it.

---

