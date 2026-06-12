---
title: "Bad upgrade 20.04LTS to 20.10"
date: 2020-11-02
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2020-11-02
I did the upgrade from 20.0 for LTS to 20.10. Desktop dual boot with windows. Boots into Ubuntu and I get to the normal screen. I see all the icons desktop etc. However when I click on anything I get a dot indicating the application is open, however nothing on the screen. Then if I click a couple more, it then goes back out to the login screen. Or it will just flash purple over and over until it shuts off completely.

Rebooted a couple times, no change.

---

### Post by jdeca57 on 2020-11-02
The information provided doesn't allow a concrete answer but if I were in your situation I would make a USB bootable medium from the Windows side and reinstall. Personally I had a good experience with Kubuntu 20.04 to 20.10 but that is of course no help.

---

### Post by claven123 on 2020-11-02
I can provide more information, or details.  It’s quite odd.

I went into recovery mode from the grub menu and we’re in the recovery, then did a full normal boot after that and it worked as it should, Then after I rebooted it went back to the same behavior. I did not perform any actions while on the recovery mode, I thought about doing the repair broken packages.

D

---

### Post by jdeca57 on 2020-11-03
Well of course you can try to solve the problem and that will be more satisfying than a reinstall but then I can add the following: your problem seems to be linked with the display manager. So go to a console ctr-alt-F2 and log in.
In text mode your system should be stable and to start with you might try:
```

systemctl status display-manager.service

```
Most likely the configuration of the display manager is the cause, in my opinion.

---

### Post by claven123 on 2020-11-04
I did the task, no change.
What do I do next?

Yes, I can reinstall if I had to.  I'd rather try to repair it if at all possible. 

Will running.... fix broken packages from the recovery menu help?

d

---

### Post by funicorn on 2020-11-07
According to what had happened, it should be related to the boot option(s) designated through Grub loader, and should be those improperly used or unused kernel modules of X display. You may want to check the relevant logs with `dmesg` to find out any abnormal kernel incidents. ```
dmesg -k |more -p
``` and especially with ```
dmesg -k -l warn |more -p
``` (or `-l /err/crit/alert/emerg`)

---

### Post by garvinrick4 on 2020-11-08
This is a suggestion:
Make a /home partition when making a partition table 
a / for the stable you were using and always leave an
open partition to install new / . Will then always have one
working stable install and one for new install. The /home partition you made
will auto put both installs using the one /home .
## Again a suggestion that has always worked well for me but vital if you are doing Ubuntu Development Release (working with unstable to bug test)

---

### Post by CelticWarrior on 2020-11-09
> [COLOR=#000000]The /home partition you made[/COLOR]
[COLOR=#000000]will auto put both installs using the one /home [/COLOR]
This is a very bad idea. /home stores user settings. You can get away with it with very similar distros but even a shared /home between Ubuntu 16.04 (Unity) and Ubuntu 18.04 or newer (Gnome) will cause problems. Even worse if different DEs based Ubuntu flavors. With fundamentally different distros this will cause caos.

---

