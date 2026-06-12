---
title: "don't need grub, how to exorcise??"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2012-11-23
HI All,

I need (prefer) to eliminate the grub screen. I have a 100 percent certified linux capable punchbox that came with microsoft preinstalled.  But, have no use for microsoft. The machine was never booted to microsoft, even when it was new, I installed linux right away (overwriting microsoft).

I'd like to eliminate the grub screen if possible, to enable faster booting. The official documentation says grub should not even appear unless there are multiple OS's installed. But, it appears anyway!!!!

The official documentation page gives ways to hide grub, or to minimize the timeout delay.  But, since I don't need it, it makes a much cleaner install if I can just eliminate it completely. 

What are my options regarding eliminating it, is it actually needed for a system with no other OS's installed?

TY

Art

---

### Post by lisati on 2012-11-23
I'd advise against removing grub entirely, because even if you only have one OS on your computer, you'll still need a bootloader. What you might want to do instead is to configure grub not to show its menu unless you ask it to.

Have a look here for more information: [https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)

---

### Post by darkod on 2012-11-23
You might have something like a recovery or tools partition still on the hdd. Even if you deleted the main system partition, a smaller system reserved or recovery partition might still be there. They have boot files on them so they are detected similar to windows.

You are right, with only ubuntu the grub boot menu shouldn't show. And you can't remove grub completely since without bootloader ubuntu (or any OS) will not boot.

Too see all partitions on the disks, post the output of:
sudo parted -l (small L)

---

### Post by goodbye-windows(tm) on 2012-11-25
I don't have access to the computer at this time, but will have at Christmas time. I did try to edit the delay parameter as suggested in [https://help.ubuntu.com/community/Gr...splay_Behavior]("https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior"), but the thing refused to allow me to save the edited file. I tried it as root in terminal using sudo. And, I tried to edit it again after logging in to the primary user account. 

I was going to try and search the forum for a solution to this issue, but ran out of time and my daughter has the computer at school until the Christmas break.

I'll post the results of the parted -l command as soon as I can.

Regarding the partitions on the hard drive.....I did leave the Dell recovery partition, which is designed to restore the OS to its original condition if necessary (which was windows 7 I think). Couldn't see deleting it, as not having it available could impact the sale price if we ever wanted to sell the system at a later date.

But, perhaps the extra Dell partition explains why the I get the grub screen.

TY to [[COLOR=#dd4814]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635") and to [darkod]("http://ubuntuforums.org/member.php?u=946366") for the enlightenment.

Art

---

### Post by SuperFreak on 2012-11-25
You could install "Grub Customizer" (look in Ubuntu Software Center) and set Timeout to zero seconds under General settings tab

---

### Post by darkod on 2012-11-26
If you left the recovery partition, probably that's the reason for the grub showing because those partitions have windows boot files on them.

It's very easy to temporarily disable the os-prober not to detect any other boot files (since you have only ubuntu), and the process doesn't delete anything. You can easily enable it later again.

You can disable it with:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

That should remove the recovery partition from the grub menu.

---

### Post by goodbye-windows(tm) on 2012-12-22
> **darkod said:**
> If you left the recovery partition, probably that's the reason for the grub showing because those partitions have windows boot files on them.

It's very easy to temporarily disable the os-prober not to detect any other boot files (since you have only ubuntu), and the process doesn't delete anything. You can easily enable it later again.

You can disable it with:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```That should remove the recovery partition from the grub menu.


Worked perfectly, now the grub flashes on the screen briefly, but doesn't slow the boot time.

TY.

Art

---

