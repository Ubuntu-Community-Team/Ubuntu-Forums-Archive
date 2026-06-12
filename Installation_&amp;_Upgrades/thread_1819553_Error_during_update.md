---
title: "Error during update"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by killboymota on 2011-08-06
im using ubuntu 11.04. I already changed servers and nothing happened. I had not edited the sources.list but made a test to get the best server and nothing changed. thanks

> **Error During Update:**
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty/Release](http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release](http://archive.canonical.com/ubuntu/dists/natty/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release](http://extras.ubuntu.com/ubuntu/dists/natty/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-updates/Release](http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-updates/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-backports/Release](http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-backports/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-security/Release](http://ubuntu-archive.mirrors.proxad.net/ubuntu/dists/natty-security/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Frogs Hair on 2011-08-06
You could try these commands , another user was having the same problem two days ago and tried changing the server also . 
```
sudo dpkg -reconfigure -a
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

