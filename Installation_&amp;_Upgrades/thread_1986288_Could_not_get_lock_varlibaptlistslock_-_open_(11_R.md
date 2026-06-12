---
title: "Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailab"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by yeehi on 2012-05-24
I have just installed Ubuntu 12.04 in VirtualBox.
I want to update the system.

This is the error message I get:

```

sudo apt-get update && sudo apt-get upgrade
 Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)

```

I have tried repeatedly but keep getting the same error message. I can reach the Internet with Firefox.

What is the problem?
What should I do?

---

### Post by kc1di on 2012-05-24
do you have software center running or synaptic. or update manager?

in any event log out and back in and see if that does it.

---

### Post by kc1di on 2012-05-24
if that does not work try these commands:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by madmalc on 2012-08-09
This worked for me - had same problem in 10.04

---

### Post by sumonbdinfo on 2013-05-29
> **kc1di said:**
> if that does not work try these commands:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

Hi,
Thank you for this. I was faced this problem and your way help me for fix this :)

---

### Post by gideonmaina on 2013-06-04
yes the solution to clearing the lock is the one that got me out !

---

### Post by Ashiq_Irphan on 2013-09-03
> **kc1di said:**
> if that does not work try these commands:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

Thanks, this one worked for me

---

### Post by kinetonat on 2013-09-15
> **Ashiq_Irphan said:**
> Thanks, this one worked for me

I tried this command in the terminal and thought it might be working as it began to many packages.

However I get this further message:

Fetched 19.8 MB in 38s (520 kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

or if i try again with apt get-update


E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ap@ap-HP-Compaq-dc7600-Convertible-Minitower:~$ 

It seems to have been happening since i went in search of software in the software centre (12.04 LTS), which could not be found, that the searching just won't stop. I have tried to kill the software centre, log out, and reboot but constantly the 'progress arrows' still show a search continuing.

This is shown also in update manager. ['Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.']

---

### Post by kinetonat on 2013-09-15
just tried this command:
sudo rm /var/lib/dpkg/lock

And now have something new going on - as pictured

it just hung there.

In terminal ic an see the problem as:

Fetched 19.8 MB in 1min 48s (183 kB/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
ap@ap-HP-Compaq-dc7600-Convertible-Minitower:~$ sudo dpkg --configure -a
Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
 * Starting NTP server ntpd              [B]                                       *** glibc detected *** lockfile-create: free(): invalid next size (fast): 0x08525008 ***
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x08525048 **[/B]*

Can i get any help?

---

### Post by ibjsb4 on 2013-09-15
Just do what it says:

```
sudo dpkg --configure -a
```

But this is a partial upgrade so don't expect wonders.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by kinetonat on 2013-09-16
I typed that in (it is there in the caption) and there followed the text (in bold).

In software centre I have tried to remove ntp, but it just hangs ....'waiting', and will not uninstall

---

### Post by coffeecat on 2013-09-16
Since the previous poster has now opened their own thread for the problem they describe in this thread, I've closed this old thread to prevent further necromancy and dilution of community effort.

---

