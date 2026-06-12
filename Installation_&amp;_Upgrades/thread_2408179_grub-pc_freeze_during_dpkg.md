---
title: "grub-pc freeze during dpkg"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by keysman on 2018-12-15
Good morning, I have an issue on my Ubuntu Server 16.04 with xen installed. After an unsuccessful safe-upgrade, I'm not able to update the package grub-pc. Let me show you the results of some statements:

```
root@jasmin /home/keysman # aptitude update
Hit [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) xenial InRelease
Hit [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) xenial-backports InRelease                                        
Hit [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) xenial-updates InRelease
Hit [http://mirror.hetzner.de/ubuntu/security](http://mirror.hetzner.de/ubuntu/security) xenial-security InRelease
Hit [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease
Hit [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Get: 1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Fetched 107 kB in 0s (130 kB/s) 
```                          
                            
```
root@jasmin /home/keysman # aptitude safe-upgrade
The following partially installed packages will be configured:
  grub-pc 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up grub-pc (2.02~beta2-36ubuntu3.20) ...
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.
```

Now the situation is stalled. Running the ps command in another shell:
```
root@jasmin /home/keysman # ps auxwww | grep dpkg
root     25563  0.0  0.1  22952  4472 pts/10   Ss+  09:03   0:00 /usr/bin/dpkg --status-fd 181 --configure grub-pc:amd64
root     25564  0.0  0.4  64784 16760 pts/10   S+   09:03   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     25575  0.0  0.0  15664  3480 pts/10   S+   09:03   0:00 /bin/bash /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     25675  0.0  0.0  15664  2148 pts/10   S+   09:03   0:00 /bin/bash /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     26039  0.0  0.0  16976   972 pts/7    S+   09:06   0:00 grep --color=auto dpkg

```

Killing the process 25563 and 25564 on the first shell I get the following messages:
```
E: Sub-process /usr/bin/dpkg exited unexpectedly
W: Operation was interrupted before it could finish
Failed to perform requested operation on package.  Trying to recover:
Setting up grub-pc (2.02~beta2-36ubuntu3.20) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
```

Running dpkg --configure -a, I've got the same stalled situation:
```
root@jasmin /home/keysman # dpkg --configure -a
Setting up grub-pc (2.02~beta2-36ubuntu3.20) ...
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.
```

```
root     26970  0.1  0.1  22944  4400 pts/0    S+   09:14   0:00 dpkg --configure -a
root     26971  2.8  0.4  64676 16740 pts/0    S+   09:14   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     26982  0.1  0.0  15664  3480 pts/0    S+   09:14   0:00 /bin/bash /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     27092  0.0  0.0  15664  2212 pts/0    S+   09:14   0:00 /bin/bash /var/lib/dpkg/info/grub-pc.postinst configure 2.02~beta2-36ubuntu3.17
root     27096  0.0  0.0  16976  1012 pts/7    S+   09:14   0:00 grep --color=auto dpkg
```

Can someone help me to fix this issue?

Thanks in advance

vv

---

