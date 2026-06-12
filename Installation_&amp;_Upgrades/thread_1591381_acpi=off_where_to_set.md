---
title: "acpi=off where to set?"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-10-09
I have tested just now if my small compaq 110 will work with ubuntu 10.04.1, it works from the life CD, but it needs the acpi=off to be set.

Whe I install it from that CD, where do I have to set the acpi=off before I reboot? (the ubuntu will not boot otherwise)

---

### Post by sisco311 on 2010-10-09
**Method 1** - Edit the grub menu item at boot time. 

During the bootup hold down the SHIFT key. At the grub menu select Ubuntu and press e for edit. 

Append the **linux** line with the boot option (acpi=off) and press Ctrl+x to boot. 

Once booted in Ubuntu, edit the /etc/default/grub file:
```
gksu gedit /etc/default/grub
```and replace the line **GRUB_CMDLINE_LINUX=""** with **GRUB_CMDLINE_LINUX="acpi=off"**, 

then generate a new Grub2 config file:```
sudo update-grub
```

**Method 2** - CHROOT

Before rebooting from the Live CD session, mount the root partition:
```
sudo mount **/dev/sdXY** /mnt
```
replace **/dev/sdXY** with the actual device name of the root partition (i.e. /dev/sda1). If you don't know the device name, check it in System -> Administration -> GParted.

Mount the virtual filesystems:
```
for i in /dev /dev/pts /proc /sys; do 
  sudo mount --bind $i /mnt$i
done
```

Chroot into Ubuntu:
```
sudo chroot /mnt
```

Edit the /etc/default/grub file:
```
nano /etc/default/grub
```
and add the acpi=off option to the appropriate line. Save the file and exit (Ctrl+x, y, Enter).

Generate a new Grub2 config file:```
update-grub
```

Exit from the chroot:
```
exit
```

Unmount the virtual filesystems & the root partition:
```
for i in /dev/pts /dev /proc /sys / ;do
  sudo umount /mnt$i
done
```

reboot:
```
sudo reboot
```

---

### Post by efflandt on 2010-10-09
If you need that parameter to initially boot an installed system, press **e** at the grub menu, then insert that on the same line as **quiet splash**.  If Ubuntu is the only OS on your system and you have not seen the grub menu, press and hold Shift key after your BIOS splash screen to see the grub menu.

Note that if a kernel boot parameter is "always" required to run your PC properly,  in /etc/default/grub instead of putting it in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (which applies to normal boot to a gui), instead put it within the quotes of **GRUB_CMDLINE_LINUX=""** [which applies to "any" boot, including (recovery) boot to console].

---

### Post by sisco311 on 2010-10-09
> **efflandt said:**
> Note that if a kernel boot parameter is "always" required to run your PC properly,  in /etc/default/grub instead of putting it in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (which applies to normal boot to a gui), instead put it within the quotes of **GRUB_CMDLINE_LINUX=""** [which applies to "any" boot, including (recovery) boot to console].

Good point! Thanks! [noparse]:)[/noparse]

---

