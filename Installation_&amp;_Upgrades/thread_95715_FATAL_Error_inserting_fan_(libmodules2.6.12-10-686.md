---
title: "FATAL: Error inserting fan (/lib/modules/2.6.12-10-686/kernel/drivers/acpifan.k o): N"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by darkrad on 2005-11-27
```
FATAL: Error inserting fan (/lib/modules/2.6.12-10-686/kernel/drivers/acpi/fan.k o): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-10-686/kernel/drivers/acpi/thermal.ko): No such device
```

After upgrading from hoary to breezy i got those 2 error messages. I notice the errors when i stop KDM and enter in a shell with alt ctrl f1. i see those 2 errors that probably are thrown in boot sequence.
Since i'm having problem installing Nvidia drivers (i used the tutorial: [https://wiki.ubuntu.com/NvidiaManual](https://wiki.ubuntu.com/NvidiaManual) (obviously downloading the right packages (breezy version))), that is the sequence boot hang on nvidia splash screen (i tried already the "no logo" option), probably those errors have anything to do with it: if graphic drivers are set as "nv" then no problem, if they're set as "nvidia" then boot hang on nvidia splash screen.
Dunno if the fatal erros are linked to this grpahic problem, but i just gave as much info i could to get the think fixed. Thanks in advance for any possible help.
bye

---

### Post by cyberbear on 2005-11-29
I am also experiencing these errors. I see them during the boot sequence. The computer seems to run just fine despite the erros. I would like to find the cause and correct it if possible.

Thanks.
Ron Bellomo

---

### Post by jrkrideau on 2005-12-24
[QUOTE=darkrad]```
FATAL: Error inserting fan (/lib/modules/2.6.12-10-686/kernel/drivers/acpi/fan.k o): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-10-686/kernel/drivers/acpi/thermal.ko): No such device
```

[/QUOTE] We have run into the same errors.  First we get a "Unable to find RSDP" statement and then the same two errors appear. 

Ubuntu Breeezy seems to go on  to install and we get a request for the User Id and password etc and we then get a $ prompt.  However we have no idea where to go from there.  I have pretty well forgotten my old Unix commands.  

I was wondering if anyone has found a solution about this or is there any way to see if we can invoke Gnome?  It is a real hassle to have to re-install Windows in order to get back net access.
Thanks and Merry Christmas.

---

