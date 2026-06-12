---
title: "Dependency Issue"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by boxybrown on 2006-10-23
I was trying to run update and upgrade like normal when I found out that I have two broken packages.  So I ran apt-get check and I got this:

boxy@boxy-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mencoder: Depends: libdivxdecore0 (>= 1:5.0.1)
            Depends: libdivxencore0 (>= 1:5.0.1)
  mplayer: Depends: libdivxdecore0 (>= 1:5.0.1)
           Depends: libdivxencore0 (>= 1:5.0.1)
E: Unmet dependencies. Try using -f.


So I then ran apt-get -f install

boxy@boxy-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libdivxdecore0 libdivxencore0
The following NEW packages will be installed:
  libdivxdecore0 libdivxencore0
0 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
2 not fully installed or removed.
Need to get 0B/282kB of archives.
After unpacking 958kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libdivxdecore0 libdivxencore0
Install these packages without verification [y/N]? y
(Reading database ... 104113 files and directories currently installed.)
Unpacking libdivxdecore0 (from .../libdivxdecore0_1%3a5.0.1-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdivxdecore0_1%3a5.0.1-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdivxdecore.so.0.0.0', which is also in package libdivxdecore0-binary
Unpacking libdivxencore0 (from .../libdivxencore0_1%3a5.0.1-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdivxencore0_1%3a5.0.1-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdivxencore.so.0.0.0', which is also in package libdivxencore0-binary
Errors were encountered while processing:
 /var/cache/apt/archives/libdivxdecore0_1%3a5.0.1-1_i386.deb
 /var/cache/apt/archives/libdivxencore0_1%3a5.0.1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anyone know a way that I can fix this problem?  I haven't been able to fix it here or in Synaptic.  I can't update anything else until I get this fixed and and would really like this issue fixed before I jump to Edgy in a couple weeks here.  

Thanks

---

### Post by Jussi Kukkonen on 2006-10-23
You have some unofficial repositories enabled I suppose (based on the verification issue)? That may get you into problems...

---

### Post by fireduck on 2006-10-25
I am experiencing the exact same issue. From the timing of it I think it may have happened shortly after I installed the Flash Player 9 Beta. That's the only real lead I have.

---

### Post by dcherryholmes on 2006-11-28
Same here.  Is there any fix?  I tried commenting out Trevino's Flash repository and running apt-get update/upgrade again, but the system is just broken.

---

### Post by dcherryholmes on 2006-11-28
Disregard.  I had not commented out Trevino's Flash repository as I thought I had.  It was the culprit, and now my dependency issues are resolved.

---

