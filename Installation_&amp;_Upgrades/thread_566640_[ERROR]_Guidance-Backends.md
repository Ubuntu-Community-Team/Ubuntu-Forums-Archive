---
title: "[ERROR] Guidance-Backends"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by kmslinux on 2007-10-03
When I tried to apt-get dist-upgrade from Feisty to Gutsy, I got an error saying that dpkg returned an error code (1). I then assumed the error was from ggz-gnome-client, because it was the package above the "Errors were encountered..." message, tried to apt-get remove ggz-gnome-client (I didn't need it, anyways...), and it told me dependencies were unmet. I deciphered from that error message that I had to apt-get -f install. I did. (By the way, I am using sudo). I tried apt-get -f install. It didn't work. Here's the code.

```
connor@Connubuntu:/downloads$ sudo apt-get -f install
[sudo] password for connor:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgcj7-jar libgcj7-0 feisty-wallpapers liblockdev1 libwxgtk2.4-1 libtdb1 libggzmod4 fast-user-switch-applet libslab0 libcrypto++5.2c2a
  feisty-session-splashes libgda2-3 libggzcore7 libgs-esp8 libgda2-common libgdiplus
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  guidance-backends
The following NEW packages will be installed:
  guidance-backends
0 upgraded, 1 newly installed, 0 to remove and 313 not upgraded.
464 not fully installed or removed.
Need to get 0B/254kB of archives.
After unpacking 1397kB of additional disk space will be used.
Do you want to continue [Y/n]?  
```


I then hit Y.


```
Do you want to continue [Y/n]? y
(Reading database ... 202308 files and directories currently installed.)
Unpacking guidance-backends (from .../guidance-backends_0.8.0svn20070928-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/guidance-backends_0.8.0svn20070928-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/guidance/vesamodes', which is also in package kde-guidance
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/guidance-backends_0.8.0svn20070928-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
connor@Connubuntu:/downloads$
```

---

### Post by kmslinux on 2007-10-03
OMG!!! Am I the only one who NEVER gets replies? No one ever reples to any of my posts! Jeez... Oh well. BUMP!

---

### Post by kiros on 2007-10-03
hi
Try : kde-guidance_0.8.0svn20070727-0ubuntu2.
It works for me.

---

### Post by kmslinux on 2007-10-03
Trying it now...

---

### Post by kmslinux on 2007-10-03
Works now. Thanks.

---

### Post by poets1977 on 2007-10-04
hi people,
can you tell me how you solved this problem?
I can't install kde-guidance_0.8.0svn20070727-0ubuntu2...same problem as guidance-backends.
Thank you.

---

### Post by trixtah on 2007-10-06
I'm having the same problem. Trying to install kde-guidance_0.8.0svn20070727-0ubuntu2_i386.deb tells me that I don't have guidance-backends installed, so the dependencies are not met. It's going around in circles a bit here....

---

### Post by trixtah on 2007-10-06
Ok, I fixed the above problem by manually downloading and installing guidance-backends_0.8.0svn20070727-0ubuntu2_i386.deb. Then the kde-guidance package was fine, and I was able to run dselect > install to get everything else moving again (for now)

---

