---
title: "Is there a way to compare installed packages?"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by dolson on 2005-09-10
I am currently running on Debian Sid.

I was wondering if there was a way to check to see what packages I have installed on my system versus what is available in Ubuntu? I know that Ubuntu does not have everything that Sid does, but as long as the apps that I have installed are there, then I should be good.

I know I can get a list via `dpkg --get-selections` but is there a list somewhere of every Ubuntu package? If there is, then I can do the scrub comparison myself easily enough.

The format I would be looking for is simply the package name, no version info or anything, ie:

```
dana@digory:~$ dpkg --get-selections | head
aalib1                                          install
acroread                                        install
adduser                                         install
aget                                            install
alien                                           install
alsa-base                                       install
alsa-oss                                        install
alsa-utils                                      install
apt                                             install
apt-utils                                       install
dana@digory:~$
```

(The whitespace and install is ok, but not necessary, just the package name.)

Thanks!

---

### Post by bsussman on 2005-09-11
Try this link for info on all packages in ubuntu:

[https://wiki.ubuntu.com/SeedManagement](https://wiki.ubuntu.com/SeedManagement)

---

