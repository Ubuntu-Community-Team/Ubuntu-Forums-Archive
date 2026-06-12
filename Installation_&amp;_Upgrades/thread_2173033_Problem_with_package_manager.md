---
title: "Problem with package manager"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by akamra on 2013-09-07
Hi guys,

I was trying to install acroread when I mistakenly tried to install acroread-bin i386. I guess it was a mistake since I have a 64 bit system. Now this package is stuck and I can neither complete the installation nor roll it back. I am not able to install or update or remove any package ever since. Following is the output to sudo apt-get install -f:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  nvidia-settings-updates nvidia-settings
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acroread-bin:i386
Suggested packages:
  libldap2:i386 libgnome-speech7:i386
The following NEW packages will be installed:
  acroread-bin:i386
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0 B/60.1 MB of archives.
After this operation, 142 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 392125 files and directories currently installed.)
Unpacking acroread-bin:i386 (from .../acroread-bin_9.5.5-1precise1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread-bin_9.5.5-1precise1_i386.deb (--unpack):
 trying to overwrite '/opt/Adobe/Reader9/Reader/intellinux/mozilla/prefs.js', which is also in package adobereader-enu:i386 9.5.5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/acroread-bin_9.5.5-1precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help will be greatly appreciated.

Thanks,
Akash

---

### Post by ibjsb4 on 2013-09-07
Try:

```
sudo apt-get clean && sudo apt-get update
```

And then try installing it.

```
sudo apt-get install acroread
```

---

