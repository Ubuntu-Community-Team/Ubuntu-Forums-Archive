---
title: "Grub2 with multiple ubuntu partitions"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by kmand on 2015-05-30
I have two versions of ubuntu one on sdb1 the other on sdb2. When the computer boots it gets grub.cfg from /boot on sdb1.
When I run on sdb2 and update its kernel, it updates /boot on sdb2, so I don't get the entry for the new kernel when I boot the machine.

How do I get the two versions to use one /boot?

---

### Post by Dennis N on 2015-05-30
> **kmand said:**
> I have two versions of ubuntu one on sdb1 the other on sdb2. When the computer boots it gets grub.cfg from /boot on sdb1.
When I run on sdb2 and update its kernel, it updates /boot on sdb2, so I don't get the entry for the new kernel when I boot the machine.

How do I get the two versions to use one /boot?

The answer is to use custom menus. Without them, you will need to run update-grub from the OS on sdb1 every time another OS upgrades the kernel. You can imagine the problem if you have 10 OS installs on your disk. Here is the guide I recommend to create custom menus that have permanent entries that need no upgrading.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

It requires a bit of study but it is well worth it. This post in a similar thread has more details:

[http://ubuntuforums.org/showthread.php?t=2277577&p=13282374#post13282374](http://ubuntuforums.org/showthread.php?t=2277577&p=13282374#post13282374)

---

### Post by grahammechanical on 2015-05-30
An alternative that I use would be to load into Ubuntu on sdb1 and run

```
sudo update-grub
```

and watch it detect the kernel on sdb2.  An upgrade may include an upgrade to Grub itself and that will cause a reinstall of Grub. Now, if Ubuntu on sdb2 gets this upgrade after Ubuntu on sdb1 than Ubuntu on sdb2 will now be in charge. 

To switch back to having sdb1 in charge load into Ubuntu on sdb1 and run

```
sudo grub-install /dev/sdb
sudo update-grub
```

Regards.

---

### Post by Dennis N on 2015-05-30
Thanks for pointing this out.

We know that grub may be reinstalled when grub packages appear in the list of upgrades shown in your package manager - e.g. Software Updater, Synaptic Package Manager, apt. This rarely happens, but it does from time to time. Be alert. To keep another OS from reinstalling grub and highjacking the grub menu, I just lock the packages for the current version of grub in the offending OS before the package manager can upgrade them. Very easily done with Synaptic, which I use. Problem solved.

---

### Post by kmand on 2015-05-30
Thanks for the suggestions. In reality the version in sdb1 is an older ubuntu release kept around for regression testing and emergency recovery. Since I don't expect to be updating it (or rarely even booting it), I'm content to let it have an older menu.lst, which I can update if needed.

---

