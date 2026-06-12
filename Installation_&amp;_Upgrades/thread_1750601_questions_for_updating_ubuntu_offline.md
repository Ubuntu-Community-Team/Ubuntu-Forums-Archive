---
title: "questions for updating ubuntu offline"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by ipfreak on 2011-05-05
hi all:  

i have ubuntu boxes (10.04 LTS) located behind firewalls and have no internet access at all.  

are there any ways i can patch the systems offline?  

also i need to get openssh-server packages installed. 

on one machine (live usb drive), i downloaded packages with following command:  

sudo apt-get source -d openssh-server  

that cmd gave me three files:  

openssh_5.3pl-3ubuntu6.debian.tar.gz 
openssh_5.3pl-3ubuntu6.dsc 
openssh_5.3pl.orig.tar.gz  

now question is:  how could i get them installed?  

thanks for help...

---

### Post by Frogs Hair on 2011-05-05
I have not done offline updates , but here are two links that may help. 

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

### Post by ipfreak on 2011-05-05
> **Frogs Hair said:**
> I have not done offline updates , but here are two links that may help. 

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

thanks. it seems to be working but actually not working right.

i tried to mark the package of "openssh-server" and it refused for dependency issue. complaining that openssh-client is a bit too old for the new openssh-server...

are there any ways to patch up the installed system offline first before installing new packages?

---

### Post by Cheesehead on 2011-05-05
You don't want new (11.04) packages. You want packages that match the release on your system (10.04).

Personally, I recommend the 'apt-zip' package for sneakernet installs if you have an online Ubuntu or Debian system. It will automatically get the correct version (and updates) for you.

Also, learn how to use the apt-cache command. It is a great resource for offline package searching, dependencies, and other important package information.

Don't download source unless you intend to compile it yourself. If you really want to manually download packages, use [http://packages.ubuntu.com](http://packages.ubuntu.com) . Simply double-click on the deb file to install it.

I did a whole offline dist-upgrade from 5.10 to 6.06 via USB stick from packages.ubuntu.com. Not really understanding the process or how the system was trying to help me, it took three days. Today I could do it manually in a few hours. With apt-zip I could do it in a few *minutes*.

---

### Post by ipfreak on 2011-05-06
> **Cheesehead said:**
> You don't want new (11.04) packages. You want packages that match the release on your system (10.04).

Personally, I recommend the 'apt-zip' package for sneakernet installs if you have an online Ubuntu or Debian system. It will automatically get the correct version (and updates) for you.

Also, learn how to use the apt-cache command. It is a great resource for offline package searching, dependencies, and other important package information.

Don't download source unless you intend to compile it yourself. If you really want to manually download packages, use [http://packages.ubuntu.com](http://packages.ubuntu.com) . Simply double-click on the deb file to install it.

I did a whole offline dist-upgrade from 5.10 to 6.06 via USB stick from packages.ubuntu.com. Not really understanding the process or how the system was trying to help me, it took three days. Today I could do it manually in a few hours. With apt-zip I could do it in a few *minutes*.


really i merely followed the advices from the links provided by [Frogs Hair]("http://ubuntuforums.org/member.php?u=1024576") and set up a local depository. those information were supposed to be for lucid only.

i think it was due to the fact the newly installed system is not patched up. the package of openssh-clietnt was automatically installed by default with the cd (10.4 LTS) but the package information (for lucid) i downloaded must have been patched up to newer versions.

---

