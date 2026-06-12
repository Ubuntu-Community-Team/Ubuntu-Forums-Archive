---
title: "Unexpected: Error 1962: no operating system found."
date: 2018-05-23
forum: Installation &amp; Upgrades
---

### Post by trasan on 2018-05-23
Hi, 

Am running 16.04 on a older Lenovo ThinkCenter. 
Have had no real issues until now.

Suddenly when starting the computer after it was shutdown for 5 days, I get the Error 1962: no operating system found.  
Have been now been playing around a bit with 
- UEFI/Legacy mode
- boot repair
- exchanging the SSD drive to another one and installing 18.04

but I get nowhere, still error 1962

 any support highly appreciated!

---

### Post by westie457 on 2018-05-23
Hello, that error message is probably specific to the Lenovo family of machines.
Here are two links for possible solutions.

[https://howtoremove.guide/error-1962-lenovo-no-operating-system-found-fix/](https://howtoremove.guide/error-1962-lenovo-no-operating-system-found-fix/)

Hopefully the first one will fix it, at least for a while. If not use the second link.

[https://forums.lenovo.com/t5/Lenovo-All-In-One-AIO-Desktops/ERROR-CODE-1962-NO-OPERATING-SYSTEM-FOUND/td-p/1034873](https://forums.lenovo.com/t5/Lenovo-All-In-One-AIO-Desktops/ERROR-CODE-1962-NO-OPERATING-SYSTEM-FOUND/td-p/1034873)

Here hopefully you can swap cables around.

---

### Post by trasan on 2018-05-24
Hi,
Thanks for helping out.
Unfortunate non of those actions worked. Still same error.

I tried to put in the original HD with windows, changed BIOS to legacy boot, and windows booted. 
So the problem seems to be connected to:  lenovo+UEFI+linux.

As I only will have linux on the HD, my plan now is to a new installation (18.04) with legacy boot (so adding the 1 MB boot partition). 
or I get deeper with UEFI and see if I get get the boot to work. I had similar problem with another lenovo computer some time ago. Just have forgotten how I solved it back then...

---

### Post by gabriellak on 2018-06-05
Hello trasan,

I was dealing with the same issue several months ago. Have you tried changing boot options? I think that it was the one that helped me. Also, as I read in [this guide]("https://ugetfix.com/ask/how-to-fix-error-code-1962-no-operating-system-found/"), running Windows diagnostic tool or enabling System Restore Point can help. 
This error seems to rule Lenovo forum :D [https://forums.lenovo.com/t5/ThinkCentre-A-E-M-S-Series/Lenovo-Thinkcentre-1962-No-operating-system-found/td-p/4004056](https://forums.lenovo.com/t5/ThinkCentre-A-E-M-S-Series/Lenovo-Thinkcentre-1962-No-operating-system-found/td-p/4004056)

---

### Post by andy-marine-01 on 2018-10-01
The appearances of 'no operating system found' error while using PC is a clear indication that your PC is contaminated with a System malware. Well, need not to be panic because there is an expert solution through which you can easily resolve such an issue. Visit - [https://www.removemalwarevirus.com/delete-virus-found-pop-up-from-windows-machine-remove-malware-virus](https://www.removemalwarevirus.com/delete-virus-found-pop-up-from-windows-machine-remove-malware-virus)

---

### Post by oldfred on 2018-10-01
Doubt if malware.
No operating system found, is almost always wrong boot mode. You have UEFI with Secure Boot, UEFI and CSM/Legacy/BIOS as choices and if system boot mode does not match install, it gives that type of error.

See this.         [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

