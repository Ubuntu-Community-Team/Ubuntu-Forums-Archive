---
title: "Boot-repair failed"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by petri on 2011-09-27
I was trying to increase LVM with system-config-lvm when it hangs and I have to kill the process. LVM was working ok afterwards but when I reboot Grub is gone and [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") didn't fix it this time.

Boot-repair created this file [http://paste.ubuntu.com/698086/](http://paste.ubuntu.com/698086/)
I hope someone knows what to do now.

---

### Post by oldfred on 2011-09-27
I do not know LVM, but it looks like all your booting is in sdc which is not part of the LVM.

Which drive are you using to boot from in BIOS? Script or grub do not report "same" drive correctly and any of the drives that say partition 3 may work.

It looks like your Windows is missing its boot files. Was it installed in a second drive with its boot loader in what was sda and that got overwritten.?

---

### Post by petri on 2011-09-28
Thanks, I changed the boot order in BIOS and Grub was working again. I'm not going to do anything else because I going to fix my LVM and then reinstall everything because of change of hardware.

---

