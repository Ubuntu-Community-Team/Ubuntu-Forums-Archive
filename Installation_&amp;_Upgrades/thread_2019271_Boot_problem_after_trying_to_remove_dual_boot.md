---
title: "Boot problem after trying to remove dual boot"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by Sven Sorensen on 2012-07-07
Hello everyone,
a friend of mine asked for help, but I'm clueless, so I'm asking you for help.
So, this friend had a win-linux dual boot, but was running low of disk so he erased the linux partition (from win I think).
Now the system won't boot, I assume grub is gone, so we're wondering if there's a way to fix it without losing the win partition.
Thanks in advance to anyone who can help

---

### Post by kc1di on 2012-07-07
> **Sven Sorensen said:**
> Hello everyone,
a friend of mine asked for help, but I'm clueless, so I'm asking you for help.
So, this friend had a win-linux dual boot, but was running low of disk so he erased the linux partition (from win I think).
Now the system won't boot, I assume grub is gone, so we're wondering if there's a way to fix it without losing the win partition.
Thanks in advance to anyone who can help

when you deleted the Linux partition all you did was delete Grub config files grub it self is still installed in the Master Boot Record (MBR)  
Your friend will have to use his windows disk to restore the MBR
You did not mention which version of windows he is using so can't get exact step by step for you.

here's a page that tells you how to restore the windows MBR using the ubuntu live cd. that may be of help.

[http://ubuntuforums.org/showthread.php?t=622828]("http://ubuntuforums.org/showthread.php?t=622828")

---

### Post by drs305 on 2012-07-07
If  
1) he has an Ubuntu LiveCD, 
2) the Windows boot files haven't been disturbed, and 
3) the boot flag is still on the Windows partition (which it should be),

he can probably restore the Windows bootloader by:

Boot the LiveCD to the Desktop
Partially* install the *lilo* bootloader
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  # Assumes the BIOS boots sda first and Windows is on sda
```
When installing lilo, the system will say lilo is not fully configured and further commands need to be run. Don't do this, as all you need to do is point the MBR information back to Windows instead of Grub.

Reboot and hopefully the Windows bootloader will appear.

---

