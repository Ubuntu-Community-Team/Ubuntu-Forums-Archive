---
title: "manually remove device driver"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Ecclesiastes on 2008-11-05
I have an Acard 6280 card on my PCI bus to attach IDE hard drives.

The correct driver for this card is AEC62XX, which lsmod shows as installed. Hardy also installs pata_artop, which doesn't work and supplants the correct driver. Gutsy didn't do this. The Hardy LiveCD doesn't do this. Knoppix 5.1.1 doesn't do this. The card and the attached drives work fine.

I have tried:

aptitude ( it doesn't show up )
'sudo modprobe -r pata_artop'
adding 'blacklist pata_artop' to modprobe.d/blacklist
adding 'install pata_artop /bin/true' to modprobe.d/blacklist
renaming the module from pata_artop.ko to pata_artop.disable

lsmod still shows it as installed.


What is loading this driver?
Where is it loading from?
HOW CAN I REMOVE THIS DRIVER?

---

### Post by Ecclesiastes on 2008-11-05
Nevermind. I got it. I hadn't done an update-initramfs -u.

---

### Post by pytheas22 on 2008-11-05
Sometimes it happens that blacklisting a module doesn't work, but it really should be unloaded if you type 'sudo modprobe -r pata_artop'.  Did you get an error message when you tried that command?  If the system doesn't want to unload pata_artop because another module depends on it, then it would tell you that and refuse to unload pata_artop until you also unload the dependent modules.

If you really can't get the module to go away using 'modprobe -r' or 'rmmod', then I guess your only other option is to manually delete the module.  If you type:
```

locate pata_artop
```

it should give you the full path to the module on your system--on mine, it's at /lib/modules/2.6.27-7-generic/kernel/drivers/ata/pata_artop.ko (there may be multiple copies of the module, one for each kernel that you have installed).  So to get rid of mine, I would type:
```

sudo rm /lib/modules/2.6.27-7-generic/kernel/drivers/ata/pata_artop.ko
``` 

However, you really should not do this unless you're certain that removing this module is not going to upset any other modules; otherwise, very bad things could happen (e.g. Ubuntu won't boot).  You may want at least to backup the module before deleting it, which you could do by typing something like:
```

cp /lib/modules/2.6.27-7-generic/kernel/drivers/ata/pata_artop.ko ~/Desktop/pata_artop.ko.BACKUP
```

---

