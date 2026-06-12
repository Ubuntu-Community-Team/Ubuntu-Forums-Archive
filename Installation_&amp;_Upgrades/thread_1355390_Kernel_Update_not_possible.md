---
title: "Kernel Update not possible"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Votan on 2009-12-14
Greetings,

I have a quite severe problem regarding my Ubuntu 9.10 root server. The server was running 8.04, I later upgraded to 8.10, 9.04 and now to 9.10 recently. Suddenly I noticed that when I do the usual updates via the update manager i get a lot of error messages. These are the messages I get in synaptic:

```

E: linux-image-2.6.31-17-server: subprocess installed post-installation script returned error exit status 2
E: linux-backports-modules-2.6.31-17-server: dependency problems - leaving unconfigured
E: linux-backports-modules-karmic-server: dependency problems - leaving unconfigured
E: linux-image-server: dependency problems - leaving unconfigured
E: linux-server: dependency problems - leaving unconfigured

```

And a little more information when I try to "upgrade" via console with *sudo apt-get upgrade*:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-2.6.31-17-server (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-server
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-17-server (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.31-17-server:
 linux-backports-modules-2.6.31-17-server depends on linux-image-2.6.31-17-server; however:
  Package linux-image-2.6.31-17-server is not configured yet.
dpkg: error processing linux-backports-modules-2.6.31-17-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-karmic-server:
 linux-backports-modules-karmic-server depends on linux-backports-modules-2.6.31-17-server; however:
  Package linux-backports-modules-2.6.31-17-server is not configured yet.
dpkg: error processing linux-backports-modules-karmic-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.31-17-server; however:
  Package linux-image-2.6.31-17-server is not configured yet.
dpkg: error processing linux-image-server (--configurNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                               No apport report written because the error message indicates its a followup error from a previous failure.
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     e):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.31.17.30); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-17-server
 linux-backports-modules-2.6.31-17-server
 linux-backports-modules-karmic-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I did sudo apt-get update before trying to update my kernel and I get these error messages. The command "uname -a" tells me I am currently using kernel 2.6.27.9 so this is quite a serious problem.

any ideas why I cannot install the current server kernel ?

---

### Post by zvacet on 2009-12-15
```
sudo dpkg --configure -a
```

---

