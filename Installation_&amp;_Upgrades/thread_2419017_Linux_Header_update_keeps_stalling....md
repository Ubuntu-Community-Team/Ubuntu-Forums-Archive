---
title: "Linux Header update keeps stalling..."
date: 2019-05-15
forum: Installation &amp; Upgrades
---

### Post by mlhudson on 2019-05-15
I got an update alert through the Software Update app. Tried to install and it keeps hanging. even when I try it through command line. I'm not a pro user, so I'm not sure what exactly I need to do.

In trying to sort it out, here's some of what I found:
```
matt@mattbuntu:~$ sudo apt-get install -f
[sudo] password for matt: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
matt@mattbuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 5.0.0.15.16); however:
  Version of linux-headers-generic on system is 5.0.0.13.14.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic

```

What do I do next?

---

### Post by Impavidus on 2019-05-15
Based on your 5.0 kernel, I assume you use Ubuntu 19.04. Now I wonder where you got linux kernel 5.0.0-15, as the latest in the repositories is 5.0.0-13. Maybe you enabled the proposed repository? Probably best to disable proposed and downgrade linux-generic to 5.0.0.13.14.

---

### Post by jvaudrey on 2019-05-16
Im having the same problem,  proposed repository is not enabled (in fact its a brand new fresh install) 


```
Preparing to unpack .../linux-libc-dev_5.0.0-16.17_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.0.0-16.17) over (5.0.0-15.16pop0) ...
dpkg: error processing archive /var/cache/apt/archives/linux-libc-dev_5.0.0-16.17_amd64.deb (--unpack):
 unable to open '/usr/share/doc/linux-libc-dev/copyright.dpkg-new': Operation not permitted
Preparing to unpack .../libapt-pkg5.0_1.8.1_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.8.1) over (1.8.0) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_5.0.0-16.17_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Impavidus on 2019-05-17
5.0.0-15 is now in the official repos, so the issue from the OP should be fixed now. Thread has been marked solved. Although, I think it was already marked solved when first opened.

For the next issue (by another user), I suggest you start your own thread (one not marked solved). It may help if you put the output of the command```
apt-cache policy linux-libc-dev
```in your post.

---

