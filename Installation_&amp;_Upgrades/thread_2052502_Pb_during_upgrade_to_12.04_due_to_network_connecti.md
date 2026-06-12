---
title: "Pb during upgrade to 12.04 due to network connection loss"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by ruman on 2012-09-03
Hello,

While upgrading from 10.04 to 12.04 I got disconnected from the server and while trying to recover I am getting an error.
Before to recover I restored the original sources.list file and now when I try to use dpkg I get the following error:
```
sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages have unmet dependencies:
  libnih-dbus1: Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.1-1 is installed.
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10 is installed.

```Could someone advise what to do?

In addition, when I try apt-get -f install I get, after a long list of packages
```
0 upgraded, 0 newly installed, 1023 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2158MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]
```

Looks like that something left the system thinking it's already upgraded even if it's not.

---

### Post by mikewhatever on 2012-09-03
Hmm, ...why restore the sources' list and not continue with the upgrade?

---

### Post by darkod on 2012-09-03
Why did you restore the original sources.list? Did you try to continue with the new ones first?

And when you say disconnected from the server, you mean the internet connection went down?

If an upgrade has been interrupted, first you can try booting into recovery mode, when the recovery menu shows select Network first, that will activate internet. Then select Drop to root shell.

If you manage to get that far, once in the root shell try:
```
dpkg --configure -a
apt-get install -f
```

See if that can help. Note that you should try this with the new sources.list, like the upgrade left it.

---

### Post by ruman on 2012-09-03
> **mikewhatever said:**
> Hmm, ...why restore the sources' list and not continue with the upgrade?

I tried to continue with the upgrade but I get this
```
Package libc6-dev has broken Breaks on cmake
  Considering cmake 0 as a solution to libc6-dev 53
  Upgrading cmake due to Breaks field in libc6-dev
Investigating cmake
Package cmake has broken Depends on libarchive12
  Considering libarchive12 0 as a solution to cmake 0
  Holding Back cmake rather than change libarchive12
Investigating libc6-dev
Package libc6-dev has broken Breaks on cmake
  Considering cmake 0 as a solution to libc6-dev 53
  Upgrading cmake due to Breaks field in libc6-dev
Investigating cmake
Package cmake has broken Depends on libarchive12
  Considering libarchive12 0 as a solution to cmake 0
  Holding Back cmake rather than change libarchive12
Investigating libc6-dev
Package libc6-dev has broken Breaks on cmake
  Considering cmake 0 as a solution to libc6-dev 53
  Upgrading cmake due to Breaks field in libc6-dev
Investigating cmake
Package cmake has broken Depends on libarchive12
  Considering libarchive12 0 as a solution to cmake 0
  Holding Back cmake rather than change libarchive12
Investigating libc6-dev
Package libc6-dev has broken Breaks on cmake
  Considering cmake 0 as a solution to libc6-dev 53
  Upgrading cmake due to Breaks field in libc6-dev
Investigating cmake
Package cmake has broken Depends on libarchive12
  Considering libarchive12 0 as a solution to cmake 0
  Holding Back cmake rather than change libarchive12
Investigating libc6-dev
Package libc6-dev has broken Breaks on cmake
  Considering cmake 0 as a solution to libc6-dev 53
  Upgrading cmake due to Breaks field in libc6-dev
Investigating cmake
Package cmake has broken Depends on libarchive12
  Considering libarchive12 0 as a solution to cmake 0
  Holding Back cmake rather than change libarchive12
Done

Broken packages

Your system contains broken packages that couldn't be fixed with this
software. Please fix them first using synaptic or apt-get before
proceeding.

ERROR:root:self.prepared() failed

Preparing the upgrade failed

Preparing the system for the upgrade failed so a bug reporting
process is being started.
=== Command terminated with exit status 1 (Mon Sep  3 15:53:54 2012) ===

```

---

### Post by ruman on 2012-09-03
> **darkod said:**
> Why did you restore the original sources.list? Did you try to continue with the new ones first?

Answered above.

> **darkod said:**
> And when you say disconnected from the server, you mean the internet connection went down?

No, I am trying to upgrade a VM server that is hosted remotely and this is my personal internet connection that I lost and thus the ssh connection to the server.

> **darkod said:**
> If an upgrade has been interrupted, first you can try booting into recovery mode, when the recovery menu shows select Network first, that will activate internet. Then select Drop to root shell.

Since server is a VM that I am using remotely, I don't have access to Grub.

---

### Post by darkod on 2012-09-03
I think you can try those commands anyway. Usually if an upgrade goes wrong it can leave the machine unbootable, so recovery mode is the first thing on your mind. But if your machine (VM) boots, try those commands from within.

If you started the upgrade again it can fail, but those commands are slightly different. The first one finishes any packages that are pending configuration, and the second one tries to fix broken packages (the end of the message you posted says to try fixing with apt).

However, I believe you need to run these with the sources.list as it was after the upgrade, not as you changed it later. Detecting a wrong sources.list might confuse it.

---

### Post by nariub on 2012-09-03
had this problem last week
half-in half-out upgrade but i started with 
sudo do-release-upgrade
not the aptitutude thing

she went sideways in the middle, sources.list was still on precise
and no network connection to finish the upgrade, she was whining about unmet dependencies..

my fix was to 
find a 10.04.4 alt iso
make a boot disc from it.
boot the 10.04 alt iso
use rescue mode (the disc will give you a network connection)
in rescue mode i went to a prompt on my root partition on my harddrive..

sudo apt-get -f install
sudo dpkg --configure -a

rebooted to get off the iso disc 
xwindows still wasnt working so i did cntl-alt-f1 to get a command prompt

logged in
and did

sudo do-release-upgrade

it bombed the first time and i resurrected it rather than destroy it,  this had the effect of re-running the upgrade.. the second time it completed and let me log in via unity and a few more minor repairs and i was back in business..

---

### Post by ruman on 2012-09-04
I managed to come back in state where I have no more errors with following commands:
```
dpkg --configure -a
apt-get install -f
```

To do so, after restoring 10.04 sources.list, I removed/purge libc6, libc6-dev and cmake and reinstalled them.

Restarted the server without issue.

Then restarting the upgrade process with do-release-upgrade command but again was unable to complete with following errors:
```
A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

ERROR:root:failed to stop screensaver poke
Traceback (most recent call last):
  File "/tmp/tmpUrDAdc/DistUpgradeQuirks.py", line 833, in _stopPokeScreensaver
    res = self._poke.wait()
  File "/usr/lib/python2.6/subprocess.py", line 1170, in wait
    pid, sts = _eintr_retry_call(os.waitpid, self.pid, 0)
  File "/usr/lib/python2.6/subprocess.py", line 465, in _eintr_retry_call
    return func(*args)
OSError: [Errno 10] No child processes
ERROR:root:SystemError from cache.commit(): installArchives() failed

Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug in a browser at
http://bugs.launchpad.net/ubuntu/+source/update-manager/+filebug and
attach the files in /var/log/dist-upgrade/ to the bug report.
installArchives() failed

dpkg: dependency problems prevent configuration of libnih-dbus1:
 libnih-dbus1 depends on libnih1 (= 1.0.3-4ubuntu9); however:
  Version of libnih1 on system is 1.0.1-1.
dpkg: error processing libnih-dbus1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnih-dbus1

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.
```

---

