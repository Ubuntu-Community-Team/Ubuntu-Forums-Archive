---
title: "Gutsy --&gt; Hardy upgrade failure with Adept Updater--please help!"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by caljohnsmith on 2008-06-08
After spending a day or so letting Adept Updater download all the files necessary to upgrade to Hardy, it got about 70% the way through the installation part but then Adept returned the following error: 
```

There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages
```
At that point I was forced to quit Adept Updater, I then rebooted, and as I dreaded I couldn't even boot into Kubuntu anymore. Booting into the new kernel caused a "kernel panic", and when I tried to boot into an older kernel, it got further but it eventually froze.

But at least I could boot into recovery mode using an old kernel, so I ran the following:
```
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
(went through the whole reconfiguration, then did:)
sudo dpkg --configure --pending
```
Still Kubuntu would crash when I tried to boot into it. I should mention that I still have about 200 MB worth of packages in /var/cache/apt/archives. I also ran the following:
```
sudo apt-get update
sudo apt-get upgrade
```
And that didn't help because Kubuntu didn't think there was anything I needed to upgrade.

In my /var/log/dist-upgrade/apt.log file there was alot of these types of messages:
```
Package restricted-manager has broken dep on restricted-manager-core
  Considering restricted-manager-core 3 as a solution to restricted-manager -1
  Removing restricted-manager rather than change restricted-manager-core
Investigating libgnome-perl
Package libgnome-perl has broken dep on libgtk-perl
  Considering libgtk-perl 2 as a solution to libgnome-perl -1
  Removing libgnome-perl rather than change libgtk-perl
Investigating libgnomekbdui1
Package libgnomekbdui1 has broken dep on libgnomekbd1
  Considering libgnomekbd1 1 as a solution to libgnomekbdui1 -1
  Removing libgnomekbdui1 rather than change libgnomekbd1
Investigating restricted-manager-kde
Package restricted-manager-kde has broken dep on restricted-manager-core
  Considering restricted-manager-core 3 as a solution to restricted-manager-kde -1
  Removing restricted-manager-kde rather than change restricted-manager-core
```
I'm not sure if that is unusual or not. 

Any ideas of what I can do? I really don't want to fresh install 8.04 because I would lose alot, considering how highly customized my system is at this point. Thanks for any help!

---

### Post by zvacet on 2008-06-09
```
sudo apt-get -f install
```

---

### Post by caljohnsmith on 2008-06-09
> **zvacet said:**
> ```
sudo apt-get -f install
```
Thanks, I forgot to mention I tried that too. Unfortunately it didn't solve the problem either. Any other ideas?

---

### Post by zvacet on 2008-06-09
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by caljohnsmith on 2008-06-09
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get dist-upgrade
```
Unfortunately, same thing again--after apt-get went through fetching all the update info, I did the "sudo apt-get dist-upgrade" and it claimed I had no upgrades and nothing to update. Any more ideas? :confused: Thanks for any help.

---

