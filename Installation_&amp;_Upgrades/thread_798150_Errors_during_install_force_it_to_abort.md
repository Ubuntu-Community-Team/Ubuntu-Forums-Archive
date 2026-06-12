---
title: "Errors during install force it to abort"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by mrs260 on 2008-05-17
This is the third time I've tried and failed to upgrade from Gutsy to Hardy, so I thought I'd ask for help before just reinstalling Gutsy from CD again.

I haven't rebooted yet--I don't know if it'll work.

During the install, I started to get more and more errors popping up, and eventually the dependencies on packages with errors got to be too much: too much was being left unconfigurable, so the the upgrade aborted. The update manager seemed to crash and now I can't open it. The errors, in general, were "subprocess post-installation script returned error exit status 139".

When I try to open Synaptic, I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I open the terminal and run the command, it tries to configure the previously failed packages. I again get a series of errors, starting with that same error 139, a couple of segmentation faults, then a long series of dependency problem errors. The last three lines before giving me my user prompt again are:

dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

I have tried running apt-get install upgrade (and update) but the terminal just asks me to run dpkg --configure -a again, and I get the same results.

---

### Post by empthollow on 2008-05-17
have you tried 
```
sudo apt-get -f install
```

---

### Post by mrs260 on 2008-05-17
I've tried that and had the same results as I described with regular sudo apt-get install. But thanks for the suggestion--I didn't know to try that.

I also tried rebooting in recovery mode. It gives me the option to repair broken packages, but when I try that, it says that it cannot remove the broken packages because the directory it's looking for doesn't exist.

I also get an error with sudo apt-get -f install that it can't resolve the hosts it's trying to download from, so it tries with previously downloaded packages. I was thinking of trying again with an ethernet cable instead of wireless.

ETA: When I reboot now, I have two different sets of 8.04 Ubuntu entries (regular and recovery): kernel 2.6.24-16-generic, and kernel 2.6.22-14-generic. I'm not sure which one I should be troubleshooting on. (With 7.10 I had entries for kernel 2.6.22-14-generic.) Also, when I try to boot in regular mode with either kernel, I can get to the login screen and enter my name and password, but then it hangs on a blank default-coloured screen. I'm not sure if it would eventually boot fully if I left it to try for awhile, but there seems to be no activity past the login/password point.

---

### Post by empthollow on 2008-05-18
hmm, i read a post with similar problems once and the solution was to use update manager for the upgrade.  you can try in recovery mode, or you can do ctrl + alt + F2 to get a console in regular mode - this can be done without logging in first. The command to run is:
```
sudo update-manager --dist-upgrade
```
hope that helps

---

### Post by mrs260 on 2008-05-18
This didn't work for me either, but I copied down the full error message. I have an ATI display driver that required me to download that firmware cutter thingy. Thought I'd mention that since the error has to do with the display.

```

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
 warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
 File "usr/bin/update-manager", line 43, in <module>
  gtk.init_check()
RuntimeError: could not open display

```

(Sorry it's been taking me so long between posts. I don't know if it's relevant to the Ubuntu issues, but ever since I updated to SP3 in my Windows XP partition, I've been having blue screens of death during or immediately after boot in Windows. It's been hard to stay in Windows long enough to get logged on here and reply to you.)

---

### Post by empthollow on 2008-05-18
it looks like it wants x to be running, what errors do you get when running
```
sudo apt-get dist-upgrade
```

---

