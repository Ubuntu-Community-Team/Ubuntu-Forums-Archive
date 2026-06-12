---
title: "Grub not finding XP and not showing menu - [SOLVED]?"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by marineBoy on 2011-02-12
Hi,
My PC has two hard disks. The first has windows XP installed and I've just installed 10.04 on the secondary drive, but grub2 wasn't finding XP to add to the menu and there was no menu showing on a reboot. I did a search but didn't find a conclusive answer, so:

I tried running os-prober, including after explicitly mounting the windows partition but still no joy.

I added:
```

menuentry "Windows xp - /dev/sda1" {
set root=(hd0,1)
chainloader (hd0,1)+1
}

```
to the 40_custom script in /etc/grub.d/.

I ran ```
sudo update-grub
``` and checked /boot/grub/grub.cfg and the new entry had been added, but still no change on booting. After checking [this thread]("http://ubuntuforums.org/showthread.php?t=1195275") I think that GRUB still thought I had a single OS machine and so didn't need to display a menu. I commented out the 
```
#GRUB_HIDDEN_TIMEOUT=0
``` line in /etc/default/grub and now it displays.

Hope this is of use to someone.
Regards,
Duncan

---

