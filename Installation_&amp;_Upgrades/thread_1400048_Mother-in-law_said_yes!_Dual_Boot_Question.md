---
title: "Mother-in-law said yes! Dual Boot Question"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2010-02-06
My mom-in-law asked me to clean up an old XP system for her to use while her primary system is sent back to HP for warranty work. I tweaked XP the best I could without reinstalling. (She doesn't have the install CDs for some of her software to be able to reinstall them.)
Her system has two hard drives. One with Windows XP Home Edition and the other has Ubuntu 9.10 on it. What we want to do is,

Make the Ubuntu HDD the master and the Windows the slave,

I want grub to stay on the slave drive so that nothing on the Windows MBR gets changed on it,

If this is possible, do I just do the wiring and then boot Ubuntu and run, ```
sudo update-grub
``` Will that work or is there something else I need to do?

Thanks,
Ronnie

---

### Post by louieb on 2010-02-06
Should work. one exception. Instead of running update-grub run **grub-mkconfig.** - Since you swapped the drives around  - may have to rebuild your device.map - grub-mkconfig runs update-grub + a few other things.
[IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

---

### Post by oldfred on 2010-02-06
I still am not sure what need to be run. But update grub just runs grub-mkconfig

My grub2
#!/bin/sh -e
exec update-grub "$@"

My update grub:
#!/bin/sh -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

I have seen:
sudo dpkg-reconfigure grub-pc
Which lists several defaults from grub and reinstalls to sdx that you select.

and:
sudo grub-mkdevicemap
or rename old device.map and it will create a new one on update-grub

---

### Post by running_rabbit07 on 2010-02-06
Cool. I appreciate the help. My main priorty is making the system to where if my in-law says she doesn't want Ubuntu, I don't have to reinstall Windows or anything like that to keep XP running. After timing start up for both OSes, I am sure she'll take the Ubuntu.

Ubuntu 9.10 boots in less than 45 seconds from hitting the power button to completely booted and idling.

Windows XP Home takes more than 4 minutes to get to the same state.

Thanx for the help.

---

