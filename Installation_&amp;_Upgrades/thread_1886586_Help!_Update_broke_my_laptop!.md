---
title: "Help! Update broke my laptop!"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by Dy1anW on 2011-11-25
I updated (not upgraded) my laptop earlier today. It was just a general update, but now when I try to start the computer, I'm stuck at the boot sequence, and it's showing all the services starting/stopping.

Any ideas how I can fix this? I'm using 11.04 if that's of any help.

Edit: additional info. All the other terminals are accessible, only tty7 is stuck, so I wonder if it was the updated graphics driver, gnome or what?

---

### Post by sudodus on 2011-11-25
Try to start in recovery mode (select in the grub menu). Does that work?

---

### Post by BC59 on 2011-11-25
From the Grub Menu Screen during boot, choose Previous Linux Versions and click on the previous kernel, which is Kernel Linux 3.0.0-12. and ENTER

Then boot normally.

---

### Post by sudodus on 2011-11-25
> **Dy1anW said:**
> I updated (not upgraded) my laptop earlier today. It was just a general update, but now when I try to start the computer, I'm stuck at the boot sequence, and it's showing all the services starting/stopping.

Any ideas how I can fix this? I'm using 11.04 if that's of any help.

Edit: additional info. All the other terminals are accessible, only tty7 is stuck, so I wonder if it was the updated graphics driver, gnome or what?
Glad it's alive via the other terminals! Yes I think it is problems with the graphics driver. 

Does it start from the old kernel as suggested by BC59?

---

### Post by Dy1anW on 2011-11-25
It probably doesn't help that I didn't install grub from the start. Luckily the laptop could still recognise a wired connection (wireless is off, and it's been yonks since I mounted devices manually).

At least I thought I didn't have it. As it turns out I already had 1.99, went to 0.98, and now I'm back to 1.99. I've no idea how to get it to start up though, it never displayed on boot. Apparently holding down the 'shift' key during boot is supposed to bring up the menu, but it's not.

---

### Post by BC59 on 2011-11-25
Well in that case It would be a good idea to install Grub2.

A good solution is to install it through Boot-Repair


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


I don't know if another member has a better idea.

---

### Post by Dy1anW on 2011-11-25
Thanks for that, but I'll have to leave this until tomorrow night when I have access to someone else's DVD writer. Even though I've installed it, I can't get it to run since it (apparently) requires a graphical interface. I tried the live-USB option, but the only spare stick I have is SanDisk, which it seems has issues with the boot loader, and the only functioning DVD writer I have is on my laptop...  Ugh! Well, fingers crossed.

---

### Post by Dy1anW on 2011-11-26
Okay, I've got GRUB2 up and running. Booting into previous versions yielded the same problem (stuck in boot sequence). I should also mention my current kernel is 2.6.38-12, which was the update from a couple days ago, but 3.0.0-12 is supposed to be the previous?

I can get into FailSafeX on the current kernel (recovery mode), which I guess uses standard video drivers. I've dropped back to driver version 173, and now the laptop boots normally again. I'm in a bit of disbelief that the proprietary driver was at fault here (or could it be a botched update?), but I'll remove the latest driver and reinstall it again later.

Thanks!

---

### Post by BC59 on 2011-11-26
If you install manually proprietary drivers, then after every kernel update you have to reinstall them.

---

