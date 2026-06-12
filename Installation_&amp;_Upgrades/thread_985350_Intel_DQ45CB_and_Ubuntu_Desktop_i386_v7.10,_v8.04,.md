---
title: "Intel DQ45CB and Ubuntu Desktop i386 v7.10, v8.04,v8.10 installation problem"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by gtherreault on 2008-11-17
Has anyone installed ubuntu desktop 7.10, 8.04 or 8.10 on the new Intel DQ45CB motherboard?

Installation stalls near the end with this message.

Configuring apt
progess bar stuck at 82%
scanning the mirror

I've tried several times with no luck, and on the last try with v8.10 I left the installation running and after more than 30 mins, the progress bar completes in a matter of seconds and a command prompt appears with this message.

/etc/rc2.d/s98usplash: 112: chvt: No space left on device
/etc/rc2.d/s99acpi-support: line 7: usr/share/acpi-support/power-funcs: no space left on device

Installing on a Seagate 80gb sata drive and system has 2gb of ddr2 memory.

I also have an older Intel DQ35JO board and installation works without a problem, so obviously something is up with the new DQ45CB.

Any comments/help would be appreciated.

Thanks

---

### Post by gtherreault on 2008-11-17
Update for v8.04:

To start the installation process of ubuntu 8.04 on the DQ45CB, make sure the SATA Hard drive setting in the BIOS is set to AHCI and not IDE, as the installation will halt at the very beginning with a Busybox command prompt error (whatever that is).

Once I had changed SATA hard drive setting from IDE to AHCI in the BIOS I was finally able to install Ubuntu 8.04, but once system was up and running I faced another problem, onboard network card is not supported, so no network connection.

I will add an old nic to PCI slot and see if I can get network running and update the installation which might fix this problem.

---

### Post by lordCovenant on 2008-11-22
im having the same problem here when trying to install ubuntu. can't get pass 82% in configuring apt.
i really don't have any idea what seems to be causing the problem.

can anyone shed a light on this?

im on asus board intel processor pc. . .

---

### Post by gtherreault on 2008-11-22
I found the solution to this problem. Disable any special options you can in the BIOS such as TPM, VT, Power states etc. Probably these features are not properly supported by ubuntu for now, don't know exactly. It will be a trail and error to figure out which one is causing the problem.

Once you do this, Ubuntu will install without a problem. What you will face after this once installed is that the network connectivity is extremely slow (this was my case). I started the downloads of updates and it was taking forever, so I left it overnight and the next morning it was done.

After the updates, Internet was normal.

So this is my solution for now on how to install v8.10, other versions have their own problems which I have yet to figure out.

Hope this helps.

Gilles:KS

---

### Post by bejam on 2008-11-28
> **gtherreault said:**
> I found the solution to this problem. Disable any special options you can in the BIOS such as TPM, VT, Power states etc.
Am interested in using VT-d. Could you tell me if Ubuntu still boots when you re-enable this (after install and updates). Also have you had any luck using the vPro AMT interface? Thanks

---

### Post by evilempire on 2009-02-09
I'm using this board with Ubuntu 8.10 64 bit and it installed straight out. Perhaps because of the Q8200 processor not supporting the VT?

Curious to see if that helps. 

Also can any of you guys use Suspend? I can suspend the system, but it insta-reboots when you try to wake it.

---

### Post by bgood4000 on 2009-03-20
I found that unpluging the network cable allowed the install to complete to the end.

---

