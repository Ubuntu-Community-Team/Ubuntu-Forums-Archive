---
title: "Errors updating and upgrading 16.04 to 18.04"
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by freesitebuilder on 2020-02-05
I have a machine running 16.04 LTS which I have not used for about nine months. I realised I'd have a lot of updates to 16.04 before I could upgrade to 18.04, but my software updater simply goes to "waiting" when I choose the install button. Ubuntu Software doesn't load anything, just the throbber.

Using terminal I get "could not get lock /var/lib/dpkg/lock" and "Unable to lock admin directory /var/lib/dpkg is anything else using it?"

My update settings are to install important, recommended, and unsupported for Xenial, check daily, auto download and install security updates, and notify of LTS versions.

I've done some searches but I can't find a cure, TIA for advice.

---

### Post by CatKiller on 2020-02-05
> **freesitebuilder said:**
> 
Using terminal I get "could not get lock /var/lib/dpkg/lock" and "Unable to lock admin directory /var/lib/dpkg is anything else using it?"

Exactly as the message says, you can only have one updater fiddling with your packages at any one time. It seems you're trying to use three. Access is controlled by a simple file lock. 

Generally you'd only need to wait for a bit for the background updater to finish, but if it's got confused - a hang of some sort, or because someone keeps trying to run other package managers at the same time - it's pretty straightforward to kill the process of the background updater and then remove the lock.

---

### Post by freesitebuilder on 2020-02-06
I'm finding this even after a reboot, when no updating should be going on? Today I got another message - "Waiting for unattended -upgr to exit" immediately after a reboot, and loading the software updater. I'd be happy to do a clean install I think if I can't work out what's going on.

---

### Post by deadflowr on 2020-02-06
That's just automatic updates.
It's on by default now.
It starts at login, or whenever networking comes up.
The default is only for security updates.

You can easily turn if off by either switching the updates in Software and Updates > Updates > Automatically check for updates > Never.
or
Edit the file (or files) /etc/apt/apt.conf.d/10periodic and/or /etc/apt/apt.conf.d/20auto-upgrades and set all to zero (0)
From this
```
APT::Periodic::Update-Package-Lists "**1**";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "**1**";
```
to this
```
APT::Periodic::Update-Package-Lists "**0**";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "**0**";
```

Or you can nuclear and just simply remove unattended-upgrades package.

---

### Post by CelticWarrior on 2020-02-06
The above is fine but it wouldn't be my first choice.

My first choice would be letting the system do its thing, i.e., just boot and wait (up to 30 minutes if it must) for the unattended updates to finish and/or seeing the updates tool popup in the dash, click on it and finally install all the proposed updates. Then I would run 'sudo apt full-upgrade' to assure everything that can be updated will be.

---

### Post by freesitebuilder on 2020-02-08
Thanks to all, changing the code cured the problem and I'm now fully updated and upgraded. I did leave it for a while to see if the system would finish, but it seemed to be doing nothing.

---

