---
title: "vertical blue line crash, video card?"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by ink251 on 2006-10-01
I tried to install Ubuntu 6.06 from the i386 cd and it boots into X then randomly becomes unresponsive and vertical blue lines appear about an inch apart.  I got ubuntu working by using the "alternative" install then getting into safe mode with grub and doing a "startx" from the command line.  Any ideas on what might be messing up the install?

stats:
GIGABYTE GA-K8VM800M motherboard with onboard "S3 Graphics UniChrome Pro IGP" and an AMD Athlon 64 3400+ Venice 2.4GHz

---

### Post by orb9220 on 2006-10-02
> onboard "S3 Graphics UniChrome Pro IGP"

is probally your problem and you need to install the driver for it.
Do a search on s3 and see what pops up. I'll keep an eye and get back to you if I find anything.

---

### Post by ink251 on 2006-10-02
Well I tried out 3 different graphics cards and I am getting the same problem (minus the blue lines).  I logged into the recovery console on my alternative install and used sysv-rc-conf to disable some of the modules.  After this the alternative install worked fine.  The only problem is the alternative install does not autodetect usb drives/hard drives etc.  Any help with either fixing the alternative install or tips to install the normal cd with modules would be appreciated.

---

