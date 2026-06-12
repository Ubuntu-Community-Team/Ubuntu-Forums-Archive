---
title: "nvidia install probs"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by cruicent on 2007-01-12
Hi, I recently installed ubuntu (coming from fedora) and I cant get my nvidia graphics card set up.
```
homepc@HomePC:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Err http://security.ubuntu.com edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.6-1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
After looking in the site mentioned it seems that version doesnt exist, so I googled, downloaded and installed the nvidia-glx version mentioned above ok, but when I try to enable it:
```
homepc@HomePC:~$ sudo nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

```
uname -r produces 2.6.17-10-386 which is different to nvidia-glx. So Im guessing I am supposed to wait a while for a new nvidia-glx to come out? Confused as to why synaptic would list it if it wasnt available and why it said all dependancies installed when I manually installed it.
___________________________________________

Also have 2 packages that wont upgrade, seems the same sort of errors:
```
homepc@HomePC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7702kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com edgy-security/restricted linux-restricted-modules-common 2.6.17.6-1
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted linux-restricted-modules-2.6.17-10-generic 2.6.17.6-1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.6-1_all.deb  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-10-generic_2.6.17.6-1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Thanks for any help.

---

### Post by Sqwishy on 2007-01-12
you're repositories are messed up. easiest thing to do is go search these forums for a working nvidia driver repository. make sure you reload or run sudo apt-get update before you try downloading it.

---

### Post by cruicent on 2007-01-12
Thanks, found a repo and now its installing.
What should I have ticked in Software Sources? I ticked all 6 earlier but have taken it down to the first 2. Do I need the other 3?

---

### Post by Sqwishy on 2007-01-12
I don't know. :-k I'm not using ubuntu right now so i'm not sure what they say. O_o

---

### Post by dabl on 2007-01-12
I had good luck using the "Envy" script installer for Nvidia drivers -- here's the link:

[http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)

Follow his instructions closely.  I found it worked better from one of the "real" console screens (Ctrl-Alt-F1) than from the console window in the GUI.

---

