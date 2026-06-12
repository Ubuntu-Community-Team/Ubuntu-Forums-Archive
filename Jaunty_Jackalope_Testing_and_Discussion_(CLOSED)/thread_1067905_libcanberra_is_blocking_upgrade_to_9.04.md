---
title: "libcanberra is blocking upgrade to 9.04"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by digitalchild on 2009-02-12
Hi all, 

I tried to upgrade my 8.10 box to jaunty 9.04 and now I'm blocked on the following error: 

here is my apt-get upgrade output

```

municchi@municchi-lnx:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gnome-session-canberra but it is not installed
E: Unmet dependencies. Try using -f.
municchi@municchi-lnx:/$ 
```

I tried with apt-get -f install, but I receive the same error

```
municchi@municchi-lnx:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libparted1.8-9 nvidia-177-modaliases
  libmagick++10 libgfortran3 libx264-59 libjline-java libavcodec51
  libservlet2.3-java libgtkglext1 libntfs-3g28
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-session-canberra
The following NEW packages will be installed:
  gnome-session-canberra
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
Need to get 0B/6754B of archives.
After this operation, 57.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 174633 files and directories currently installed.)
Unpacking gnome-session-canberra (from .../gnome-session-canberra_0.11-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-session-canberra_0.11-1ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also in package libcanberra-gnome
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session-canberra_0.11-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
municchi@municchi-lnx:/$ 

```

here is also my apt-get check output

```

municchi@municchi-lnx:/$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gnome-session-canberra but it is not installed
E: Unmet dependencies. Try using -f.
municchi@municchi-lnx:/$ 

```

Could someone help me? 
Thanks a lot for your time! 

Digital Child

---

### Post by nick_stokie on 2009-02-15
This might be related:

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/302251/comments/21](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/302251/comments/21)

---

### Post by digitalchild on 2009-02-15
Yes, I also confirm that this workaround solved my issue:


 # aptitude remove libcanberra-gnome -- also removes ubuntu-desktop
 # apt-get update
 # apt-get upgrade
 # apt-get install ubuntu-desktop

Thanks, nick_stokie!

DigitalChild

---

