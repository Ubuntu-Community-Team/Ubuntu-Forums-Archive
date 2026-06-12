---
title: "Can GRUB1 boot Lucid?"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ubuntiac on 2010-04-05
Hi there all,

After experimenting with a couple of distros on a second partition it removed the grub entries referring to Kubuntu. Kubuntu's still on the disk, just not in GRUB.

Now I have Arch - which uses Grub1 - booting properly with no reference to Kubuntu. I can edit the menu.lst in Arch to update GRUB, but none of the options I try seem to boot Kubuntu properly.

I have a pretty simple setup. Fdisk -l:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6778    54444253+  83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3            6779        9327    20474842+  83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
```

sda1 is Kubuntu
sda3 is Arch

My menu.lst entries look like:

```
title	 Kubuntu, 2.6.32-18-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-18-generic root=/dev/sda1 ro
initrd	 /boot/initrd.img-2.6.32-18-generic
quiet
savedefault
boot

title	 Kubuntu, 2.6.32-18-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.32-18-generic root=/dev/sda1 ro single
initrd	 /boot/initrd.img-2.6.32-18-generic
boot
```

I can browse my kubuntu partition and /boot/vmlinuz-2.6.32-18-generic and /boot/initrd.img-2.6.32-18-generic are there.

Strangely, the standard boot option just says "File not found" though while recovery seems to boot, but goes to a black screen at the end. There are no flashing keyboard lights, but even Alt+Sysrq+RSEINUB won't reboot it.

Any ideas? I miss my Kubuntu! :'(

---

### Post by oldfred on 2010-04-05
Did you use ext4 for Kubuntu? Ubuntu updated its version of grub legacy with 9.04 to allow booting into ext4, but grub legacy is/was not maintained so others may not have that capability.

---

### Post by Ubuntiac on 2010-04-05
> **oldfred said:**
> Did you use ext4 for Kubuntu? Ubuntu updated its version of grub legacy with 9.04 to allow booting into ext4, but grub legacy is/was not maintained so others may not have that capability.

Interesting... Yes, I did use EXT4. So it may work better with the same configuration, just using GRUB2, huh...

---

### Post by Ubuntiac on 2010-04-05
Hey, would it be possible to install grub2 to the bootloader from a K/Ubuntu live CD? I'm thinking that might do the trick...

---

### Post by oldfred on 2010-04-05
You can add grub2 and it should find all your other systems with a sudo update-grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

