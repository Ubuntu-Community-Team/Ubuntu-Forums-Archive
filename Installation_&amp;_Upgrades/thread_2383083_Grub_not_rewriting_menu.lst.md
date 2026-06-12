---
title: "Grub not rewriting menu.lst"
date: 2018-01-20
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-01-20
I installed a new kernel and headers on Ubuntu 16.04 LTS, ran update-initramfs -c -k then ran update-grub. update-grub found the new kernel and ran without error. It did not update menu.lst. I was able to manually edit and update menu.lst. It is working now.

However I want to find out why update-grub is not updating the menu.lst. Any ideas on how to find out? I'm concerned that the next kernel update will not update properly.

---

### Post by jeremy31 on 2018-01-20
Did you install another Linux Distro since your Ubuntu install?

---

### Post by oldfred on 2018-01-20
Grub2 has been standard since about 9.10 and grub2 does not use menu.lst. Grub legacy uses menu.lst.
Did you uninstall grub 2 and install grub legacy?

Updates with grub2 should be updating grub.cfg.

Boot-Repair will not work with grub legacy. It was developed after grub2 became the standard. But Report will show configuration.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rsteinmetz70112 on 2018-01-20
This machine started out a long time ago. Since that time every component has been upgraded and the file system transfered to new hardware. It has been continuously in service and updated.  It is running legacy grub because that was the standard when the system was originally configured back around 2006.

---

### Post by yancek on 2018-01-20
As pointed out above, the update-grub script works only with Grub2 and you need to manually edit the menu.lst file if you add/change systems.

---

### Post by grahammechanical on 2018-01-20
I am sure that when the OS was upgraded to a newer version of Ubuntu (one that uses Grub 2) then legacy Grub would have been discarded in favor of Grub 2. I remember that happening on my system. It may be that menu.list was left on the system and that is why you are seeing it.

I have also found that sometimes it is useful to run the grub install command to get changes recognized.

```
sudo update-grub
sudo grub-install /dev/sda
```

If there is only one hard drive (sda). 

Regards

---

### Post by Taemojitsu on 2018-01-21
I'm trying to load an older kernel to check a bug causing a kworker thread to use lots of CPU. The problem is I can't get grub to update.

As with the first poster, update-grub changes grub.cfg, after successfully detecting recent kernels.

When I reboot, it's apparently using menu.lst. This was somehow updated because it contains the most recent kernel, but it also has a kernel that has been removed.

I'd like to either update menu.lst with existing kernels, or get my system to use grub.cfg.

My system was installed sometime in 2009. I think I have GRUB 2; the packages I have that contain 'grub' are these, all of which are version 2.02~beta3~4ubuntu7:

grub-common
grub-pc-bin
grub2-common
grub-pc
grub-gfxpayload-lists

My menu.lst also contains an old, broken Windows installation, and an "---Other---" divider.

Whether this is GRUB or GRUB 2, how do I either
1) make the old settings in menu.lst get put into /etc/default/grub or some other place where they are then used for grub.cfg, or
2) get menu.lst to update, like the first poster was asking.

If this is GRUB 2, will just deleting menu.lst cause grub.cfg to be used instead? I obviously don't want to casually do this.

The only other change I made to menu.lst was restricting it to the two most recent kernels with "# howmany=2". (I had hoped to change this to 3 and boot a 4.8 kernel to test, not realizing that my current menu.lst lists a nonexistent 4.10 kernel so it still only needs to list two kernels.)

/etc/default/grub doesn't show a 'howmany' option; is there a way to add it? If older kernels are automatically cleared now, this may not be necessary.

I updated from 16.10 to 17.04 on Jan 8, and then updated to 17.10. 17.04 added the 4.10 kernel, and 17.10 apparently removed it. I didn't reboot between the updates. menu.lst must have been updated before the 4.10 kernel was removed; how?

SOLUTION: During the upgrade, I noticed that 'grub' was being removed. I forgot this when the grub menu showed up after restarting. There was also a note about 'upgrade-from-grub-legacy', a command I didn't run. See [https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading)

So I have GRUB legacy installed on the MBR, and probably in /boot/grub. Installed packages doesn't show this. GRUB2 writes to grub.cfg because it's possible to chainload from menu.lst, probably. I need to follow the instructions to upgrade and hope it works correctly afterwards.

---

### Post by rsteinmetz70112 on 2018-01-21
> **yancek said:**
> As pointed out above, the update-grub script works only with Grub2 and you need to manually edit the menu.lst file if you add/change systems.

I don't understand the comment above to say that. But in any case it has apparently been updating menu.lsy untill the latest upgrade.

---

### Post by rsteinmetz70112 on 2018-01-21
> **grahammechanical said:**
> I am sure that when the OS was upgraded to a newer version of Ubuntu (one that uses Grub 2) then legacy Grub would have been discarded in favor of Grub 2. I remember that happening on my system. It may be that menu.list was left on the system and that is why you are seeing it.

That has not been my experience. I still have systems that use LiLO, simply because it has never been necessary to change.


> I have also found that sometimes it is useful to run the grub install command to get changes recognized.

```
sudo update-grub
sudo grub-install /dev/sda
```

If there is only one hard drive (sda). 

Regards

I'll try that. But, it was my understanding that grub install only updated the Master Boot Block but as always I may be wrong.

---

