---
title: "Dual boot on separate drives issue"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by haiwave on 2020-06-27
Hello, I'm new here. So right now I'm dual booting Windows 10 and Ubuntu 20.04 on separate drives. Everything works, but I have a problem. Ubuntu recognizes the drive in which W10 is installed as /dev/sda2, is there any way to tell Ubuntu not to ever use this drive, or even to make it invisible? Lots of opportunities for me to mess up the W10 drives. From what I've read here, unmounting it seems like a good option but I don't want to mess something up. If anyone knows what to do please tell me, thank you!

---

### Post by Impavidus on 2020-06-28
It won't be mounted right after booting Ubuntu, so no need to unmount it. You could put the Win10 partition in your /etc/fstab with the noauto option. If you do so, it still won't mount automatically during boot, but at the same time your file manager will no longer show it in the side panel, offering to mount it. At the same time, you could configure your Ubuntu to automatically mount a shared data partition in some convenient place.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by oldfred on 2020-06-28
Is sda2 your ESP - efi system partition?
Ubuntu's Ubiquity installs grub boot loader into the ESP on the first drive, often sda.

Did you create an ESP on your Ubuntu drive?
Post this:
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint | egrep -v "^loop"

---

