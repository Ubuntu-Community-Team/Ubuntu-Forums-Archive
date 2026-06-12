---
title: "shim-signed, the bane of my entire existence"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by MissMonicaE on 2015-09-03
ETA: I'm running Ubuntu 12.04.

Every time I go to install updates, shim-signed tries to update and always returns the same error. (I didn't copy it down, and now I'm not getting it anymore.) I ran ```
sudo apt-get -f install
``` because that was what Terminal told me to do about the unmet dependencies when I was trying to install R (still no luck on that), and I got:

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  shim-signed
The following packages will be upgraded:
  shim-signed
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/408 kB of archives.
After this operation, 65.5 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on shim (= 0.4-0ubuntu4); however:
  Version of shim on system is 0.8-0ubuntu2.
dpkg: error processing shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Well, now I'm kicking myself because shim was in my recommended updates YESTERDAY and I told it to go ahead. I read here ([https://askubuntu.com/questions/596554/is-there-a-way-to-undo-software-updates](https://askubuntu.com/questions/596554/is-there-a-way-to-undo-software-updates)) that I could undo it with Synaptic, but I don't have Synaptic and I can't install it because dependencies. I tried the third solution here ([https://askubuntu.com/questions/34888/is-there-any-way-to-roll-back-the-most-recent-upgrade](https://askubuntu.com/questions/34888/is-there-any-way-to-roll-back-the-most-recent-upgrade)) but I get
```
sudo apt-cache policy shim
shim:
  Installed: 0.8-0ubuntu2
  Candidate: 0.8-0ubuntu2
  Version table:
 *** 0.8-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
```
so it looks like 0.4 is no longer available. I have never even been able to figure out what shim-signed is for.
Does anyone know what I should do, short of throwing my laptop into the sea and joining the Amish?

---

### Post by ubfan1 on 2015-09-03
What Ubuntu release are you running?  The 0.4 version is what's on my 14.04 system.  shim-signed is just for running with secure boot enabled.  If you are not running with secure boot enabled, you don't need it, just use grubx64.efi for the UEFI bootloader.

---

### Post by MissMonicaE on 2015-09-03
Sorry, I'm on 12.04.

---

### Post by Dennis N on 2015-09-03
what do you see for **apt-cache policy shim-signed**

---

### Post by MissMonicaE on 2015-09-03
```
shim-signed:
  Installed: 1.5~12.04.1+0.4-0ubuntu4
  Candidate: 1.9~12.04.1+0.8-0ubuntu2
  Version table:
     1.9~12.04.1+0.8-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
 *** 1.5~12.04.1+0.4-0ubuntu4 0
        100 /var/lib/dpkg/status
```

---

### Post by Dennis N on 2015-09-03
Based on post #1:
```
sudo apt-cache policy shim
shim:
  Installed: 0.8-0ubuntu2
  Candidate: 0.8-0ubuntu2

```
shim-signed 1.9~12.04.1+0.8-0ubuntu2 is the one for 12.04 that depends on this version of shim, 
See: [http://packages.ubuntu.com/precise-updates/shim-signed](http://packages.ubuntu.com/precise-updates/shim-signed)
so that is what needs to be installed (same as the candidate in your last post). Did you try 
```
sudo apt-get upgrade shim-signed
```
If you want, you could first try a simulation of the upgrade to see what would happen. Note no sudo here.
```
apt-get -s upgrade shim-signed
```
Then run the command with sudo (and no -s) after you are satisfied. 
This should fix your problem.

Note: shim-signed has only 3 dependencies (see the linked web page), so if they are already on your system, it should install. You already have the right version of shim, and most likely the other two as well (grub packages).

---

### Post by MissMonicaE on 2015-09-05
I did that, and got
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 shim-signed : Depends: shim (= 0.4-0ubuntu4) but 0.8-0ubuntu2 is installed
E: Unmet dependencies. Try using -f.
```
:( so I'm still stuck.

---

