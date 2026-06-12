---
title: "switch windows OS in 10.10 dual-boot?"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by nsus on 2010-12-21
hello all,

I recently bought an asus eee-PC 900HD set up by its previous owner to to boot to either ubuntu 10.10 or windows xp.
My question is simple: how can I get rid of xp and install vista in its place?
As a side-note; the eee-PC has no optical drive.  It has USB ports and an SD card reader.  Is it possible to install windows through one of these?  I do have an old laptop optical drive I've been meaning to house in a USB enclosure.  Is the cd/dvd route my only option?

thanks in advance

---

### Post by dino99 on 2010-12-21
is it possible: yes, select it into bios to boot on

replace xp: install partedmagic on a usb stick to format xp, then install vista on that usb stick to make the installation.

note: if grub (the ubuntu bootloader is installed on the same device as xp (might be), that mean that formatting xp will remove grub too, so previously install grub-pc on the ubuntu partition (something like /dev/sda1, instead of /dev/sda actually)

---

### Post by sikander3786 on 2010-12-21
Here is how you can create a startup disk for Windows 7 using Ubuntu. The procedure would be same for Vista.

[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

Make sure you don't delete any other partitions during Windows installation as the Windows partitioner wouldn't recongize Ubuntu partitions at all and might list them as unknown partition.

As said above, installation of Vista would remove Grub and will place the Windows bootloader in MBR of your HDD thus making Ubuntu un-bootable. You'll need to re-install Grub then.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Feel free to ask if you've got further queries :-)

---

