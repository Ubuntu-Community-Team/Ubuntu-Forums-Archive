---
title: "Problem to boot full encrypted ubuntu"
date: 2023-04-09
forum: Installation &amp; Upgrades
---

### Post by dan4567 on 2023-04-09
Hello everyone, After GRUB loading i choose one of the available option and get Kernel panic not syncing, message, trying to choose previous kernel does not help
This , which described here [https://askubuntu.com/a/48516](https://askubuntu.com/a/48516)
```
sudo fdisk -l
sudo mount /dev/sdax /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt 
sudo mount /dev/sday /mnt/boot
```

does not help

here is my log from Boot Repair
[https://pastebin.ubuntu.com/p/Kcdc8FQwDX/](https://pastebin.ubuntu.com/p/Kcdc8FQwDX/)

also what i think may be relevant is that after grub i does not asked for password to decrypt volume ether when i press c key (for command promt in grub) and trying to cryptomount (hd0,somedrive3) it says nothing but still not ask for password any suggestions? Thanks!

---

### Post by TheFu on 2023-04-09
How good are your backups?  Whenever encryption is used, having excellent, restorable, backups is mandatory, not optional.  This is because when any sort of disk issue happens on an encrypted device, normal tools are often ineffective and the only solution is to start over with a fresh install.
Plus, the effort in performing routine backups seems to exercise parts of the drive in a way that prevents bitrot, so it is a prophylactic, preventing many disk issues.  The more and better we do backups, the less likely we are to need them. 

Not sure what you expect to happen by setting up a chroot.  Did you  attempt to mkinitrd and reinstall grub after those commands?
Someone else will need to look at the pastebin.

---

