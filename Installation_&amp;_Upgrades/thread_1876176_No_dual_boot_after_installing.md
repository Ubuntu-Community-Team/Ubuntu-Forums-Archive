---
title: "No dual boot after installing"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2011-11-05
I've tried twice and same result, i.e. the definition of insanity.  

I have Win7-64 installed and am trying to create a dual boot with Ubuntu 11.10.  I let it auto install after telling it to install beside Win7.  It appears to install and then reboots (after saying to remove the CD) but only the Windows sign-in windows appears after the reboot.

This was done of an SSD with 40G of free space for Ubuntu and there appears to be something on the space that was originally free but no dual boot option when it boots.

????

---

### Post by raja.genupula on 2011-11-06
hold shift key for grub menu while booting going on and from there you can select ubuntu. I think may be your grub time is zero. install grub customizer (my signature) after installing it click at preference tab and then change the boot time to ten sec.:)

---

### Post by deeppow on 2011-11-06
> **raja.genupula said:**
> hold shift key for grub menu while booting going on and from there you can select ubuntu. I think may be your grub time is zero. install grub customizer (my signature) after installing it click at preference tab and then change the boot time to ten sec.:)

No, didn't enter dual boot.  Only Windows login came up.

---

### Post by raja.genupula on 2011-11-06
Hi look for grub recovery in my signature ...i am sure that gonna help you to solve the issue.

---

### Post by deeppow on 2011-11-08
The boot-repair-disk fixed the problem.  Now "no network" connection but I'll post that separate.

Thanks for the help.

---

