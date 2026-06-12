---
title: "Booting Dapper from files on disk (no cd/floppy)"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by GatoViejo on 2006-04-01
Greetings:

I am making preparations to install Dapper on a Thinkpad 560X which cannot boot from cd. To do this, I copied the vmlinuz and initrd.gz to a FAT partition and set up GRUB like this:

title Ubuntu Install
root (hd0,0)
kernel /boot/vmlinuz ramdisk_size=14972 root=/dev/ram0 rw
initrd /boot/initrd.gz

A similar setup (using ram instead of ram0) works with the Breezy boot files but Dapper ends up with:

mount: /dev/ram0 on /root failed: No such device

followed by more errors and a shell prompt. At this point, both /dev/ram0 and /root do exist.

Any suggestions would be appreciated.

---

### Post by Sef on 2006-04-01
Have you tried using a USB key and install through that?

---

### Post by GatoViejo on 2006-04-01
This machine will not boot from USB. Once I get the installer to boot, I can use a USB cdrom drive for the rest of the install.

---

### Post by GatoViejo on 2006-04-02
I found out something surprising that may explain the problem but does not help solve it. I copied the initrd.gz to another machine, gunzipped it, and tried to mount it. It would not mount. The error was "you must specify the filesystem type". However, when I did the same thing with initrd.gz files from Breezy CDs (both live and install) they mounted just fine. Apparently there is something fundamentally different about the initrd.gz file in Dapper.

BTW, I am using flight 5. I can only get dialup at home so downloading flight 6 will have to wait until I get into town.

Does anyone know what is different about initrd.gz in Dapper?

---

### Post by GatoViejo on 2006-04-02
Apparently the initrd file in Dapper is a cpio archive instead of a disk image. So, for another shot in the dark, I built a disk image from the contents of the cpio archive and tried using that as the initrd.gz. This gave me a kernel panic.

What magic is in the CD that allows this to work?

---

### Post by fbe on 2006-05-13
Hello,

  SInce the initrd is a cpio file, you cannot mount it. To see/modify its contents :

mkdir initrd_content
cd initrd_content
cpio -i < initrd

  Now you can see the content of the initrd in initrd_content

  To make a new initrd :

cd initrd_content
rm ../initrd
find . -print | cpio -o > ../initrd

  Hope this will help ;)

---

