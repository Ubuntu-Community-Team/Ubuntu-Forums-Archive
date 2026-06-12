---
title: "AWN broke apt-get =\"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Hawk__0 on 2007-09-22
Sorry guys I tried following other threads and such.. but i'm stuck :(
basically, i had AWN installed, it ****** up, so i went to install the new version (without removing the old one.. i assume it would jsut overwrite it.) so i followed the instructions here:
[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository)

and when i get to"
 "For AWN BZR do:
sudo apt-get install avant-window-navigator-bzr"
i get this:
```

steve@steve-desktop:~$ sudo apt-get install avant-window-navigator-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avant-window-navigator-bzr is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libawn-bzr (= 0.1.2-bzr78-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

so i tried installing the dependencies, and, 
```
steve@steve-desktop:~$ sudo apt-get install libawn-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-awn libawn0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.8kB of archives.
After unpacking, 111kB of additional disk space will be used.
(Reading database ... 156135 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.1.2-bzr78-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

arrrrg frustrated! it broke my damn apt-get...
how fix?

thx in advance

---

### Post by Pumalite on 2007-09-22
How about just running: sudo apt-get -f install

---

### Post by Hawk__0 on 2007-09-22
didnt work. 
```
steve@steve-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-awn libawn0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.8kB of archives.
After unpacking, 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 156135 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.1.2-bzr78-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.1.2-bzr78-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@steve-desktop:~$ 


```

---

### Post by Pumalite on 2007-09-22
Try then:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by Hawk__0 on 2007-09-22
ok i fixed it thanks!

---

### Post by Pumalite on 2007-09-22
You are welcome. Happy Ubuntuing!

---

