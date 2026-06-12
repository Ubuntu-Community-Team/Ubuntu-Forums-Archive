---
title: "Grub2 Picking up old OS install"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by Digicrat on 2010-12-12
I regret not forcing Ubuntu to keep Grub1 back when I had the option .... if I even did.

I've been having issues with mythbuntu since the last few upgrades, so I decided to go for a fresh install.  Since I had a free partition (from a deleted Windows install that I moved to a dedicated box), I decided to leave the old root partition as a backup and reinstall to the new partition.  If it works, I may use dd in the future to clone the partition as an easy backup solution before upgrades.  

The install went fine ... but now GRUB2 detects both the old (now non-functional) install, as well as the new functional install.  More annoyingly than that, it shows the defunct install first in the list, with the correct install at the end.  Even odder, the correct install is auto-named with the partition name (sda5) of the old install, even though it's the one booting to the new partition (sda3)...


How can I get Grub2 to ignore the old install (or to be precise, NOT auto-detect other OS)?  Or at least show the functional install first.  

Any help would be appreciated ...

---

### Post by drs305 on 2010-12-12
All the indications are that G2 is still booting from the old install.

Unless you have renamed the scripts, the first one listed is from the controlling Grub2 partition. If you inspect /boot/grub/grub.cfg and look at the "### 10_linux section" it will confirm this suspicion.

From you new installation, run the following to transfer control to your current OS, and run update-grub to incorporate the changes. It assumes you want it on the "sda" MBR. Do NOT include the partition number.

```
sudo grub-install /dev/sda
sudo update-grub
```

That's all it takes. If you don't want to see any other OS's:
```
gksu gedit /etc/default/grub
```
Add this line:
> GRUB_DISABLE_OS_PROBER="true"
Save the file and update grub again.

---

### Post by Digicrat on 2010-12-13
That did the trick.

Thanks.

---

