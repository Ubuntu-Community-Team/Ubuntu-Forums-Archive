---
title: "Software updater error"
date: 2023-01-03
forum: Installation &amp; Upgrades
---

### Post by Pierre Dartigues on 2023-01-03
Hi there, I am trying to update Ubuntu 22.04 using the software updater. 
When I try to use the software-updater, it reports back: Failed to download repository information; check your internet connection.

However, internet works fine and uninterupted.

When I change the server from what to download updates it reloads the cache I end up seeing this:

I then tried updating by using the command "sudo apt update" which returns i.a.

```
Err:12 [https://ppa.launchpadcontent.net/ubuntuhandbook1/lives/ubuntu](https://ppa.launchpadcontent.net/ubuntuhandbook1/lives/ubuntu) jammy Release  404  Not Found [IP: 2620:2d:4000:1::3e 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/ubuntuhandbook1/lives/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
```

Then  I tried "sudo apt upgrade" which gives next return:
```
dpkg: error processing package urbackup-server (--configure):
 installed urbackup-server package post-installation script subprocess returned 
error exit status 1
Errors were encountered while processing:
 urbackup-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After all that I rebooted but that did nog cure the problem...

What shoud I do?

Greetings,
Pieter

---

### Post by QIII on 2023-01-03
You have added a PPA (Personal Package Archive) that does not have a package suitable for Jammy.  It appears that the last Ubuntu release for which the package has an install candidate is for Bionic -- about four years old.

I would suggest uninstalling that package, removing the PPA and then attempting to complete your update.

---

### Post by deadflowr on 2023-01-03
Yep.
Remove the PPA for ubuntuhandbook1/lives as there is no version for Ubuntu 22.04, jammy.
From a terminal you can run
```
sudo add-apt-repository --remove ppa:ubuntuhandbook1/lives
sudo apt update
```

---

### Post by QIII on 2023-01-03
Please do not remove edits made by the Forums Staff.

---

### Post by Pierre Dartigues on 2023-01-03
Yesss, it worked! Thanks a lot for your help deadflowr (And QIII as well)

Pieter

---

