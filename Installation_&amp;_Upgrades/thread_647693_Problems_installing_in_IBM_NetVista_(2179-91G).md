---
title: "Problems installing in IBM NetVista (2179-91G)"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by thusgaard on 2007-12-22
Hi 

As mentioned above I have install problems on an old IBM NetVista, it's a iMAC inspired PC (or is it the other way around).

I've tried with Ubuntu and Xubuntu and I get similar errors. 

I get at screen full og the first 2 lines below and then I get the last 2 lines. I hope to have this machine installed by this time tomorrow. Else my dad wants me to install windows 98 on it again!!!

```
[188.989461] SQUASHFS error: sb_bread failed read block 09C298
[188.989552] SQUASHFS errer: Unable to read page, block 2709D262, size90C7
Run-init: /sbin/init: I/O error
[188.990078] Kernel panic - Not syncing! Attempted to kill init!
```

Please help me. 

The machine has 312 (??) MB og RAM. 

Kind regards J;-)

---

### Post by oldsoundguy on 2007-12-22
run a chkdisk or scandisk and have it mark the bad sectors on the drive.

---

### Post by thusgaard on 2007-12-23
How do I checkdisk/scandisk with a ubuntu Live CD?

BTW, I'm not installing, I'm trying to run the Live CD.

EDIT HERE: I have tested the Live CD, via the option in the boot menu, no errors found. I have tested RAM with the Live CD and I have run DBAN on the machine to clean the disk, DBAN found no errors.

---

### Post by thusgaard on 2007-12-23
I'm getting grey haired here. 

I disabled everything in BIOS (should have done that before posting) Now both my live CD's will boot, but instead of booting to the desktop, they boot to the logon screen, and ask for username and password. What is the username and password for a live CD (XUBUNTU or UBUNTU)

J;-)

---

### Post by thusgaard on 2007-12-23
I have done som research. 
And I now have 2 (maybe 3 old IBM systems that fail). 

There is no problem installing DSL in the SYSLINUX variant. So my Guess is that my hardware is to old to run UBUNTU/XUBUNTU, due to these systems booting with ISOLinux. How ever I have not tried the ISOLinux version of DSL and I havn't got the time now as I need to test if DSL will be OK for the intended use.

I'd still love to run UBUNTU on this hardware but it seams impossible.

J;-)

---

