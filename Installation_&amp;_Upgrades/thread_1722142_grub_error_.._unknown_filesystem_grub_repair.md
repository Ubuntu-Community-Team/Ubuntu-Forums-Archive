---
title: "grub error .. unknown filesystem grub repair"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by patrick11ty on 2011-04-05
hello .. my dual boot (ubuntu 10.10 & win7) has given a grub error that I would like some help solving. on boot the computer now says:
> error: unknown filesystem
grub rescue>

I would really like to get both systems up and running ..
I have dug around a few hours and tried some steps i found [here]("https://help.ubuntu.com/community/Grub2#Command Line and Rescue Mode") but honestly I am afraid I will lose the win7 if I have not already if I go further. from the grub rescue I have found the grub here:
```
ls (hd0,msdos7)/boot/grub
```
which is weird I think as the results from the boot info script (below) seems to indicate it should be on msdos6.. **help would be greatly appreciated**.

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

////clip////

```

---

### Post by wilee-nilee on 2011-04-05
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **partition #6** for (,msdos6)/boot/grub.

Your install is in sda7 follow this link in reinstalling the grub2 bootloader from a live cd to the mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Same page as your link; above, section 12.

---

### Post by drs305 on 2011-04-05
If everything is intact you may be able to do this from the rescue prompt:

```
set prefix=(hd0,7)/boot/grub
set root=(hd0,7)
insmod (hd0,7)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda7 ro
initrd /initrd.img 
boot
```

If it boots run:
```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by patrick11ty on 2011-04-05
it worked! was surprised during the process that it didn't recognize or need me to specify a /home or /boot but I guess it didn't need it as it seems to be fully functional (win7 as well seems to be working).

thanks so much for your help.

---

### Post by patrick11ty on 2011-04-05
> **drs305 said:**
> If everything is intact you may be able to do this from the rescue prompt:

```
set prefix=(hd0,7)/boot/grub
set root=(hd0,7)
insmod (hd0,7)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda7 ro
initrd /initrd.img 
boot
```

If it boots run:
```
sudo grub-install /dev/sda
sudo update-grub
```
thanks for the idea .. but I was at the time booted into the live usb. hopefully it can help someone else in the future.

thanks for your help!

---

