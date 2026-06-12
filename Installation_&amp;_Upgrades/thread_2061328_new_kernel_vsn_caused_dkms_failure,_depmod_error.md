---
title: "new kernel vsn caused dkms failure, depmod error"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2012-09-22
Did a clean install of Kubuntu 12.04 two days ago.
This evening it said there were available updates, namely kernel version 3.2.0-31.  In more detail:
```
The following NEW packages will be installed:
  linux-headers-3.2.0-31{a} [3.2.0-31.50]  linux-headers-3.2.0-31-generic{a} [3.2.0-31.50]  
  linux-image-3.2.0-31-generic{a} [3.2.0-31.50]  
The following packages will be upgraded:
  linux-generic [3.2.0.30.32 -> 3.2.0.31.34]  linux-headers-generic [3.2.0.30.32 -> 3.2.0.31.34]  
  linux-image-generic [3.2.0.30.32 -> 3.2.0.31.34]  linux-libc-dev [3.2.0-30.48 -> 3.2.0-31.50]  
The following packages are SUGGESTED but will NOT be installed:
  fdutils  linux-source-3.2.0  linux-tools  
4 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
```I did the update via
```
sudo aptitude -v -V safe-upgrade
```and received the error:
```
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
```The full output is attached to this post.

Being worried, before rebooting I did 
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall  linux-headers-3.2.0-31  linux-headers-3.2.0-31-generic    linux-image-3.2.0-31-generic
```I then rebooted and system seems to be fine for the moment.

However i am quite worried that there is something wrong deep in the system and it wil eventually show up. What is the cause of this and what does it mean?

[this machine is a Dell Precision 670 with Nvidia Quadro FX 1400 graphics card, running NVidia drivers.  I am testing 12.04 so not too much else installed on it yet.]

---

### Post by PhillyKingston on 2012-09-22
I had similar problems, Firefox had stated that it couldn't start, so I rebooted, not realizing this had happened.  Now the system doesn't boot.  Any thoughts on recovery?

---

### Post by undecidable on 2012-09-22
The problem in this thread is that the new kernel vsn caused dkms install failure, due to a depmod error.
a.  the problem is with is with 12.04 only
b.  the system  does boot
c.  and firefox is not part of the problem.

Did you have the error:
   DKMS: Install Failed (depmod problems)  ?
if not, it is not a similar problem.

---

### Post by VirgilMachine on 2013-08-24
Here's my sequence of events.  ubuntu 12.04 vm running on 12.04 host (both 64-bit).

Got the "Not all upgrades can be installed message."  

Did 
```
sudo apt-get update
sudo apt-get upgrade sudo apt-get install linux-generic linux-headers-generic linux-image-generic
```

Got the Error! Problems with depmod blah blah messages as described above.

Not knowing if this was going to cause problems on reboot, I researched and came across this thread.  

Followed the steps above to fix/clean/update/reinstall (mine was 3.2.0.52 kernal)--no depmod errors.

Rebooted and all is well.

---

### Post by undecidable on 2013-08-26
As it was for me.  Have now been using 12.04 for a year and 4 days.

---

