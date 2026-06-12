---
title: "Computer offline: installing updates from USB-stick ?"
date: 2022-12-06
forum: Installation &amp; Upgrades
---

### Post by vincentm77 on 2022-12-06
Hi everyone,

I have a computer (ubuntu 22.04) in a room with no internet access.
Still, I would like to be able to install updates/upgrades from time to time...

Ideally I would copy files from a repository to an USB-stick when I have access to another computer (with internet access), then plug the USB-Stick to my ubuntu computer and install the updates/upgrades from the USB-stick...

So my question is the following: 
- how may I copy/synchronize the repository for updates/upgrades for my ubuntu 22.04 to a USB-Stick ?
- how may I configure my ubuntu computer so that it takes the USB-stick as a "repository" 

Thanks !
Vincent

---

### Post by tea for one on 2022-12-06
This link should provide food for thought
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

However, synaptic is not installed as default so you will have to download the deb package first.
[https://packages.ubuntu.com/jammy/synaptic](https://packages.ubuntu.com/jammy/synaptic)

---

