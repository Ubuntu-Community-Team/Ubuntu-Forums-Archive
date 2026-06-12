---
title: "Upgrade leaves me with &quot;no resume image&quot;"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by CDiablo on 2008-04-24
I used the alternate cd to upgrade and I restarted and I have an error for "no resume image" followed by a whole line of numbers. I can get into a prompt but I get no GUI. I was upgrading from 7.10 and used the nvidia official driver/not nv(could that be the problem?) but everything else was pretty standard.

EDIT: the official error is:

Starting up...
Loading, please wait
usplash:Setting mode 1024x768 failed
usplash : Using mode 800x600
kinit: name_to_dev_t(/dev/disk/by-uuid/2efa9ec2-e1b7-48a8-ba1d-a24c62d42912)=da5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/2efa9ec2-e1b7-48a8-ba1d-a24c62d4912
kinit: No resume image, doing normal boot

---

### Post by Peter09 on 2008-04-24
No resume image sounds like a hibernation error. Have you tried to reboot again?

Can you get to recovery mode?

PC

---

### Post by CDiablo on 2008-04-24
Im not sure what you mean by recovery mode. Rebooting does not help. As I said I can get to a command prompt, just no GUI. I can do command line fine, but I dont know what to do.

---

### Post by Peter09 on 2008-04-24
try typing

```
startx
```

at the command prompt

PC

---

### Post by CDiablo on 2008-04-24
When doing startx it says a bunch of stuff about the nvidia driver

"Failed to initialize the NVIDIA kernel module Please ensure that there is a supported NVIDIA gpu in this system, and that NVIDIA device files have been createde properly.
**Aborting**
Error API mismatch, the NVIDIA kernel module has version 169.12, but this NVIDIA driver component has version 100.14.23. Please make sure that the kernel module and all NVIDIA driver components have the same version.
Screen(s)found, but none hae a useable configuration.

"Failed to initialize the NVIDIA kernel module Please ensure that there is a supported NVIDIA gpu in this system, and that NVIDIA device files have been createde properly.

Fatal server error:
no screens found 
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): server error

---

### Post by Peter09 on 2008-04-25
try installing envyng from the command line

```
sudo apt-get install envyng-gtk
```

then run

```
envyng -t
```

it will install your nvidia driver and hopefully let you start ubuntu.

PC

---

### Post by dawynn on 2008-04-25
I believe that the "resume image" is a reference to your swap drive.  Under certain circumstances (maybe hibernate? or a system crash? I'm not sure how these get built), a resume image can be written to your swap drive that the computer can then utilize on reboot.  If it found nothing, your swap drive had nothing to restore.  

If you're getting to the command line with no trouble, I wouldn't worry about the resume image bit.  I'd look at /var/log/Xorg.0.log and work through the issues found there.  Looks like others have already started pointing you in the right direction.

---

