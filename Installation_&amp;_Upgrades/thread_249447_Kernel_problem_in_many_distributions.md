---
title: "Kernel problem in many distributions?"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by radradish on 2006-09-02
Hi

I've got problems installing Ubuntu 6.06 on Asus laptop. During the bootup many similar disk errors appears:
```
hda task-in-initr: status=0x59 {DriveReady SeekComplete DataRequest Error}
hda task-in-initr: error 0x04 {DriveStatusError}
```
It's possible to run live linux by pressing ctrl-C, but then in gui installation process hangs up once again and there is no way to push it forward.
I guess the same issue appear during SUSE 10.1 installation, because the hd act the same way (when observing hdd led) and the installation process also hangs up (only reboot is the solution).

So far I found many similar cases with 0x04 error etc. over the internet but NO cure for it :(
The most annoying advice is to check MD5 sums of iso's... ](*,) 

I can likely draw a conclusion that some component used in these two distributions causes that problem. Kernel maybe?

It's hard to find ways to solve that problem. Even do not know what to search for with google after reading many, many posts.

Waiting for new release... :frown:

---

### Post by tseliot on 2006-09-02
It might be a problem related to the kernel.

Try Knoppix 5.0.1 and see if it works (it's a livecd).

If it does, then kernel 2.6.17 solves your problem.

---

### Post by radradish on 2006-09-05
Knoppix works fine :) I'll try with earlier versions of Ubuntu / Suse and then upgrade. That will be the easiest way. Thank you

---

