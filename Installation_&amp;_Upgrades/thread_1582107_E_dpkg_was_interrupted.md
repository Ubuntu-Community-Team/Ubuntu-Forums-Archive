---
title: "E: dpkg was interrupted"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by l0uismustdie on 2010-09-26
Earlier today I was faced with the following message:
```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```
after attempting to do a sudo apt-get install

Following the prompts request I ran the command and received the resulting error:
```

***@***:/etc$ sudo dpkg --configure -a
Setting up nfs-kernel-server (1:1.2.0-4ubuntu4) ...
 * Exporting directories for NFS kernel daemon...                                                   [ OK ] 
 * Starting NFS kernel daemon                                                                       [fail] 
invoke-rc.d: initscript nfs-kernel-server, action "start" failed.
dpkg: error processing nfs-kernel-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-kernel-server

```

I'm not exactly sure how to repair nfs-kernel-server or how it got damaged...

---

### Post by sikander3786 on 2010-09-26
Try to stop nfs-kernel-server prior to configuring it.

```

sudo /etc/init.d/nfs-kernel-server stop 

```

Then

```

sudo dpkg --configure nfs-kernel-server 

```

Then

```

sudo apt-get update

```

---

### Post by l0uismustdie on 2010-09-26
Thanks for your prompt reply but it doesn't look like this is working.  Here is output of what you suggested
```

***@***:/etc$ sudo /etc/init.d/nfs-kernel-server stop
[sudo] password for ***: 
 * Stopping NFS kernel daemon                                                                       [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                 [ OK ] 
***@***:/etc$ sudo dpkg --configure nfs-kernel-server
Setting up nfs-kernel-server (1:1.2.0-4ubuntu4) ...
 * Exporting directories for NFS kernel daemon...                                                   [ OK ] 
 * Starting NFS kernel daemon                                                                       [fail] 
invoke-rc.d: initscript nfs-kernel-server, action "start" failed.
dpkg: error processing nfs-kernel-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-kernel-server

```

---

### Post by sikander3786 on 2010-09-26
What happens when you do this.

```
sudo /etc/init.d/nfs-kernel-server stop
```

```
sudo apt-get remove nfs-kernel-server
```

If that doesn't work,

```
sudo apt-get install --reinstall nfs-kernel-server
```

Or

```
sudo dpkg -r nfs-kernel-server
```

---

### Post by l0uismustdie on 2010-09-26
Doesn't look like this was successful either... when I tried the reinstall line it is still failing on starting the NFS kernel demon.  Here is some output after a reboot:
```

***@***:~$ sudo dpkg -r nfs-kernel-server
[sudo] password for josh: 
(Reading database ... 161678 files and directories currently installed.)
Removing nfs-kernel-server ...
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
Processing triggers for man-db ...
Processing triggers for ureadahead ...

```

This was after I uninstalled it.

Then for a reinstall:
```

***@***:~$ sudo apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nfs-kernel-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/158kB of archives.
After this operation, 397kB of additional disk space will be used.
Selecting previously deselected package nfs-kernel-server.
(Reading database ... 161654 files and directories currently installed.)
Unpacking nfs-kernel-server (from .../nfs-kernel-server_1%3a1.2.0-4ubuntu4_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up nfs-kernel-server (1:1.2.0-4ubuntu4) ...
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [fail] 
invoke-rc.d: initscript nfs-kernel-server, action "start" failed.
dpkg: error processing nfs-kernel-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also tried 
```

sudo apt-get install --reinstall nfs-kernel-server

```

---

### Post by sikander3786 on 2010-09-26
Well I'm out of ideas for now. You should also try to remove and reinstall nfs-common. 

Did you Google it? Search a solution there or wait for someone else to answer. I am also going to Google, will let you know if I find something.

---

### Post by l0uismustdie on 2010-11-20
Anyone else have ideas about this one?

---

