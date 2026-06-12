---
title: "How can I upgrade my software channel?"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by slsolaris on 2008-06-13
It is that when I try to download i new software by "add/remove" in application menu it always download an old version of the program, my question is Howa can i update my source list or my software channel in order to download the last versions of the softwares in a "SAFE MODE", thanx!

---

### Post by Pumalite on 2008-06-13
System>Administration>Software Soureces>Open ALL your repos, including: partner, backporst, proposed, etc. Excepted src unless you have a specific need for them. Then:
sudo apt-get update
sudo apt-get dist-upgrade.

---

### Post by pedro_orange on 2008-06-13
> **Pumalite said:**
> 
sudo apt-get dist-upgrade.

Updates the distro/OS, not the software you're running?

```
sudo apt-get clean
sudo apt-get update
```

Will update your apt cache depending on the info in /etc/apt/sources.list

Once you've done that your update manager will check to see if there are any more up to date versions of your software in the repos.

You can GUI your sources.list from Software Sources in Administration.

---

### Post by mikewhatever on 2008-06-13
> **slsolaris said:**
> It is that when I try to download i new software by "add/remove" in application menu it always download an old version of the program, my question is Howa can i update my source list or my software channel in order to download the last versions of the softwares in a "SAFE MODE", thanx!

A lot of software in (Add/Remove) repositories is not the latest version, and it does not matter whether your are in safe or regular GUI mode. It is especially noticeable with older releases such as Dapper Drake. Because of the way repositories work in Ubuntu, you can not upgrade most of the software to a later version without upgrading the system. A work around would be to check Back Port repository or sites like getdeb.net.

---

### Post by slsolaris on 2008-06-14
thax u all, i did what you told me about apt-get update an upgrade, but it didnt wok because when i download a program for example transmission, it download an old version "1.06" to be exactly, and i went to the official page and it goes to "1.21", please help me, it is more defecult to me to go to the page and download the source code and install it from it. how can i change my port repository?
-second point could be: how can i convert a source code to .deb file.
thanx a lot again!

---

