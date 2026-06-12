---
title: "Windows 7 missing from grub"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by x_master222 on 2012-10-25
Hi! On my laptop, I had Windows 7 with Windows 8 on dualboot. Now, I installed also Ubuntu and when I restarted system after installation of Ubuntu, there was no choice of booting into Windows 7. There is just Ubuntu and Windows8, no Windows7. How to fix it ? I did not deleted windows7, its partition is there.
Thx

---

### Post by darkod on 2012-10-25
Did you try to select the win8? Does it open a second menu to select between win7 and win8?

When you install two versions of windows, it combines the boot files. This is a windows thing.

Grub2 looks only for boot files and reports them. So it sees the combined boot files as one.

After you select win8 you should have the windows menu to select between 7 and 8.

---

### Post by powder on 2012-10-25
Run this command, then reboot.
> sudo update-grub

---

### Post by darkod on 2012-10-26
> **powder said:**
> Run this command, then reboot.

That rarely helps, ubuntu was installed last and if the boot files of windows are separate it should have already detected both of them.

The issue is more probably combined boot files in which case running update-grub can never make both windows versions show up in the boot menu.

---

### Post by x_master222 on 2012-10-26
I tried to select Win8 and it opened menu with choice of Win7/Win8, but when I selected Windows7 it booted again into boot menu with Ubuntu/Win8. But now, I tried it again and it works. So, thank you. Hope it will work .. I am going to delete Win8 partiton.

---

### Post by darkod on 2012-10-26
Just make sure you don't delete the partition where the windows boot files are!!!

---

### Post by Mark Phelps on 2012-10-26
> **x_master222 said:**
> Hope it will work .. I am going to delete Win8 partiton.

BEFORE you do that, boot into Win8 and change the settings to select Win7 by default. This will restore the Win7 boot loader so when you reboot after removing Win8, it will boot OK.

---

