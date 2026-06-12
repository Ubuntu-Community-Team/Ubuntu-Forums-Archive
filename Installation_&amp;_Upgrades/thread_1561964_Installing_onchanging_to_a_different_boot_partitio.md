---
title: "Installing on/changing to a different boot partition, over SSH?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by Picklegnome on 2010-08-26
Is there any way I can SSH to a box on which I've got xubuntu installed, install Ubuntu server (for example) on a separate partition, then change the boot partition to the fresh install? I only have SSH access.

---

### Post by Reiger on 2010-08-28
Possible but it is not going to be as clean nor as easy as it would be if you had physical access to the machine.

Anyway you could of course set up a copy installation on a machine where you *do* have physical access, then transfer it over the web to the target machine (in a single archive, using scp) and on the target machine inject it in the spare partition. Then modify the boot menu on the target machine to select your new Ubuntu server by default and reboot. 

This has quite a bit of risk of failing mainly because you cannot really verify the thing works beforehand. Also you need to have installed any drivers + SSH server on the installation before you transfer it over SSH and set up configurations properly too.

---

