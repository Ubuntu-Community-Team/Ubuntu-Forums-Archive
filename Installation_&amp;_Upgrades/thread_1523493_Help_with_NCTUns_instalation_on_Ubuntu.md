---
title: "Help with NCTUns instalation on Ubuntu"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by indigodavid on 2010-07-03
I'm trying to install NCTUns 6.0 on Ubuntu 10.04. I'm folowing the guide in [http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu](http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu), with some variations to adapt that procedure to my system.

I managed to accomplish the installation and I can see the new kernel installed in the GRUB but when I try to access to it I get an error.

[COLOR=SeaGreen][ 1.040651] ACPI: I/O resource 0000:00:1f.3 [0x1c00-0x1c1f] confilcts with ACPI region SMBI [0x1c00-0x1c0f]
mount: mounting none on /dev failed: No such device
fuse: device not found, try 'modprobe fuse' first
Could not mount the partition /dev/sda2[/COLOR]

I think my mistake could happen when I was compiling the kernel I tried the step
cp config-2.6.25 .config

[FONT=Arial][FONT=Verdana]But I couldn´t copy that, so instead I executed a default configuration[/FONT]
[/FONT]
[FONT=Courier New]make defconfig[/FONT]

[FONT=Verdana]Could anyone help me to configure properly the kernel before compiling it?[/FONT]

---

