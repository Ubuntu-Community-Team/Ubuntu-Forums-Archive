---
title: "[SOLVED] multiple kernel entries in grub menu.1st"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by kevind2071 on 2008-06-25
Hi

When I used Update Manager to update ubuntu last month, it added a new kernel entry in my grub menu.1st file.  When my wife started the computer the next day, grub did not boot and she picked the recovery partition for my Windows computer.  It has taken a couple weeks to get Windows working again. I noticed that it did it again when I updated tonight.

Is there any reason to keep older kernels in menu.1st? (for example, kernel 2.6.24-19-generic, kernel 2.6.24-18-generic, kernel 2.6.24-16-generic and kernel 2.6.24-14-generic)

Kevin

---

### Post by iaculallad on 2008-06-25
> **kevind2071 said:**
> Hi

When I used Update Manager to update ubuntu last month, it added a new kernel entry in my grub menu.1st file.  When my wife started the computer the next day, grub did not boot and she picked the recovery partition for my Windows computer.  It has taken a couple weeks to get Windows working again. I noticed that it did it again when I updated tonight.

Is there any reason to keep older kernels in menu.1st? (for example, kernel 2.6.24-19-generic, kernel 2.6.24-18-generic, kernel 2.6.24-16-generic and kernel 2.6.24-14-generic)

Kevin

Placing the kernel entries in your menu.lst is the job of **update-grub**, this is performed everytime your kernel is updated to newer version.
You can get rid (delete it/comment it out) of those old kernels in your GRUB menu by editing the /boot/grub/menu.lst file. Then later on, try to delete those old kernels using your Synaptics Package Manager. Search for the string "linux-image" (w/o quote) and delete the old kernels that displays.

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by kevind2071 on 2008-06-25
I figured that I could comment out the grub entries and/or change the default number manually, but that seems to be a hassle every time the kernel changes.

If later, I decide to use Synaptics to remove the kernels, will **grub-update** delete the entries in **menu.1st**.

---

### Post by iaculallad on 2008-06-25
> **kevind2071 said:**
> I figured that I could comment out the grub entries and/or change the default number manually, but that seems to be a hassle every time the kernel changes.

If later, I decide to use Synaptics to remove the kernels, will **grub-update** delete the entries in **menu.1st**.

Yes, that automatically would make changes in your /boot/grub/menu.lst file.

---

### Post by kevind2071 on 2008-06-25
> **iaculallad said:**
> Yes, that automatically would make changes in your /boot/grub/menu.lst file.

Is there any reason to keep older kernels around?  I understand keeping one or two around for testing purposes.  What is a good rule of thumb?

---

### Post by iaculallad on 2008-06-25
> **kevind2071 said:**
> Is there any reason to keep older kernels around?  I understand keeping one or two around for testing purposes.  What is a good rule of thumb?

Good rule of thumb is to keep a kernel (old kernel) that has not caused your system to break or displayed any major error. You're new kernel upgrade would just be for experimentation.

If that "new" kernel had not caused any breakdown, then maybe, it's time for that OLD kernel to be deleted.

---

