---
title: "ACPI -pcc probe failed"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by ray24 on 2015-04-25
Hi, I upgraded Kubuntu 14.10 to 15.04. Immediately upon boot I get the message, "1.187108 ACPI -pcc probe failed." The boot continues, but then stops. If I boot into the restore mode, have Kubuntu check and repair all files, I can then continue the boot normally, and all is well.

Any way to stop this?

Thanks, Ray

---

### Post by dino99 on 2015-04-25
that is a new kernel feature comment; so your mobo does not support it; nothing to worry about, take it as simple info.

---

### Post by ray24 on 2015-04-25
Unfortunately it is more than simple info; my pc will not boot into Kubuntu unless I repeat all the steps above. I need for it to boot correctly without having to repair all the files each time I turn on my pc.

---

### Post by dino99 on 2015-04-25
it cant be caused by that pcc thing
glance at your logs (journalctl) to know what goes wrong (red lines into journalctl, but again ppc is not to blame)

---

### Post by ray24 on 2015-04-25
Hi, thanks for that info. I'm not an expert in Ubuntu. How do I access the journalctl? Also, I cannot install Clam, which appeared to be the only failure during the upgrade. I uninstalled it then tried to reinstall it, but could not. It says a file doesn't exist (sorry, I'm at a different pc and don't remember what file it was). But I checked, and the file does exist. In any case, I cannot boot correctly even after uninstalling Clam.

---

### Post by dino99 on 2015-04-25
i'm not a kubuntu user as it have more issues still not fixed compared to ubuntu; and both the qt5 version and plasma are quite new, so expected problems.

from a terminal: sudo journalctl

---

### Post by ray24 on 2015-04-25
Thank you for your help. I'll check the file ASAP to see if I can find (and hopefully fix) the problem.

---

### Post by matt_symes on 2015-04-25
Hi

> ACPI -ppc probe failed

As dino99 said, this is a new kernel feature in 3.19 kernels and higher. It *should *not cause you any problem.

The kernel is probing ACPI, looking for the "Platforms communication channel" interface. This is a new ACPI interface and not much hardware currently supports it. 

I get this warning under the 4.0 kernel as ACPI on this laptop also does not support it.

```

matthew-laptop:/home/matthew:2 % uname -r && dmesg | grep PCC
4.0.0-040000-generic
[    0.716077] PCCT header not found.
matthew-laptop:/home/matthew:2 % 
```

For those so inclined, the acpi5.0a specification can be downloaded from the website acpi.info, however, as always, drink plenty of water as it's a pretty dry read.

Kind regards

---

### Post by parka2 on 2015-07-28
i change the drive of my videocard to a privative drive [https://drive.google.com/file/d/0B4AhGcDjm52HNjlvd2RpWHJpaTQ/view?usp=sharing](https://drive.google.com/file/d/0B4AhGcDjm52HNjlvd2RpWHJpaTQ/view?usp=sharing)
Now the problem is fixed

---

