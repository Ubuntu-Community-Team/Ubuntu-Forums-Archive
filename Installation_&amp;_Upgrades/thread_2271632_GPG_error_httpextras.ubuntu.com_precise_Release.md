---
title: "GPG error: http://extras.ubuntu.com precise Release"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by cbrun on 2015-03-31
There have been several questions around GPG errors, all with a similar solutions that involve cleaning out the lists file.  I have not had any success with that approach and looking for either what I'm doing wrong or what I might try next.
I am running Ubuntu 12.04 LTS.

ubuntuBB:~$ sudo apt-get clean
ubuntuBB:~$ cd /var/lib/apt
ubuntuBB:/var/lib/apt$ sudo mv lists list.cb
ubuntuBB:/var/lib/apt$ sudo mkdir -p lists/partial
ubuntuBB:/var/lib/apt$ sudo apt-get clean
ubuntuBB:/var/lib/apt$ sudo apt-get update
...
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192




ubuntuBB:/var/lib/apt$ sudo rm /var/lib/apt/lists/* -vf
ubuntuBB:/var/lib/apt$ sudo apt-get update
...
Reading package lists... Done

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

---

### Post by oldos2er on 2015-03-31
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

### Post by cbrun on 2015-04-01
Ann - Thank you.  That was the solution.

---

