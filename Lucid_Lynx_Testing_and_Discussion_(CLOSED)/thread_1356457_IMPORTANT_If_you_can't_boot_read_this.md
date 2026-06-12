---
title: "IMPORTANT: If you can't boot read this"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gnomeuser on 2009-12-16
And whatever you do NOT use dkms 2.1.1.0-0ubuntu3, as this version has a missing then statement in the dkms_installer which results in crippling your machine on bootup. 

There is recovery to be made should you have made the mistake of using the damaged previous version. Boot a LiveCD and edit /usr/lib/dkms/dkms_autoinstaller

Find 

if [ -L /vmlinuz -a -e /vmlinuz ]
then <-- insert then here
linktarget="$(basename "$(readlink /vmlinuz)")"

save and reboot your machine.

I repeat, using dkms 2.1.1.0-0ubuntu3 will screw you over, it's dangerous. Use dkms 2.1.1.0-0ubuntu5 or higher and be saved the horror.

---

### Post by LKjell on 2009-12-16
Weird I do not have that file.

---

### Post by philinux on 2009-12-16
If I've removed the nvidia driver is this why I've not got this file too?

---

### Post by dino99 on 2009-12-16
well,

i've updated / upgraded lucid from outside, and have seen this warning "failed to setup dbus".
Try to boot again: that time, it boot but in low resolution. Looking at drivers, no one is active.
Driver activation: 195, 190 failed; only 185 can be activated.
Shutdown & reboot: again boot failed.

Don't know which dkms is used actualy, this is with the last in repo. :(

---

### Post by gnomeuser on 2009-12-16
I apologize, I got the filename wrong, it has been corrected in the parent post.

---

### Post by VMC on 2009-12-16
> **LKjell said:**
> Weird I do not have that file.

It's for developers or advance linux users. I don't have it either and don't see a need for it myself.

Originally written by Dell engineers. Here's the [wiki]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support").

---

### Post by darco on 2009-12-16
Though this is limited to nvidia drivers, I have always used this script from sdennie and have never had an issue when updating to a new kernel.

[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)




darco

---

### Post by tad1073 on 2009-12-16
I upgraded from 9.10 to 10.04, added this ppa [https://launchpad.net/~sevenmachines/+archive/nvidia+1](https://launchpad.net/~sevenmachines/+archive/nvidia+1)  , removed all instances of nvidia drivers, installed the 195.22 driver, opened up nvidia-settings and was promted to run the command  nvidia-xconfig as root, rebooted and everything was good.

---

### Post by andrewsomething on 2009-12-16
> **dino99 said:**
> i've updated / upgraded lucid from outside, and have seen this warning "failed to setup dbus".
Try to boot again: that time, it boot but in low resolution. Looking at drivers, no one is active.
Driver activation: 195, 190 failed; only 185 can be activated.
Shutdown & reboot: again boot failed.

I think that's a different issue. See: [https://bugs.edge.launchpad.net/ubuntu/+source/dbus/+bug/441100](https://bugs.edge.launchpad.net/ubuntu/+source/dbus/+bug/441100)

Updating dbus in a chroot environment won't work, and often ends up leaving many other packages unconfigured.

Boot into you Lucid install and select recovery mode from GRUB. Select netroot from the recovery menu. Run "dpkg --configure -a" to setup any unconfigured packages. Then run an "apt-get update && apt-get upgrade" After rebooting you should be fine.

This has always worked for me. In the future, just don't try to do any upgrades of dbus through a chroot.

---

### Post by dino99 on 2009-12-18
> **tad1073 said:**
> I upgraded from 9.10 to 10.04, added this ppa [https://launchpad.net/~sevenmachines/+archive/nvidia+1](https://launchpad.net/~sevenmachines/+archive/nvidia+1)  , removed all instances of nvidia drivers, installed the 195.22 driver, opened up nvidia-settings and was promted to run the command  nvidia-xconfig as root, rebooted and everything was good.

Great, thanks

---

