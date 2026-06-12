---
title: "X server problem after doing upgrades with NVIDIA (low graphics mode)"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by thebeefytaco on 2008-08-06
I've had this problem since edgy eft and I think it's time I've posted this here.

Currently I'm running 8.04 64 bit, but I have this problem on 32 bit as well. On a clean install everything works fine, but after I do the first upgrade and reboot I get the low graphics mode error thing. However if I stop gdm and reinstall my drivers it works fine.
I have a 7600 GS.
I'm trying to figure out what in the upgrade causes this and how to fix this, I hate having to reinstall my drivers after every boot.

If you need the output of anything let me know and I'll get it here pretty quickly.

Thanks in advance.
Edit: I have a dual monitor setup.

---

### Post by thebeefytaco on 2008-08-09
bump
please I need help with this
should I be posting in a different section?

---

### Post by Pumalite on 2008-08-09
If you install your drivers 'the old fashion way'; you have to reinstall your driver after each kernel upgrade.

---

### Post by PmDematagoda on 2008-08-09
Try this:-
1) Open a modules file for editing with:-
```
sudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nvidia_new nv"
```
and save the file.

Then reboot the PC and see if the Nvidia module now works properly.

---

