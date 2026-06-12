---
title: "PPA not updated in Lucid Lynx sources.list"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Scifer on 2010-08-20
I'm trying to add PPAs in my Kubuntu Lucid Lynx installation.
```
$ sudo add-apt-repository ppa:kubuntu-ppa/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv E4DFEC907DEDA4B8A670E8042836CB0A8AC93F7A
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```
But when I look in my sources.list, the PPA repository is not there. Nevertheless I SUSPECT I'm receiving it's updates.

Questions:

[LIST=1]
[*]Is there a file that PPAs are being written to other than sources.list?
[*]Should I manually update sources.list in order to add this PPAs?
[*]Where this updates are coming from?
[/LIST]

---

### Post by snowpine on 2010-08-20
There is a folder called /etc/apt/sources.list.d/ where additional sources can be stored.

Check in there for your PPA.

---

### Post by Scifer on 2010-08-20
> **snowpine said:**
> There is a folder called /etc/apt/sources.list.d/ where additional sources can be stored.

Check in there for your PPA.
That's it. All PPA repositories are being added to individual files in this folder.
Thanks a lot :D

---

### Post by Scifer on 2010-08-20
By the way. Is It convenient to remove this PPAs manually and leave its keys untouched? Should I remove the keys manually too? How to do this?
Is there some script like remove-apt-repository?

---

### Post by ankspo71 on 2010-08-21
Hi,
Leaving the keys in won't harm your system. If you would like to remove them though, I think they can be removed by looking for a something tab named "authentication" (or something similar) in your software sources manager.

If you would like to prevent future updates you can easily disable the repository in your software sources manager instead of deleting them. I'm using Linux Mint KDE at the moment which doesn't have kpackagekit installed, but in the settings of kpackagekit would be the place to look in Kubuntu.

---

### Post by Mazehero55 on 2010-12-18
Any way I can add a ppa to these manually? I have jolicloud 1.1 so ppa should work but it's not letting me add ppa's the usual way. Could someone post an example of what one of these ppa list files look like so I can make my own?

thanks:P

---

### Post by wojox on 2010-12-18
What ppa's you trying to install?

---

### Post by abumaia on 2010-12-18
Is there a way to consolidate all the PPAs in sources.list.d into one file that's easier to backup?

---

