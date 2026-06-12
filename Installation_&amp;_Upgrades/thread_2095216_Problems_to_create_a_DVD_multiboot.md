---
title: "Problems to create a DVD multiboot"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by Breixo L Garcia on 2012-12-16
Hi Community,

I have been trying to create a DVD multiboot with the multicd tool.
I'm following this steps [http://http://multicd.tuxfamily.org/#Instructions]("http://http://multicd.tuxfamily.org/#Instructions")

But the console shows always that:

cp: fallo al extender «/home/breixo/Documentos/mydvd/MultiCD/multicd-working/boot/i386.l.ubuntu/vmlinuz»: Error de entrada/salida

"Error Input/Output" for the english speakers... or something like that

What do I miss out? Any Help would be greatly appreciated

-Regards

---

### Post by oldfred on 2012-12-16
I have never used the multiboot CD, but use grub2 to loopmount ISO from flash drives. 

But I sometimes get a similar error. Usually a path to the correct location is wrong. Sometimes with loopmounting and grub2 some ISO just do not work.

       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by Breixo L Garcia on 2012-12-16
Hi oldfred,

Thanks a lot for your answer but the solution was only download the distro one more time. Because they were corrupted during the download. Now I have a new problem with this multicd.

The console shows that:

cp: no se puede efectuar `stat' sobre «/tmp/syslinux-*/com32/modules/chain.c32»: No existe el archivo o el directorio

If someone have any idea, it would be greatful.

-Regards

---

