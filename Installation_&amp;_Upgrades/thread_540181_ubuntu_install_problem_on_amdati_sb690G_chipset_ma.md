---
title: "ubuntu install problem on amd/ati sb690G chipset mainboard"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by localhost_ro on 2007-09-01
Hello, I'm sort of a linux newbie. Here's my problem: i wanted to install ubuntu feisty (both x64 and x86 editions, both livecd and alternate editions). The boot freezes right after loading isolinux and the kernel, without any error messages. My mainboard (which I suspect being guilty for this problem) is an ASUS M2A-VM, with a amd 690G/SB600 chipset. I would also like to mention that i have had this problem with other linux distros, but NOT with the debian 4.0 etch, which I guess ubuntu feisty is based on. I have searched some linux support forums regarding problems with the amd/ati 690g/sb600/x1250 onboard video adapter, but I have found nothing. So, if there's anyone having similar problems who has an idea what is this all about (i also suspect some boot parameters having to be sent, I tried noacpi and noapic, but still didn't work), I would appreciate any feedback.

---

### Post by vesper8 on 2007-09-25
I have the same Mobo and the same problems!! Anyone have a solution for installing on this motherboard ??

---

### Post by tbdombrosky on 2007-10-05
> **vesper8 said:**
> I have the same Mobo and the same problems!! Anyone have a solution for installing on this motherboard ??

Try disabling HPET in the bios.

-Tom

---

### Post by makeyre on 2007-11-11
A lot of people seem to be having this problem...and I still haven't seen a good fix for it.  I really want to get Ubuntu working on this machine, and every component in it is newly purchased; there should be no reason why it won't work.  The mainboard and CPU have been out for at least 6 months now - is there anything I can do to help get support working for this mainboard/CPU?  For example, any commands you'd like to see the output of that could help diagnose the problem?

My main topic on this problem:

[http://ubuntuforums.org/showthread.php?t=609491](http://ubuntuforums.org/showthread.php?t=609491)

---

