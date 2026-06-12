---
title: "Update Manager Problem"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by hambidextrous on 2010-01-05
Update Manager is working properly.  When I check for updates I receive the following message titled: 

Could not download all repository indexes

The message was the following:

Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.


How do I fix this?

---

### Post by drs305 on 2010-01-05
Either post your /etc/apt/sources.list or take a look at it yourself.

All lines in sources.list should start with either "deb" or "#". If it starts with anything else, it is going to create an error. 

For self-help, look for the line referecing google above and place a # symbol in front to make sources.list disregard the line.

To view and edit:
```
gksu gedit /etc/apt/sources.list
```

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by hambidextrous on 2010-01-05
I don't see any reference to the google line in the source.list.

Here is the source list:
```
[B]deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
[/B]
```

I believe this started shortly after installing google chrome.  To stop the error from appearing I unchecked the google line ([http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main) in the third-party software tab in the software sources.  It prevented the error but I don't think any updates were being installed so I re-checked it and got the update manager error again.

---

### Post by drs305 on 2010-01-05
Take a look in /etc/apt/sources.list.d/  There will probably be a specific file in there for google if it's not listed in the sources.list file.

The other way would be to open Settings in Synaptic or Update Manager and take a look for google in the Third Party/Other software tab of Repositories. You could just untick it there. If you want the repository, revisit the site and refer to the instructions for adding the repository.

---

### Post by snowpine on 2010-01-06
Does Google have a version of Chrome available for the lpia architecture? That's my guess of the problem. You might need to repackage the i386 for lpia, [see here]("http://ubuntuforums.org/showthread.php?t=962835").

---

### Post by hambidextrous on 2010-01-06
That sounds like the problem I have.  Chrome is installed and runs, but does not show up in the synaptic package manager and I don't know how to uninstall Chrome.  I hope that if I can remove it the update manager will start working properly again.

Any thoughts on what I should do to remove Chrome?

---

### Post by snowpine on 2010-01-06
This is the answer:

> **hambidextrous said:**
> To stop the error from appearing I unchecked the google line ([http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main) in the third-party software tab in the software sources.  

---

### Post by hambidextrous on 2010-01-06
After I do that the update manager runs like everything is ok, but never installs anything.  The same number packages to be installed displays everytime I run the update manager, then it just says last updated an hour ago.  I check again, same thing.

Chrome still works even with the google line in the third party tab unchecked.  I would like to see if I can get rid of all the chrome files and see if that fixes it, but I don't know how to uninstall it.

---

### Post by snowpine on 2010-01-06
You can try upgrading from the command line, and posting the output here.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hambidextrous on 2010-01-06
Here is what I get;
```
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Hit http://wine.budgetdedicated.com hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Hit http://wine.budgetdedicated.com hardy Release
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://wine.budgetdedicated.com hardy/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/public Translation-en_US
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/public Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/public Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by snowpine on 2010-01-06
Everything looks fine to me. Your system is up to date. :)

---

### Post by drs305 on 2010-01-06
> **hambidextrous said:**
> Chrome still works even with the google line in the third party tab unchecked.  I would like to see if I can get rid of all the chrome files and see if that fixes it, but I don't know how to uninstall it.

Disabling a repository doesn't disable an app. The repositories are used as a place to store packages and their updates. Once you have a package on your machine, removing the repository merely stops your system from looking for any file updates or new versions found in that particular repository. Your app is "frozen" in time and won't be updated because the system won't be looking for a list of improvements to it.

---

