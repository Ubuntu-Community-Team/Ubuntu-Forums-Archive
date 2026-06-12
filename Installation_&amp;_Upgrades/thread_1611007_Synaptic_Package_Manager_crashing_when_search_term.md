---
title: "Synaptic Package Manager crashing when search term entered"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by PSpy on 2010-11-01
I'm running Ubuntu 10.04 on my EeePC Netbook.

Up until recently I have had no problems installing packages for various openSource projects and IDE's that I need.

However, today my Synaptic Package Manager (SPM) started crashing whenever I begin to enter a search term (ie, as soon as it starts querying a search result).

I tried updating and restarting, but that did not fix the problem.

I am not yet comfortable enough to use 'sudo apt-get install XXXX' and am still reliant on the SPM for getting the packages that I need.

When I enter 'gksudo -d synaptic' in terminal, it produces this output:
No ask_pass set, using default!
xauth: /tmp/libgksu-ENNKH0/.Xauthority
STARTUP_ID: gksudo/synaptic/2280-0-omnitool_TIME1332906
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

The SPM then opens.  Once again, when I start typing a search term, the application closes without explanation.

The terminal then produces the following output:
xauth: /tmp/libgksu-ENNKH0/.Xauthority
xauth_env: /var/run/gdm/auth-for-perry-JF7lVd/database
dir: /tmp/libgksu-ENNKH0

Any clue why my SPM is failing?  I really need to install a package asap...

---

### Post by forliberty on 2011-03-12
Bump. 

I'm having the same problem. I've been running 10.04 since it came out and have had no other problems. But I recently discovered that if I try to do a search in Synaptic Package Manager, it just closes. If I load it from the command line, it just closes without an error message. I checked out various other threads, but could not find a solution. Another thread suggested removing and reinstalling the apt-xpian-index package, but that didn't help. 

Any ideas??

---

### Post by Joncas on 2011-03-28
Hello,

landed here googling with the same problem :  Synaptic Package Manager crashes as soon as a search term is entered.

Has anyone found a solution ?

---

### Post by forliberty on 2011-03-29
This is a known bug, and there doesn't seem to be a solution for it yet. Please visit [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/673104](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/673104) and vote or comment to let the developers know this is a serious issue. (I know the thread there says a new bug has been created for this issue, but the link to the supposed new bug doesn't work, and a search for the new bug number turns up nothing.)

David

---

