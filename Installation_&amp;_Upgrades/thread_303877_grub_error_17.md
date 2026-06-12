---
title: "grub error 17"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by borntaskate on 2006-11-21
ok so i just installed a clean copy of windows xp pro on a 40 gb partition of my 150 gb and a 5 gb partition for my swap and the rest ext3 for my "/"so its
hda1 windows
hda2 swap
hda3 ext3
hdb ntfs

and my grub gives me error 17and wont boot how do i fix the grub please help thx

---

### Post by adwait on 2006-11-21
That's because you should idelly install Linux after windows so that grub can look for all the other OSs. ANyway, you can boot off the live CD and use
```
sudo grub-install /dev/hda
```

This will reinstall GRUB.

---

### Post by borntaskate on 2006-11-21
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by adwait on 2006-11-21
Try using
```
sudo cp /proc/mounts /etc/mtab
```

before the grub-install command.

---

### Post by borntaskate on 2006-11-21
ubuntu@ubuntu:~$ sudo cp /proc/mounts /etc/mtab
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

