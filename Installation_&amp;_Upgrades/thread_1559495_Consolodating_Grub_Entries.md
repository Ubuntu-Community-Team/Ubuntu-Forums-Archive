---
title: "Consolodating Grub Entries"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Mike_uk on 2010-08-23
I am dual booting Ubunto 10.0.4 with windows XP. When I boot and get the Ubunto grub2 screen, I have multiple entries for ubunto, how do I edit the file so I just get ubunto, winxp and memtest. Not 4 or everything, it possibly happened when upgrading versions of Ubunto. Mike

---

### Post by ajgreeny on 2010-08-23
> **Mike_uk said:**
> I am dual booting Ubunto 10.0.4 with windows XP. When I boot and get the Ubunto grub2 screen, I have multiple entries for ubunto, how do I edit the file so I just get ubunto, winxp and memtest. Not 4 or everything, it possibly happened when upgrading versions of Ubunto. Mike
These multiple entries for ubuntu are simply new kernels that are added every so often when they are available in updates.  It is nothing to worry about, and I would suggest you keep the two most recent kernel versions on the machine, just in case something goes wrong with one of them.  You can remove older versions of the kernel using synaptic easily by searching for the number you see in the menu, eg 2.6.32-22 and removing from there.

You can remove the **memtest** and **recovery mode** entries from the menu, but do not edit the **/boot/grub/grub.cfg** file.   To do this you must edit as root with ```
gksudo gedit /etc/default/grub
``` and uncomment (remove the #) from the second of the two lines to remove recovery mode from the menu
> # Uncomment to disable generation of recovery mode menu entries
[COLOR=Red]#[/COLOR]GRUB_DISABLE_LINUX_RECOVERY="true"

To get rid of memtest you should remove the executable status from **/etc/grub.d/20_memtest86+** with ```
sudo chmod -x /etc/grub.d/20_memtest86+
```then run ```
sudo update-grub
```

---

