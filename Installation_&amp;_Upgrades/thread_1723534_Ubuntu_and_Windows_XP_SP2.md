---
title: "Ubuntu and Windows XP SP2"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by nikhillife11 on 2011-04-07
Hello all,

I have made 3 partitions and installed ubuntu on first partition...second one was for swap..I installed windows XP SP2 on 3 partition... While installing XP it made my Linux partition inactive.

But then i booted my system from live USB and turned Ubuntu partition into active...

But still I am not able to boot into ubuntu...Can anyone help me plzz...

---

### Post by Dutch70 on 2011-04-07
It's always best to install windows first. I hope you installed it windows into a primary partition, not a logical partition.

See if this helps get Ubuntu booting again.
[[COLOR="Red"]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Mark Phelps on 2011-04-07
When you installed XP, it overwrote the MBR and removed the entry for GRUB that allowed you to launch Ubuntu.

The links provided should get that working again.

Also, as far as I know, while Windows requires the OS partition to be active to work, Linux does not.

---

### Post by oldfred on 2011-04-07
Windows has to have the boot flag (active partition) on the windows primary partition. Grub does not use the boot flag, but some BIOS do require a boot flag on a primary partition to even let you boot (BIOS desinger must only have known about windows).

Reinstall grub2's boot loader to the MBR to let you boot Ubuntu.

After you boot run this to add windows to the grub menu.
```

sudo update-grub
```

---

