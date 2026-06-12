---
title: "badly broken package"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by bbc4 on 2010-02-24
I recently attempted to install snort through synaptic and when I tried the package broke.  Now I cannot use synaptic to update or install other packages.  I have tried apt-get -f install , apt-get clean, apt-get autoremove, and apt-get -f autoremove .  here is the output from attempting a force install of the package. 

b@Bbox:/etc$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up snort (2.8.4.1-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing snort (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
b@Bbox:/etc$ 

any help would be very appreciated.

---

### Post by n0dix on 2010-02-24
```
sudo dpkg --force all --remove
```

---

### Post by bbc4 on 2010-02-25
No dice.  Returns the exact same error as previously stated.

---

### Post by booshire on 2010-02-25
> **bbc4 said:**
> No dice.  Returns the exact same error as previously stated.

how about this?

$ sudo apt-get purge snort

---

### Post by bbc4 on 2010-02-27
That didn't work either.  Is there any other information that I can post to make this easier?

---

