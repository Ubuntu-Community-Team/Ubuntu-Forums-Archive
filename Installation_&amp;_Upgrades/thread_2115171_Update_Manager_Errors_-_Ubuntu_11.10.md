---
title: "Update Manager Errors - Ubuntu 11.10"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by raindogxx on 2013-02-12
Hello,

After relocating from the US to Ireland I have encountered the following error message when attempting to update my system using Update Manager:


"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/debian.slimdevices.com_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

Minus the smiley. 

Any advise would be greatly appreciated.

---

### Post by matt_symes on 2013-02-12
Hi
 
Opoen a terminal and type
 
 ```
sudo rm /var/lib/apt/lists/debian.slimdevices.com_dists_stable_main_binary-i386_Packages
```
 
Enter your password. It will not be echoed to the screen.  Then type
 
```
 
sudo apt-get update

```
 
Hopefully that will fix it for you.
 
Kind regards

---

### Post by raindogxx on 2013-02-12
That solved my problem. 

Thanks very much for your help.

---

### Post by raindogxx on 2013-02-18
I prematurely listed this as solved as I did receive some updates after making the changes recommended by matt_symes.

Since those updates I've been getting the following error when I run update manager:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/debian.slimdevices.com_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"


I also get these errors when I run Synaptic Package Manager:

"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/debian.slimdevices.com_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."


Can anyone point me in the right direction? Last time I was able to get Package Manager to open it said the definitions were last updated 276 days ago. 

Thanks

---

### Post by mörgæs on 2013-02-18
[http://ubuntuforums.org/showthread.php?t=2078996](http://ubuntuforums.org/showthread.php?t=2078996)

Googling the error message is normally the fastest way of getting a solution.

Besides, 11.10 is soon running out of support. You should consider a fresh install of 12.10.

---

