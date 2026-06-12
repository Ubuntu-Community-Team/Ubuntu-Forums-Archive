---
title: "keep old config after apt install"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by ptz2 on 2019-04-10
Package installation question. I am on Ubuntu xenial, packaging some code of mine to a deb package and installing it with apt/apt-get. Problem: I can't get apt-get to keep an old configuration file when updating the package. Things I tried: 


```
apt-get -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install <package>
```
```
export DEBIAN_FRONTEND=noninteractive ; apt-get install -y -o Dpkg::Options::="--force-confold" <package>
```


And a few variations; I tried both editing and not editing the config file prior to running the package update. Nothing works, the new config file is always silently installed (without backing up the old one).


Suggestions?

---

