---
title: "Removing two old kernels causes update-grub to run 4 times."
date: 2009-11-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-11-16
Takes ages to run. Should this not be a deferred operation so it only runs once at the end?

Apt log attached.

---

### Post by slakkie on 2009-11-16
No, how does it know it will remove 2 kernels? The same will happen if you install 2 kernels at the same time. Same thing.

---

### Post by SevenMachines on 2009-11-16
i'm guessing this is the kind of thing that could be tackled with dpkg triggers instead of running update-grub hooked directly into the linux-image postrm script. maybe theres a reason why its not so, maybe its just not been done yet. since a pending call triggered on update-grub would mean any other triggers on update-grub would be ignored it seems like exactly what you'd want. hmmm :)

---

### Post by SevenMachines on 2009-11-16
if your computer is anything like mine the first update-grub is a result of a dkms modules uninstall and the second the actual purge of the linux-image.

---

### Post by philinux on 2009-11-16
> **SevenMachines said:**
> if your computer is anything like mine the first update-grub is a result of a dkms modules uninstall and the second the actual purge of the linux-image.

Correct.

I think it just needs a deferred trigger.

---

### Post by inportb on 2009-11-16
Agreed. Though fortunately for normal users, kernel updates don't occur often.

---

### Post by ranch hand on 2009-11-16
If you use the symbolic menu entry in a custom file with entries for all your OS' you can disable all of the grub.d scripts except 00_header, 05_debian-theme and the custom entry file.

That way you do not have much running when update-grub is run.

---

### Post by xebian on 2009-11-17
> **philinux said:**
> Takes ages to run. Should this not be a deferred operation so it only runs once at the end?

Apt log attached.

Your solution is to make update-grub do nothing.

Copy /usr/sbin/update-grub  to <something-else>.

Edit /usr/sbin/update-grub and comment out the only line that calls grub-mkconfig.

Then when you want/need to recreate your grub.cfg just execute <something-else>

You just have to remember to run it manually whenever you install new kernel.

---

