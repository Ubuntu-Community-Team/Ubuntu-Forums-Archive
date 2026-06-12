---
title: "USB-Drive mutliboot with Grub2?"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by bastler on 2010-09-08
Hey Guys!

I have two systems set up with Ubuntu 10.04 LTS (one Desktop, one Laptop) and full disk encryption loosely following the tutorial on lfde.org.

In short:
- entire HDD (including root and swap) as lvm2 inside cryptsetuk-luks-container
- /boot and grub2 on a usb flash drive I carry around.

This works nicely, but at the moment it means carrying around TWO flash drives, which is inconvenient.

Is there a way to put the boot partitions of both machines onto the same USB flash drive and have grub2 display a menu at boot time, enabling me to chose which partition to access and which kernel to load?

I could of course manually insert the entries into one grub-config, specifying a different grub-root. But that would break automatic kernel and initramfs-updates for at least one system.

What I would rather do is chainload grub2.
So in other words what I want is:
- plug in USB drive
- have grub2 display the normal boot menu for the Laptop system with the different kernels PLUS one additional entry "Switch to Desktop"
- when "Switch to Desktop" is selected have grub2 load a second instance of grub2, displaying a menu for the different kernels available on the other boot partition on the stick

- preserve the possibility for both systems to automatically update their respective grub2 kernel lists etc.


In theory I believe this should be possible, since you can easily install e. g. Linux and Windows onto the same drive and have grub2 load one or the other. And grub2 shouldn't care what it loads, as long as it knows how to access it.

However, I don't quite know how to tell grub2 there is a second operating system around on a separete partition...
Any ideas?

---

### Post by C.S.Cameron on 2010-09-08
Have you tried adding the menuentries for both machines in 40_custom then doing an update grub?

---

### Post by oldfred on 2010-09-08
You can put two entires like this into 40_custom and always boot the most current kernel. You just have to have the correct partition numbers. If they happened to be the same partition only one entry would be required.

Boot most up2date kernel on sda5
menuentry "Desktop sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

menuentry "Laptop sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}

---

