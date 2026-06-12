---
title: "[SOLVED] linux-ubuntu-modules-2.6.24-17-generic is not configured yet"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by MilkSjeik on 2008-06-03
Hi, I'm pretty new to Ubuntu. Already had a few distro's and was looking this time for an OS that is easy to work with and keep it up-to-date. Since recently I have less computer time to spend, so that's why I switched on the laptop to Ubuntu 8.04. Install and hardware recognition was perfect.

Now since a few days I have upgrade problems. Already tried to find a solutions on these forums, but didn't find anything (yet) that looked the same.

```
Setting up xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.13-18.41) ...
 * Starting atieventsd
   ...done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

```

How do I configure "Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet."? Every time updates/installations happen, it ends with this same error message.

---

### Post by EXCiD3 on 2008-06-03
Well, it says "No space left on device" are you out of hard drive space? Since this has to do with the kernel packages, make sure your /boot partition is large enough.

---

### Post by wootah on 2008-06-03
> **MilkSjeik said:**
> Hi, I'm pretty new to Ubuntu. Already had a few distro's and was looking this time for an OS that is easy to work with and keep it up-to-date. Since recently I have less computer time to spend, so that's why I switched on the laptop to Ubuntu 8.04. Install and hardware recognition was perfect.

Now since a few days I have upgrade problems. Already tried to find a solutions on these forums, but didn't find anything (yet) that looked the same.

```
Setting up xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.13-18.41) ...
 * Starting atieventsd
   ...done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

** gzip: stdout: No space left on device**
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

```How do I configure "Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet."? Every time updates/installations happen, it ends with this same error message.

Looks like you ran out of space :(

EDIT: Ahhh EXCiD3 beat me to it :)

---

### Post by EXCiD3 on 2008-06-03
> **wootah said:**
> Looks like you ran out of space :(

EDIT: Ahhh EXCiD3 beat me to it :)

hehe! better fighting to answer questions than fighting to get responses! :popcorn:

---

### Post by MilkSjeik on 2008-06-03
> **EXCiD3 said:**
> Well, it says "No space left on device" are you out of hard drive space? Since this has to do with the kernel packages, make sure your /boot partition is large enough.

Easy answer... Makes sence. I'll see what I can do about it :)

---

### Post by EXCiD3 on 2008-06-03
Just use GParted to resize your partitions if you have a separate /boot. Simple as that! :) Otherwise just free up some space and you should be good.

---

### Post by wootah on 2008-06-03
> **EXCiD3 said:**
> hehe! better fighting to answer questions than fighting to get responses! :popcorn:
And this is why I love this community :D

PS: To the op: if this helps, don't forget to come back and mark the thread as solved (The link 'Thread Tools' -> Mark as Solved) and thank the people that helped :)

---

### Post by MilkSjeik on 2008-06-05
> **wootah said:**
> And this is why I love this community :D

PS: To the op: if this helps, don't forget to come back and mark the thread as solved (The link 'Thread Tools' -> Mark as Solved) and thank the people that helped :)

Ok thanks all ;-)
I've deleted manually some old back-ups and it helped. So now I'll give it a try with GParted to resize! That will save me from another fresh install.

---

### Post by EXCiD3 on 2008-06-05
lol i think he meant for you to click the Thanks button (the blue medal) ;) Helps so that people with the same problem can find the answers quickly.

i remember the good old days when something broke...fix with a reinstall :) after screwing it up enough times and wasting DAYS worth on the forums you can get pretty good at fixing things haha

---

### Post by goofatyerservice on 2008-06-25
I know this is solved but I need to ask, because I'm having the problem

Linux n00b here...


Do I need the previous kernel files? Hopefully that's what these are:
(Ubuntu Studio)
initrd.img-2.6.24-18-rt 
initrd.img-2.6.24-17-rt
initrd.img-2.6.24-16-rt
initrd.img-2.6.24-18-rt.bak 
initrd.img-2.6.24-17-rt.bak
initrd.img-2.6.24-16-rt.bak
vmlinuz-2.6.24-18-rt
vmlinuz-2.6.24-17-rt
vmlinuz-2.6.24-16-rt

system.map.....config...?

---

