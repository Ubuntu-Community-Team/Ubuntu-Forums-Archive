---
title: "GRUB problems with windows"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by PixelCloud on 2006-09-25
I recently installed windows xp onto another partition on my harddrive.

However, reinstalling grub didnt go as i planned, i was unable to boot into kubuntu after reinstalling grub.

```

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

```

however when i reinstalled grub i typed root (hd0,0) then setup (hd0)

if i change the root to (hd0,0) the ubuntu will get to the splash screen but fail to mount the root partition

i'm confused and i just want a dual booting system

i used the grub super disk to boot into ubuntu directly which worked.

---

### Post by zxee on 2006-09-26
While in your ubuntu install try starting grub from a shell.
> sudo grub
then 'find /boot/grub/stage1' that step might not be necessary but it should return the actual partition of your install. 
After it does that 'setup hd0,0' or whatever grub outputs, and restart. Hope that helps.

---

### Post by adrian15 on 2006-09-27
> **PixelCloud said:**
> I recently installed windows xp onto another partition on my harddrive.

However, reinstalling grub didnt go as i planned, i was unable to boot into kubuntu after reinstalling grub.

```

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

```

however when i reinstalled grub i typed root (hd0,0) then setup (hd0)

if i change the root to (hd0,0) the ubuntu will get to the splash screen but fail to mount the root partition

i'm confused and i just want a dual booting system

i used the grub super disk to boot into ubuntu directly which worked.

Here it is the solution:

```

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

```

Usually (hd0,0) means hda1 in terms of Linux kernel.

And you will also need /etc/fstab to be updated. Where you see /dev/hda2 you will have to write /dev/hda1 if not it will tell you that it cannot mount ROOT VFS.

adrian15

---

