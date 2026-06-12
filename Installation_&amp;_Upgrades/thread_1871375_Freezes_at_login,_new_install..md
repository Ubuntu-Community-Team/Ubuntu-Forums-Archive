---
title: "Freezes at login, new install."
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Monster_user on 2011-10-28
I've got a problem with Kubuntu 11.

I just wiped my old Kubuntu partition, and then installed a clean load of Kubuntu 11.10.

Now I can't login to my desktop. It asks for a password, starts to load, then gets freezes.

System:
Sony Vaio
nForce 220 motherboard
Athlon XP 2400+
1GB DDR
160gb EIDE (13GB partition for Kubuntu)
USB wifi adapter.
Nvidia Geforce 6800

Nevermind, it appears to be an OpenGL issue.

---

### Post by MAFoElffen on 2011-10-28
> **Monster_user said:**
> I've got a problem with Kubuntu 11.

I just wiped my old Kubuntu partition, and then installed a clean load of Kubuntu 11.10.

Now I can't login to my desktop. It asks for a password, starts to load, then gets freezes.

System:
Sony Vaio
nForce 220 motherboard
Athlon XP 2400+
1GB DDR
160gb EIDE (13GB partition for Kubuntu)
USB wifi adapter.
Nvidia Geforce 6800
Can you toggle to a text console? <cntrl><alt><F2>

If not look here to boot to a TTY text console temporarily:
[http://ubuntuforums.org/showpost.php?p=11383888&postcount=715](http://ubuntuforums.org/showpost.php?p=11383888&postcount=715)

Once in a tty prompt and logged in:
```
[FONT=monospace]
[/FONT]sudo rm .Xauthority* 
touch .Xauthority 
chmod 600 .Xauthority
sudo shutdown -r reboot

```
That should reset the authorities profile for X.

---

