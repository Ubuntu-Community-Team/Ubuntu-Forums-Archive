---
title: "windows hard disk will not go away"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by peebly on 2006-11-25
hello

I have just installed edgy, when it boots up the windows hard disk appears on the desktop and in my computer.

If I unmount the disk to get rid of them they reappear next time I restart edgy.

How can I stop this.

Linux and Windows are on separate hard disks.

---

### Post by Dr. Nick on 2006-11-25
edit fstab, use this command from a terminal
[B]
gksudo gedit /etc/fstab
[/B]
put # in front of the line that mounts the ntfs of vfat partition

---

### Post by bulldog on 2006-11-25
If you have separate hard disks and you won't see GRUB as your bootloader,just try to boot from the other hard disk.

I think GRUB is installed on the other hdd,so make this your master boot device in your BIOS.

---

### Post by peebly on 2006-11-25
thanks people, issue resolved.

:)

---

