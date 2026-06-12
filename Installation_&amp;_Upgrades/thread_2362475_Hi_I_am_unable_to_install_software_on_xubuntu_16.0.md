---
title: "Hi I am unable to install software on xubuntu 16.04"
date: 2017-05-29
forum: Installation &amp; Upgrades
---

### Post by gagg2 on 2017-05-29
When ever I try to install anything from the software program, I hit install It asks me for my password shows installing and does not install any software for hours.
When I try to install anything from the terminal I get this error
```

gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ sudo apt install okular
Reading package lists... Done
Building dependency tree       
Reading state information... Done
okular is already the newest version (4:15.12.3-0ubuntu1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up phonon:amd64 (4:4.8.3-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package phonon:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libokularcore7:
 libokularcore7 depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package libokularcore7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of okular:
 okular depends on libokularcore7 (= 4:15.12.3-0ubuntu1); however:
  Package libokularcore7 is not configured yet.
 okular depends on kde-runtime (>> 4:4.10); however:
  Package kde-runtime is not configured yet.
 okular depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package okular (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 phonon:amd64
 kde-runtime
 libokularcore7
 okular
E: Sub-process /usr/bin/dpkg returned an error code (1)
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ 

```
I am running it on an Hp laptop model P108tx
8GB Ram
I7

---

### Post by Impavidus on 2017-05-29
It seems that your package manager is messed up. Make sure all package managers (software centre, synaptic, update manager etc) are closed, then try```
sudo dpkg --configure -a
```It may give a more useful error message.

---

### Post by Autodave on 2017-05-29
Is your machine set up for automatic updates? If not, that may possibly holding it back. Or, you may need to reinstall "libokularcore7" again.  Let's start by making sure your machine is updated. In a terminal window, run this:

sudo apt-get update
sudo apt-get upgrade

After that is completed, see if you still have the error. Or, if you get that error before that completes, let's go to  either "software center" or "synaptic" and reinstall the 
libokularcore7 package.

---

### Post by gagg2 on 2017-05-29
Hi thanks for the reply.
This the output for sudo apt-get update reply
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get update
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ 

output for sudo apt-get upgrade
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]

---

### Post by gagg2 on 2017-05-29
Hi thanks for the reply.

This is what I got
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$ sudo dpkg --configure -a
Setting up phonon:amd64 (4:4.8.3-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package phonon:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of okular:
 okular depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package okular (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libokularcore7:
 libokularcore7 depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package libokularcore7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on phonon; however:
  Package phonon:amd64 is not configured yet.


dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phonon:amd64
 okular
 libokularcore7
 kde-runtime
gagg@gagg-HP-Pavilion-15-Notebook-PC:~$

---

### Post by oldos2er on 2017-05-29
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

Update Manager might be running in the background. Can you run ```
sudo fuser -v /var/cache/debconf/config.dat
``` and copy/paste its output here?

---

### Post by gagg2 on 2017-05-30
Hi oldos2er thanks for the reply.
Here's is the output
USER        PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       7390 F.... dpkg-preconfigu

---

### Post by oldos2er on 2017-05-30
So take the PID from that output, and kill it: ```
sudo kill 7390
``` Note the process may have a different ID now if it's still running.

If that doesn't work try ```
sudo kill -9 PID
``` Replace PID with the actual process number.

---

### Post by gagg2 on 2017-06-01
Thankyou so much everything is working now. Much appreciated.

---

### Post by vasa1 on 2017-06-01
> **gagg2 said:**
> Thankyou so much everything is working now. Much appreciated.

Then please visit [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

