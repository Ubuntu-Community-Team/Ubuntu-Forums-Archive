---
title: "Bootloader Ubuntu 11.04 Installation"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by dzonov on 2011-07-26
While i was installing ubuntu 11.04, a mirror has been appeared
It was something like:
You can't install bootloader here, please choose another destination.
I chose continue without bootloader.
The installation finished & i rebooted my computer. After the reboot my computer won't start Linux Ubuntu 11.04. It stays on the boot screen.
What should i do? At the first screen i had chose: Erase & Install, & ubuntu had been installed on the whole partition: 320GB.

Please help, thanks

---

### Post by drs305 on 2011-07-26
dzonov,

Welcome to Ubuntu and the Ubuntu forums.  :-)

So we can see the status of your system, please go to the following site and, while running the ubuntu livecd, download/extract/run the boot info script. Post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by dzonov on 2011-07-26
I'm with Try it now [LiveCD]

---

### Post by drs305 on 2011-07-26
To place the Grub 2 bootloader on your system, from the LiveCD you will mount your Ubuntu partition and then install Grub 2.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Do not include the partition number in the second command. Remove the CD and reboot.


You will probably end up at the grub prompt, as you don't yet have a grub menu. If at the grub prompt, enter these commands:

```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod (hd0,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

It should boot into Ubuntu. 

Once it boots, run:
```
sudo update-grub
```

The next time you reboot, it should boot directly into Ubuntu. If you want to see the Grub 2 menu, since you only have one OS, you would have to hold down the Shift key during boot. (Note: seeing the menu is not necessary; only if you are interested.)

---

