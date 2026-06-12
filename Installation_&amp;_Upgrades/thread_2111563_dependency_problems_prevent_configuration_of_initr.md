---
title: "dependency problems prevent configuration of initramfs-tools"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by joshhaglund on 2013-02-02
Yesterday I ran the usual updates and it ended with errors:

dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.

It appears to me the comparison operator should be >= instead of << but I'm not sure if that's the problem.

I tried:
sudo dpkg --clear-avail
sudo aptitude update
sudo aptitude safe-upgrade --full-resolver

I'm running 12.04 amd64

---

### Post by jdsmofo on 2013-02-05
I am having the same problem, also with 12.04 amd64. I've tried every suggestion I can find, but nothing has worked.  For example:

sudo apt-get install --reinstall initramfs-tools

Returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/49.0 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by joshhaglund on 2013-02-06
This is not a recommended fix because it might break something but it worked for me.

sudo edit /var/lib/dpkg/status
find the line "Package: initramfs-tools" (line 3439 for me)
A few lines down, look for the offending dependency in the "Depends:" line
delete that dependency but don't touch the others and watch the comma pattern:
initramfs-tools-bin (<< 0.99ubuntu13.1~)

then I did:
sudo apt-get update 
sudo apt-get install -f

Looking at the /status file now, I see that the depencency is now:
initramfs-tools-bin (<< 0.99ubuntu13.1.1~)

so, it added a .1 before the ~ and maybe you could just do that.
good luck!

Also, if this affected you I suggest clicking the 'this bug affects me' thing on this bug report: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/984688](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/984688)

The versions of initramfs-tools are different in that bug report but I suspect the cause is the same.

---

### Post by wnwLnJX on 2013-09-08
Although you indicate the fix you proposed is not recommended, I would like to say that it saved my day. I did exactly as you indicated iand it worked just fine. On top of that I went back to the "Synaptic Package Manager" performed a refresh where it proposed an update of "initramfs-tools" and it worked. Now both "initramfs-tools" and "initramfs-tools-bin" are updated and have the same version i.e. 0.99ubuntu13.2. The problem I had occured in LinuxMint 13 (maya) 32-bit on a Asus EeePC 1000 SDD.

---

