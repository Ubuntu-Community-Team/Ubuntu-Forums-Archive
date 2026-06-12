---
title: "Making a LILO boot floppy for Ubuntu"
date: 2004-12-25
forum: Installation &amp; Upgrades
---

### Post by Thanatos9602 on 2004-12-25
Instead of trying to figure out how to put two linux distributions on one computer & config Lilo. What about making a Lilo boot floppy for Ubuntu? How would I go about that? I need step by step in linux. Unfortunately, it doesn't have the make boot command like windows does. If it does? I can't find it. Thanks for any help. Sorry for the stupid questions.

---

### Post by paradox on 2005-01-10
I have same question! Any person can paste commands to create this floppy?

TNX!

---

### Post by eldrich_rebello on 2005-01-10
Booting From Floppy

One of the great attractions to Linux is the small size of the kernel, the core code necessary to run the operating system. On most systems, even in a default install configuration, the kernel is less than 1.44 MB - small enough to copy to a floppy. The ability to copy this core code to a floppy means that, even in many catastrophic failure scenarios, you’ll always have the ability to get to your Linux system. If your BIOS is set up to allow booting from a floppy, you’ll be able to do so with Linux.

This boot floppy also differs greatly from a Windows rescue disk. On the Windows side, the rescue disk merely provides a set of tools that allow you to access the operating system from a hard drive or CD-ROM. The Windows kernel does not, in fact, reside on the floppy. In Linux, every piece of code necessary to run the basic OS can be copied to a boot floppy.

A Linux boot floppy is, in my book, one of four or five essential backup tools. Even though my boot loader of choice has always been Lilo, I keep a boot floppy for my Linux OS in its own special place in my work area, where it’s immediately accessible in a pinch.

If you’ve recompiled the kernel or lost the original boot floppy created during install, it’s a good idea to create another. Creating another floppy after a kernel recompile is necessary in order to use the new kernel from floppy.

This is a relatively painless process in Linux. First, use a brand new formatted floppy. As this floppy can be in DOS format with no ill effects, you should be able to use a new disk straight out of the box. Next, check the path you’ve assigned your existing kernel in Lilo:

    view /etc/lilo

You’re looking for the “image” line in Lilo. It should look something like this:

    image = /boot/vmlinuz

Now, with the floppy in the drive, issue the following command:

    dd if=/boot/vmlinuz of=/dev/fd0 bs=8192

This command instructs your Linux system to copy [dd] the input file [if] /boot/vmlinuz to the output file [of] / dev/fd0 [the first floppy device] using a block size [bs] of 8192 bytes. Provided your BIOS is set up to boot from floppy, you should be able to test this new boot floppy by leaving the floppy in the drive and rebooting.

By keeping a current boot floppy close by, you’ll always have access to your Linux system.

---

### Post by eldrich_rebello on 2005-01-10
I know what you're thinking -- if I don't install the boot loader, how will I boot the system?

Let's assume that the bootloader is on the first hard drive (hda) from your original distro. You need to copy certain files from the /boot directory of the hdb drive to the /boot directory of the hda drive. To do this, you must first mount the hdb drive while logged in as the root user. Since this is only a temporary mount point, I just use the floppy directory:

mount/dev/hdb1 /mnt/floppy

Some of the newer distros now use the /media directory for mount points, so if the above command doesn't work, try:

mount /dev/hdb1 /media/floppy

You should see an icon appear on the desktop that looks like a diskette. Enter that drive, and cd /mnt/floppy/ boot or cd /media/floppy/boot.

There are three files you need to copy to the /boot directory of the first hard drive (hda). The first is System.map, which will look something like System.map-2.6.9-1.6_FC2 (which is the System.map for the 2.6.9.-1.6 kernel from Fedora Core 2). The other two files will have identical numeric suffixes, after prefixes of vmlinuz and initrd. Once you locate these three files, copy them to the /boot directory of the first hard drive (hda). When copying the initrd file, make sure to copy it exactly as you see it, including the .img extension that will be someplace in the name of the file.

Now cd /boot to change to the /boot directory of your first hard drive (hda). You should see the three new files added to the directory.

Now there's only one step left -- add a stanza to GRUB, the boot loader file. Change to the /boot/grub directory and open the file menu.lst in your favorite text editor. Scroll down a few lines and add the new stanza under the one for your existing distro, skipping a line between them. It should look something like this:

title "whatever you want to call your new distro"
    root (hd1,0)
    kernel /boot/vmlinuz"Your Kernel Number" ro root=LABEL=/
    initrd /boot/initrd"Your Kernel Number".img

Note that this is a case-sensitive and space-sensitive document. That means that root=label is different from root=LABEL, and there is no space after the "=".

If you've done things right, you can now reboot your machine and you will see your new entry in the boot menu. Select it and you will boot into your new distro.

---

### Post by eldrich_rebello on 2005-01-10
not too sure if this will help.read anyway.off topic.must confess

---

### Post by paradox on 2005-01-10
TNX, TNX!!!  :D  :!:  :mrgreen:  8)

---

### Post by wallijonn on 2005-01-10
I did this one for GRUB: [http://www.ubuntuforums.org/showthread.php?t=6195&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=6195&highlight=grub)

---

### Post by paradox on 2005-01-11
hummmm...i try dd if=/boot/vmlinuz-2.6.8-3-i386 of=/dev/fd0 bs=8192 but this don't work (vmlinuz is link at vmlinuz-2.6.8-3-i386. At boot i receive this message:

this isn't a boot floppy. Remove floppy and press any key.

Humm...i try with bs=1440 and without bs but i still receive same message.

How i wrong?

TNX!

---

