---
title: "reconnect to running &quot;do-release-upgrade&quot;"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by nashibuntu on 2012-04-30
I was running a "do-release-upgrade" via the command line in a terminal (not over ssh). Some way through the upgrade I was told that there was a difference between two config files and I decided to drop to a shell to examine the differences. After exiting emacs the terminal was somehow corrupted. I tried 'clear' - but it didn't fix it, so I typed 'exit' to return to the upgrade process. However, instead of returning, the terminal exited completely!

I opened a new terminal and tried 'dpkg --configure -a' to continue, but it tells me 'dpkg: error: dpkg status database is locked by another process' so it appears the upgrade is still running.

When I do
ps aux | grep update

I get (amongst other things)
```
root     22170  0.0  2.3 166120 89920 ?        S    Apr29   0:04 /usr/bin/python /tmp/update-manager-NOeOdy/precise --mode=server --frontend=DistUpgradeViewText
root     23152  0.0  0.2  20120  8104 pts/1    Ss   19:35   0:01 /usr/bin/dpkg --force-overwrite --status-fd 9 --configure libdconf0 dconf-service dconf-gsettings-backend cheese-common ...

```
 
Question: How can I reconnect to this stalled upgrade process?

Thank you.

---

### Post by nashibuntu on 2012-04-30
I am considering sending the dpkg process the HUP signal to let it know that PTS/1 is dead:

```
sudo kill -HUP 23152
```

This will presumably kill the upgrade process in an 'appropriate' manner - after which I am hoping I will be able to restart it with 'sudo dpkg --configure -a'

I'd be interested to know whether this is the best/safest course of action.

Thanks.

---

### Post by mikeb123 on 2012-05-03
I've had exactly the same experience (well, with vi rather than emacs but other than that identical). I'm afraid I don't have an answer for you - my system has been left in an unknown state so I'm reverting to backup.

I've file a bug report at [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/994063](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/994063). Between this issue and bug 924079, which I've also hit on another system, upgrading to Precise has so far been impossible to do cleanly from either Lucid or Oneiric. It certainly doesn't feel ready for release.

---

### Post by nashibuntu on 2012-05-03
I agree with you about it not being ready for release. I too have tried it on two computers and in both cases the upgrade failed.

The first time was via the update manager from a clean Oneiric desktop install. At some stage the computer hung completely. I waited several hours but the screen was frozen - no mouse movement or response to keyboard shortcuts, including CTRL-ALT-number. I was forced to reboot. On rebooting the mouse was still frozen - but I manged to continue the upgrade from the command line, after which everything appears to be working fine. It's frustrating that there doesn't appear to be an easy way to navigate around the top and side bars without the mouse.

The second time was a server install which has since had unity-desktop added to it. I encountered the problem described in the posts above with the console which vanished. In the end sending the HUP signal did nothing and I was forced to kill the upgrade. I tried continuing the upgrade with

sudo dpkg --configure -a

but unfortunately it didn't go smoothly. I got told that Samba failed to install properly and now my system is unstable.

I tried

sudo apt-get update
sudo apt-get install -f

but I get told
```
dpkg: dependency problems prevent configuration of samba
 samba depends on samba-common (= 2:3.6.3-2ubuntu2); however:
  Version of samba-common on system is 2:3.6.3-2ubuntu2.1.
 samba depends on libwbclient0 (= 2:3.6.3-2ubuntu2); however:
  Version of libwclient0 on system is 2:3.6.3-2ubuntu2.1.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Now ubuntu frequently pops up messages telling me that an error has been encountered and it needs to send an error report. Furthermore, when I click the "Dash Home" button in the top left hand corner it is completely empty. No applications show up, even when typing in the search box.

I'd be grateful about ideas for how to recover from this.

Thanks.

---

