---
title: "&quot;Update&quot; failed miserably please advise"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by m.merranko on 2009-12-20
Yesterday I tried to "upgrade" to the newest version of ubuntu 9.10 Karmic Koala from the existing 9.04 Jaunty Jackalope
after reporting 2 or 3 errors it restarted leaving this



fsck from util-linux-ng 2.16
/dev/sda1 contains a file system with errors, check forced.
Filesystem checks are in progress (ESC to cancel):
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e., without -a or -p options)
mountall: fsck / [303] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (293) terminated with status 3
Mount of file system failed.
A maintenance shell shell will now be stated.
CONTROL-D will terminate this shell and re-try.
root@merranko:~# _




What the deuce?
Help me out please.

---

### Post by darkod on 2009-12-20
I don't know why it happened but as it says, run the fsck manually. Boot with the ubuntu cd, Try Ubuntu option, and in terminal run:
sudo fsck /dev/sda1

---

### Post by m.merranko on 2009-12-20
i have done this and i had to hit 'y' a million times to fix a bunch of stuff and then i rebooted and this is up there now (and it froze)


fsck from util-linuxng 2.16
/dev/sda1: clean, 228136/2354688 files, 5527461/9408057 blocks
* Preparing restricted drivers...
* Starting AppArmor
* Configuring network interfaces...
* Starting bluetooth
* Starting network connection manager NetworkManager 
* Starting Common Unix Printing System: supsd
* PulseAudio configured for per-user sessions
* Enabling additional executable binary formats binfmt-support
* Checking battery state...
...done.

---

### Post by phillw on 2009-12-20
Hi,

Reboot from the LiveCD again, then from terminal issue
```
sudo e2fsck -y /dev/sda1 
```

The -y will stop you from pressing the yes a million times.

Then try rebooting.

Phill.

---

### Post by m.merranko on 2009-12-21
Hah I was just going at it for a while and the screen went blank and i reset the computer and it booted right up.  I did absolutely nothing to aid this besides hitting yes a million times (thanks phillw i will remember that in the future)

---

