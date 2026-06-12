---
title: "Error BrokenCount &gt; 0"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Robert_Barrow on 2014-05-28
Hi, 

first post!

I have encountered a weirdness with the package system that I can't seem to find the root cause of.

I am getting an error message stating 'BrokenCount >0', the software centre refuses to install anything saying that I have a 'Broken Cache'. 

The strange bit is that nothing show as being broken either through apt or synaptic. They both update and and install packages without any complaints. I'm guessing that there is just a flag somewhere that needs to be reset to allow the Ubuntu software to run properly. But I can't find it anywhere.

Any help would be appreciated, it's more annoying than anything else.

---

### Post by slickymaster on 2014-05-28
Hi Robert_Barrow, welcome to the forums.
Can you please post back the output you get when running these commands at a terminal window (one at a time please)```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by Robert_Barrow on 2014-05-28
Thanks for the swift reply!

```

Ign http://gb.archive.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty-updates InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://dl.google.com stable InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://repo.steampowered.com precise InRelease
Ign http://gb.archive.ubuntu.com trusty-backports InRelease
Ign http://ppa.launchpad.net trusty InRelease
Hit http://extras.ubuntu.com trusty Release
Hit http://repo.steampowered.com precise/steam Sources
Hit http://dl.google.com stable Release.gpg
Hit http://gb.archive.ubuntu.com trusty Release.gpg
Ign http://ppa.launchpad.net trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://extras.ubuntu.com trusty/main Sources
Get:1 http://gb.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Ign http://ppa.launchpad.net saucy InRelease
Hit http://dl.google.com stable Release
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://repo.steampowered.com precise/steam amd64 Packages
Get:2 http://gb.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Ign http://ppa.launchpad.net trusty InRelease
Get:3 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://extras.ubuntu.com trusty/main i386 Packages
Hit http://dl.google.com stable/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty Release
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://repo.steampowered.com precise/steam i386 Packages
Get:4 http://gb.archive.ubuntu.com trusty-updates Release [58.5 kB]
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://dl.google.com stable/main i386 Packages
Ign http://linux.dropbox.com trusty InRelease
Get:5 http://security.ubuntu.com trusty-security Release [58.5 kB]
Hit http://ppa.launchpad.net trusty Release.gpg
Ign https://private-ppa.launchpad.net trusty InRelease
Hit http://ppa.launchpad.net trusty Release.gpg
Get:6 http://linux.dropbox.com trusty Release.gpg [489 B]
Hit https://private-ppa.launchpad.net trusty Release.gpg
Get:7 http://gb.archive.ubuntu.com trusty-backports Release [58.6 kB]
Hit http://ppa.launchpad.net saucy Release.gpg
Hit https://private-ppa.launchpad.net trusty Release
Hit http://ppa.launchpad.net trusty Release.gpg
Get:8 http://linux.dropbox.com trusty Release [2,601 B]
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/main Sources
Hit http://ppa.launchpad.net trusty Release
Get:9 http://security.ubuntu.com trusty-security/main Sources [16.0 kB]
Hit http://gb.archive.ubuntu.com trusty/restricted Sources
Hit http://ppa.launchpad.net trusty Release
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Get:10 http://linux.dropbox.com trusty/main amd64 Packages [1,143 B]
Hit http://gb.archive.ubuntu.com trusty/universe Sources
Hit http://ppa.launchpad.net trusty Release
Ign http://extras.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources
Hit http://ppa.launchpad.net trusty Release
Ign http://extras.ubuntu.com trusty/main Translation-en
Get:11 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages
Hit http://ppa.launchpad.net saucy Release
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://ppa.launchpad.net trusty Release
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages
Get:12 http://linux.dropbox.com trusty/main i386 Packages [1,143 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Ign http://dl.google.com stable/main Translation-en_GB
Get:13 http://security.ubuntu.com trusty-security/universe Sources [4,212 B]
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages
Ign http://dl.google.com stable/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:14 http://security.ubuntu.com trusty-security/multiverse Sources [687 B]
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages
Get:15 http://security.ubuntu.com trusty-security/main amd64 Packages [51.8 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB
Get:16 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [17.9 kB]
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:18 http://gb.archive.ubuntu.com trusty-updates/main Sources [45.7 kB]
Get:19 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:20 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [14 B]
Get:21 http://security.ubuntu.com trusty-security/main i386 Packages [49.4 kB]
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Get:22 http://gb.archive.ubuntu.com trusty-updates/universe Sources [28.2 kB]
Hit http://ppa.launchpad.net saucy/main i386 Packages
Get:23 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [2,234 B]
Get:24 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [109 kB]
Get:25 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:26 http://security.ubuntu.com trusty-security/universe i386 Packages [17.9 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Get:27 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,404 B]
Get:29 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [74.9 kB]
Ign http://linux.dropbox.com trusty/main Translation-en_GB
Get:30 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,089 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Ign http://linux.dropbox.com trusty/main Translation-en
Get:31 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [107 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Get:32 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:33 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [75.3 kB]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en
Get:34 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,273 B]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Get:35 http://gb.archive.ubuntu.com trusty-backports/main Sources [14 B]
Get:36 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Get:37 http://gb.archive.ubuntu.com trusty-backports/universe Sources [4,123 B]
Get:38 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [768 B]
Get:39 http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Get:40 http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:41 http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages [4,099 B]
Get:42 http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [619 B]
Get:43 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [14 B]
Get:44 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:45 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [4,114 B]
Get:46 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [619 B]
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://security.ubuntu.com trusty-security/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com trusty-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB
Fetched 816 kB in 8s (97.2 kB/s)
Reading package lists... Done

```

No errors there.

---

### Post by Robert_Barrow on 2014-05-28
```

Reading package lists...
Building dependency tree...
Reading state information...
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by Robert_Barrow on 2014-05-28
And dpkg returns nothing!
 
```

amadeus@Solid-Snake:~/Downloads$ sudo dpkg --configure -a
amadeus@Solid-Snake:~/Downloads$ 

```

---

### Post by slickymaster on 2014-05-28
Apparently there are no problems with the package manager.

I'm assuming that you get that error message when you open the Software Center, and that the error message shows up in a dialog box. If that's correct does it provides any button labeled 'Repair'? If yes, have you tried to click it?

---

### Post by Robert_Barrow on 2014-05-28
I tried the repair option but it just repeats itself. I also get the warning icon on the top bar. That tells me that the Broken Count > 0. But there is obviously nothing wrong with the package system itself, that's why I thought it might just be a flag somewhere that's got stuck. I had a few mishaps installing Apache with PHP-FPM the other day and I wonder if that has left some residual error flag somewhere.

---

### Post by slickymaster on 2014-05-28
I can't be sure of what might be the culprit. It could perfectly also be third party repositories. You could try to disable them, since they are a common source of problems, and check if the issue persists.

Also, you could have a read at [this thread]("http://askubuntu.com/questions/223143/broken-package-after-update-linux-headers-error-brokencount-0"), and see if any of the suggested workarounds can be useful for your case.

---

