---
title: "can't update installed Ubuntu 13.10 grub config from Live CD"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by paul-extraspecialbitter on 2014-06-29
I've installed Ubuntu 13.10 to my laptop but can't see the monitor on my HP Folio 13. I'm familiar with the fix, which is to edit /etc/default/grub with the "acpi_backlight=vendor" option, which I am attempting to do from my Live CD. When trying to run update-grub, however, I get the following error:

```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

```

This happens even when I try specifying the boot partition explicitly, and also when executing grub-mkconfig directly.

```

ubuntu@ubuntu:~$ sudo update-grub /media/ubuntu/543a3512-0488-4a53-b37d-9b0b98b092d9
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /media/ubuntu/543a3512-0488-4a53-b37d-9b0b98b092d9/boot/grub/grub.cfg
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

```

---

### Post by Bucky Ball on 2014-06-29
Welcome. Make the changes running from the Live CD then reboot and launch the recovery kernel. Should be the second on you grub menu list at boot. 

When you get to the options, drop to a shell as root and 'update-grub'. If it throws and error about the disks not being mounted, exit to the menu and 'Repair Broken Packages'. This should mount the drives/partitions. Then run the update-grub command again.

Any luck? You could also make all changes running in the recovery kernel.

---

### Post by paul-extraspecialbitter on 2014-06-29
Thanks for the reply. Unfortunately even the grub menu suffers from the same backlighting issue, so I'm unable to see the screen in time to select the recovery kernel. It boots the default kernel instead, resulting in a booted system that is far to faint to be usable.

---

