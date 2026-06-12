---
title: "[plymouth] egg vs. chicken problem"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kerneloftruth on 2010-04-04
Hi guys,

after installation of a clean Lucid Beta1 amd64 from alternate CD & an dist-upgrade

I first got an error message about out-dated or not matching libplymouth (don't know the exact term anymore)

so I selected those two libraries for upgrade in synaptics and it continued to install the updates

unfortunately there are missing dependencies for plymouth:

> Setting up initramfs-tools (0.92bubuntu67) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-16-generic
grep: /lib/plymouth/themes/text.plymouth: No such file or directory
grep: /lib/plymouth/themes/default.plymouth: No such file or directory
cpio: ./lib/plymouth/.so: Cannot stat: No such file or directory
cpio: ./lib/plymouth/label.so: Cannot stat: No such file or directory
cpio: ./lib/plymouth/themes/default.plymouth: Cannot stat: No such file or directory
cpio: ./lib/plymouth/themes/text.plymouth: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-16-generic
dpkg: subprocess installed post-installation script returned error exit status 1

each time it bails out at that point

dpkg --configure -a 

doesn't help since it errors at that point again thus leaving the apt-get / synaptic database in a inconsistent (?) state which I seemingly can't leave


help please ](*,)

is a new installation and/or waiting for Beta2 with fixed dependencies the only option ?

many thanks in advance :KS


P.S.: I'll shutdown / restart the system soon so perhaps I'll be forced to re-install anyways ...

---

### Post by kerneloftruth on 2010-04-04
well the fix for now was to remove the offending update (queue):

```
sudo rm -rf /var/lib/dpkg/updates/*
```

and install the missing 

plymouth-theme-text

plymouth-theme-ubuntu-text

plymouth-theme-ubuntu-logo (if needed)

from the console or synaptic :lolflag:

---

