---
title: "i can't find win 7 after installing ubuntu please help :("
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Meshal-USA on 2011-10-20
hi,

i'm newbie and i just installed ubuntu and it override windows 7.

i used "testdisk" and i restored the partitions and that's what i have when i run "sudo fdisk -l"

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1959        1972      102400   82  Linux swap / Solaris
/dev/sda2   *        1972       31386   236274408+   7  HPFS/NTFS
/dev/sda3           31386       60802   236278784   83  Linux

```

but i cannot find windows in the grub menu and i tried everything and i couldn't find windows. and i think what i have in the hard drive right now is the windows recovery files, which i believe is the reason why windows is not booting up.

could somebody help :(

i'm looking forward for your help

thanks,

---

### Post by shadytv on 2011-10-20
just a shot in the dark have you tried sudo update-grub?

---

### Post by Meshal-USA on 2011-10-20
> **shadytv said:**
> just a shot in the dark have you tried sudo update-grub?

thanks for you reply, yes i tried updating grub but still it's not there.

i also recovered it by using the "boot-repair" but still nothing happen :(

---

### Post by oldfred on 2011-10-20
From boot repair post the link to a report of the boot_info script.

It looks like you installed swap to sda1 which is unusual. Windows 7 normally has a hidden boot/recovery partition in sda1 with its boot files. If they were there, you can with a Windows repairCD fix sda2 to make it bootable.

---

### Post by Meshal-USA on 2011-10-20
> **oldfred said:**
> From boot repair post the link to a report of the boot_info script.

It looks like you installed swap to sda1 which is unusual. Windows 7 normally has a hidden boot/recovery partition in sda1 with its boot files. If they were there, you can with a Windows repairCD fix sda2 to make it bootable.

Oh I see, ok i'll use win repairCD and i'll post what happened

Thanks a lot for ur help

---

### Post by Meshal-USA on 2011-10-20
okay it's been fixed now :) :)

thanks a lot guys.

---

