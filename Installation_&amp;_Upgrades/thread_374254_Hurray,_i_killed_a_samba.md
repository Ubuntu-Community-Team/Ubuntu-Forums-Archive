---
title: "Hurray, i killed a samba"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by hothgremlin on 2007-03-02
Dear community!

I played with the samba config yestarday and it seemed i broke it. I then uninstalled samba aiming to reinstall it with apt-get install samba. What happened was this:
```

 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I then removed samba once again and looked for remaining pieces of the old installation. The directory /etc/samba was still existing, so i deleted it, hoping that a new install will bring back the old configuration.. 
Don't ask: it did not.

Any idea how i will get this thing working? The solutions posted in other threads didn't help.

with best regards,
hg

PS: i am using 6.01

---

### Post by LotsOfPhil on 2007-03-02
Not to continue you on your cycle, but you could try sudo aptitude purge samba and then reinstall.

---

### Post by hothgremlin on 2007-03-02
I did that:
```

aptitude purge samba
apt-get install samba
```

my server's answer:
```

 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:mad:

---

### Post by dannyboy79 on 2007-03-02
I am guessing you have a bad symlink laying around. Do a sudo find / -name *samba and then when you find the symlink, most likely in /etc/rc2.d/ and /etc/rc3.d/, (it might be the K09samba as this has been an issue in the past, somehow the link gets messed up) just delete them all, then try to reinstall samba. Note: I would use the find command over the locate in case the locate database hasn't been updated yet.

---

### Post by hothgremlin on 2007-03-02
thank you for the try; but it didn't work...

i did:
```
rm -r /etc/rc*.d/*samba
apt-get remove samba
aptitude purge samba
apt-get install samba

```


he did:
```

 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dannyboy79 on 2007-03-02
ok, wait. so are you saying that samba is installing but it's not working? if that's the case than you have bad symlinks somewhere. I know this because of this:
Starting Samba daemons...                                             [fail]

do any arise when you try to install samba? are you sure that all your symlinks are ok? do they all point to /etc/init.d/samba?

---

### Post by krokodil on 2007-03-04
I am having the exact same problem, also played around with smb.conf and purged samba with the idea of reinstalling fresh:

```
$ sudo aptitude install samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up samba (3.0.22-1ubuntu3.2) ...
 * Starting Samba daemons...                                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.2) ...
 * Starting Samba daemons...                                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
```

Here is where all my symlinks are pointing, still not working...

```
$ ls -als /etc/rc*.d/*samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc0.d/K19samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc1.d/K19samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc2.d/S20samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc3.d/S20samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc4.d/S20samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc5.d/S20samba -> ../init.d/samba
0 lrwxrwxrwx 1 root root 15 2007-03-04 14:31 /etc/rc6.d/K19samba -> ../init.d/samba

```

---

### Post by jhansonxi on 2007-03-04
Check the log to see if there are any clues:
/var/log/dpkg.log

---

### Post by asd0 on 2007-08-09
I had the same problem after some configuration changing and removing samba to restore the default configuration.
```
sudo apt-get remove --purge samba
sudo apt-get install samba
...
  * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
...
```
I found this solution:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-July/118600.html]("https://lists.ubuntu.com/archives/ubuntu-users/2007-July/118600.html")
For short, you have to reinstall samba-common:
```
sudo apt-get remove samba-common
sudo apt-get install samba
```
For me it solved it...

---

