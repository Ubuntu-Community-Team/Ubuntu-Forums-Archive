---
title: "Installing things always gives me following error"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by danielgrosvenor on 2010-06-04
Hi guys.  I'm very new to Linux so hopefully this problem will have an obvious solution I'm just missing.

Every time I attempt to install anything, in any way, I'm given the following error message:
[B]
E: lib32nss-mdns: subprocess installed post-installation script  returned error exit status 2
E: wine1.2: dependency problems - leaving unconfigured[/B]

I went into Synaptics Package Manager and told it to uninstall WINE in case that was what was causing the problems.  It sort of half-uninstalled-it then gave me that exact same error message.

I have two threads currently open on the forums - [adjusting laptop brightness]("http://ubuntuforums.org/showthread.php?t=1500505") and [flashing BIOS]("http://ubuntuforums.org/showthread.php?t=1501007") - and both problems hit a brick wall because of this same error message.

As I'm new to Linux I have absolutely no idea how to proceed, so would greatly appreciate any advice you experts are able to offer me. :)

---

### Post by dv3500ea on 2010-06-04
Try going to Applications -> Accessories -> Terminal
type: ```
sudo apt-get install -f
``` and press enter.
enter your password when prompted.

---

### Post by danielgrosvenor on 2010-06-04
> **dv3500ea said:**
> Try going to Applications -> Accessories -> Terminal
type: ```
sudo apt-get install -f
``` and press enter.
enter your password when prompted.

Have done so.  Here is the result (hopefully it'll make more sense to you than it does to me!)

```
dan@DansDell:~$ sudo apt-get install -f
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lib32nss-mdns (0.10-3ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing lib32nss-mdns (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of wine1.2:
 wine1.2 depends on lib32nss-mdns (>= 0.10-3); however:
  Package lib32nss-mdns is not configured yet.
dpkg: error processing wine1.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                        Errors were encountered while processing:
 lib32nss-mdns
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@DansDell:~$ 
```

---

