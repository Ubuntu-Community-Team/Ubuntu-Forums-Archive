---
title: "Ubuntu / Mandriva 2007"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by mikeglover on 2006-11-02
I have just installed Mandriva 2007 alongside Ubuntu. (On the same hard drive) (Ubuntu 6.10 is in Hda1, Mandriva 2007 is in Hda5 and swap is Hda6)
I accidentally selected Mandriva to install GRUB bootloader while installing.
When I boot up now, I only see Mandriva as an option in the bootloader.
Does anyone know how I can restore the bootloader or add Ubuntu to the GRUB bootloader that Mandriva installed?

Thanks

Mike

---

### Post by Kateikyoushi on 2006-11-02
You have to add an ubuntu to your grub.

Something like this

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

Title can be anything you like, the root line should point to your ubuntu /boot partition or / if you have no separate /boot, couting starts with 0 so hda1 is (hd0,0).

Find the kernel and initrd you have in your /boot folder and add them to grub.menu
After that just save and reboot.

---

### Post by mikeglover on 2006-11-02
Hi,

Thanks for the quick reply.
I have now added the commands which you said to do. My ubuntu install is in Hda1 so i presumed that was (hd0,0)
I now get a kernel panic when i try to boot the option.
I've attached a picture showing the output.
Any ideas what this means?

---

### Post by galileon on 2006-11-02
its trying to load the kernel in sda5 for one thing, you might want to change this to (hd0,0)...

---

### Post by mikeglover on 2006-11-02
Ah yes... oops.
It works now.

Thanks very much for all your help.

---

