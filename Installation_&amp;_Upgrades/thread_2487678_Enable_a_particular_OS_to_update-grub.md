---
title: "Enable a particular OS to update-grub"
date: 2023-06-12
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2023-06-12
I have my laptop set up for UEFI boot, and it is partitioned like this:

[LIST=1]
[*]/dev/sda1 efi      (Mounted as /boot/efi)
[*]/dev/sda2 ext4   (UbuntuUnity 22.04)
[*]/dev/sda3 ext4   (Ubuntu 20.04)
[*]/dev/sda4 swap  
[*]/dev/sda5 ext4   (Mounted as /home)
[/LIST]

Both Ubuntu versions mount partitions 1 and 5 as shown in the list.

If I am running the OS on partition 2 and run update-grub after making changes to /etc/default/grub, then the next time I reboot the machine I see my changes in the boot menu as expected.  But if I run the OS on partition 3 (which was installed before the other) and make any such changes, they have no effect at all on the actual boot process.

Since the version on partition 3 is my "default" system at the moment, is there some way for me to enable it, rather than the other OS, to make changes to the grub boot menu?

---

### Post by tea for one on 2023-06-12
It looks like Ubuntu 22.04 on /dev/sda2 is controlling grub at the moment.

Boot into Ubuntu 20.04 on /dev/sda3
Open a terminal and enter:-
```
sudo grub-install /dev/sda
```
```
sudo update-grub
```
If there are errors in the terminal output, please post the command and output within code tags.
If no errors, reboot and see if your preferred grub menu appears.

---

### Post by DavidS on 2023-06-14
Thank you so much for that answer.  I now have my system set up as I want it!

---

### Post by oldfred on 2023-06-14
Note that a major update to grub, will reinstall it. 
So if 22.04 gets update, you may just have to redo the update in 20,04, if you still want it as the default.

---

### Post by Bashing-om on 2023-06-14
DavidS; Hey --

I too multi-boot 'buntus and my final solution to controlling grub is to disable /etc/grub.d/30_os-prober in my secondary systems; such then only my primary system controls booting.

[INDENT]but --- more than one way
[/INDENT]

---

