---
title: "Upgradine modset issue"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by mbusha on 2011-03-21
I seem to have a recurring error that happens whenever the kernel gets upgraded.  I'm running Ubuntu 10.10 on a Lenovo thinkpad T510, and during the last two software updates that updated the kernel (to 2.6.35-27 and 2.6.35-28 ), my grub.cfg file was changed to look something like this:

```
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set dcefe75b-4669-4787-98e3-5b4e94785474
        linux   /boot/vmlinuz-2.6.35-28-generic root=UUID=dcefe75b-4669-4787-98e3-5b4e94785474 ro   i915.modset=0 quiet splash
        initrd  /boot/initrd.img-2.6.35-28-generic
}
```The key change here is the "i915.modset=0" entry, which I know was note there before since I deleted it after my last update.  This results in the following error message during the boot process:

```

Mar  21 9:52:57 XXXXX kernel: [   17.516057] i915: Unknown parameter `modset'

```with the vesa drivers being instead of nv, which forces my machine to run at very low resolution with all graphics effects disabled.  (This is further detailed in the [linked thread]("http://ubuntuforums.org/showthread.php?p=10521715#post10521715")). 

The solution seems to be to just deleted the "i915.modset=0" entry of the grub.cfg file, but now that this has happened a second time after updating, I'm wondering if there might be something else going on (or am I just going to have to change the entry in grub.cfg every time there's an update?).  Has anyone else seen anything like this or have any thoughts why this would be happening?  

Thanks in advance.

---

### Post by dino99 on 2011-03-21
yes there is a typo error: replace "modset" by "modeset" by editing:

sudo gedit /etc/default/grub

then save, close and:

sudo grub-mkconfig
sudo update-grub

---

### Post by mbusha on 2011-03-21
Thanks!

---

