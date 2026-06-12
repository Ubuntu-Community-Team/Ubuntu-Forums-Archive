---
title: "FFmpeg iinstallation on ubuntu 15.10"
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by naveen15 on 2016-01-09
Hi,
To install ffmpeg followed these commands :- 

```
sudo apt-add-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install ffmpeg

After running these commands I get error :-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate
```

Please help me on this. 

Thanks in Advance

---

### Post by kc1di on 2016-01-09
The error your getting means that ffmpeg file is not in the ppa's repository.  however I found it in the restricted repositories , make sure you have the restricted repositories enabled and run the install again. 

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install ffmpeg
```

should work then.

(note: if you have not already done so I recommend that you install synaptic package manager```
sudo apt-get install synaptic
``` Then use that to install the other files. )

---

### Post by naveen15 on 2016-01-10
When I run command :- sudo apt-get install synaptic

I get this following output 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate


and when I run command :-  sudo apt-get install ubuntu-restricted-extras

output is :- 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras


Please help me..

---

### Post by kansasnoob on 2016-01-10
You should purge that ppa. Please read:

[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

Specifically:

> Please note that if using this ppa I would *not* try upgrading to 14.10/15.04, ect. Do a fresh install instead. The intent here is just for users wishing to stay on 14.04

---

