---
title: "Adding Repositories"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by corrytonapple on 2011-05-15
Hello Community!
I am trying to install BURG, following this guide:
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)
It has me add the repositories and the keys first thing, and I do.  But, I cannot get the system to work with it.  It says
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

```
What do I do to make the repositories available to my system?  I also have another application that needs the repositories, and is having the same error/warning.
Thanks!

---

### Post by plucky on 2011-05-16
> **corrytonapple said:**
> Hello Community!
I am trying to install BURG, following this guide:
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)
It has me add the repositories and the keys first thing, and I do.  But, I cannot get the system to work with it.  It says
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

```
What do I do to make the repositories available to my system?  I also have another application that needs the repositories, and is having the same error/warning.
Thanks!

Thats the problem with PPAs,just because there is a PPA for Maverick,doesn't mean there is one for Natty.

See [Here](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/)

You will have to wait until the owner of the PPA updates their repository for Natty,that is, if they will.

Remove the PPA from your sources.list.

Good Luck

---

### Post by NormanFLinux on 2011-05-16
You can still use the backports.... there should be no problem with using PPAs set up for Lucid and Maverick - as long as they are still maintained.

---

### Post by corrytonapple on 2011-05-16
Well, I saw the page you linked to plucky, and I have already seen it.  I went through, and figured I would just ask with Natty being the ubuntu version I through in until I get a solution.  While I was on IRC last night, ubottu gave me the answer.  Just go to the Terminal and type:
```
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  437D05B5S
```
Thanks for the help.

---

