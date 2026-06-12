---
title: "kernel upgrade errors after fresh install"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by spinsane on 2010-07-23
Bah. I just activated backports and partners and I got it.

-------------------

I just bought a newish asus x83vm-x2 and am dual-booting seven and lucid lynx. On my last two computers I had migrated completely to Ubuntu, but windows 7 has a few compelling features...

Anyways- I'm having issues upgrading the kernel on my fresh install of ubuntu (not that it matters, but I installed via jump drive).

In update manager, the kernel upgrades are grayed out.

In synaptic, I get these (current kernel version is 2.6.32.21.22 btw)-
```
linux-generic:
     Depends: linux-image-generic (=2.6.32.24.25) but 2.6.32.21.22 is to be installed
linux-image-generic:
     Depends: linux-image-2.6.32-24-generic  but it is not installable
linux-headers-generic:
     Depends: linux-headers-2.6.32-24-generic  but it is not installable
```I tried progressively installing kernel updates through each version, but after 2.6.32.23 I couldn't get any further- went ahead and refreshened my install...

It appears as thought "linux-image-2.6.32-24-generic" is not in the repository... but if that were the case, you'd think that my machine would just auto-update to an earlier version. IDK- I'm confuddled.

In apt-get I get this-
```
The following packages have been kept back:
linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by mark.altern on 2010-07-23
Exactly the same problem here, this is after a fresh install a few days ago and I didn't mess up with anything. my kernel is in:
```
2.6.32-23-generic #37-Ubuntu
```
and it seems to get stuck. The new kernel update is grayed out in update-manager, and while I do it by hand:
```
sudo apt-get install linux-generic linux-headers-generic linux-image-generic 
```
I only get the following unmet dependency error:
```
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.32-24-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.32-24-generic but it is not installable
E: Broken packages

```

I am waiting for this kernel update for quite a while, what should I do?

---

### Post by Cavsfan on 2010-07-23
I have the same thing. It must be held back temporarily. It will probably be available shortly.

---

### Post by keep-on-smiling on 2010-07-23
Hello

...and yep, same issue - as I remember this does happen from time to time. Wait a bit (as in a day or so) and try again. This happened to me on a 32-bit Ubuntu with no kernel tweaking.

---

### Post by Elmer Fudd on 2010-07-23
Not a fresh install here, but same problem. No 2.6.32-24 so the -25 will not install. Glad to see it's not just me.

Acer 7736z
Ubuntu 10.04
2.6.32-23

---

### Post by Cavsfan on 2010-07-23
"sudo uname -a" says I have this kernel - 2.6.32-23-generic

I was told to use this method to update instead of Update Manager:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade (this gets the kernel if it is available)

Is this the way you all get updates?

I use Update Manager to see if there are any available and then close it and open a terminal and enter the above commands.

The kernel still is grayed out as I check every once in a while.

---

### Post by mallaigh on 2010-07-23
This problem appears to have been fixed.  It looks they rolled back the version of the kernel on the repository.

edit: I was trying to install from the Ubuntu mini disc (it downloads the kernel) and when it was downloading 2.6.32-25 it would fail to install it, but I just finished installing Ubuntu and my kernel version is 2.6.32-24.

---

### Post by sdaau on 2010-07-23
Same here - let's hope it gets settled in couple of days...

---

### Post by mark.altern on 2010-07-23
It is fixed now!

cheers!

---

### Post by jflaker on 2010-07-23
Still showing on my side:
```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Version is: Kernel Linux 2.6.32-23-generic

---

### Post by mark.altern on 2010-07-23
I am US, what country are you from? I guess the time for different servers to be completely snyced is different, you should be able to update in a short while. 

best,

---

### Post by jflaker on 2010-07-23
Interesting....fixed now.  I am on the cornell.edu mirror.  It probably took a little bit to sync up.

---

