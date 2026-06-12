---
title: "Modifying mini.iso"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by robert.sherwood@gmail.com on 2008-04-11
I have a fun problem, hopefully.

I have recently inherited a slightly old Bladeserver chassie (an RLX 300ex, for you blade geeks).

The blades include only serial port, no keyboard or monitor. The existing image is a very odd, very customized redhat distribution that basically can't be connected to the internet without major surgery and the sacrifice of several chickens. 

Accordingly, I have used the mini.iso net boot installation, and transferred it to the blade via console. The mini.iso will boot, but the included kernel cannot recognize the drive controller (a ALI15X3). The kernel from the normal cdrom will boot and recognize the controller.

I don't want to transfer the entire normal installer image over serial link (think 3KB/sec). I have transferred the mini.iso image, and the kernel and modules from the normal image. I have confirmed that I can boot the kernel from the normal image by installing it on a spare partition and booting through lilo.

What I want to do is this: I want to take the kernel from the normal installer, and drop it into the mini.iso installer. I have tried the obvious route (mount loopback, copy files, configure lilo, boot) but I receive the following error during boot:

[   40.008200] List of all partitions:                                          
[   40.018695] No filesystem could mount root, tried:  cramfs                   
[   40.035228] Kernel panic - not syncing: VFS: Unable to mount root fs on unkn)

Any thoughts? Does anyone know how to drop a new kernel into the mini.iso image?

Rob

---

### Post by robert.sherwood@gmail.com on 2008-04-21
Okay, trying again:

The goal is to boot with a kernel that will recognize my hard drive, and then continue with the regular installation process.

1. Mounted mini.iso to /tmp/mini.iso
2. Copied contents of /tmp/mini.iso to /opt (a separate partition on an old linux installation)
3. copied /tmp/mini.iso/initrd.gz to scratch directory (as initrd.mini.iso.gz)
4. unmounted mini.iso
5. mounted ubuntu-8.04-beta-server-i386.iso to /tmp/mini.iso
6. copied /tmp/mini.iso/install/vmlinuz to /opt
7. copied /tmp/mini.iso/install/initrd.gz to scratch directory (as initrd.gz)
8. mkdir initrd.temp1 under scratch directory
9. gunzip initrd.gz
10. cd initrd.temp1
11. cpio -i < ../initrd
12 mkdir initrd.temp2 under scratch directory
13. gunzip initrd.mini.iso.gz
14. cd initrd.temp2
15. cpio -i < ../initrd.mini.iso
16. copy initrd.temp1/lib/modules/2.6.24-12-generic to initrd.temp2/lib/modules/
17. delete initrd.temp2/lib/modules/2.6.24-15-generic
18. cd to scratch directory
19. find initrd.temp1 | cpio -o > initrd.2
20 gzip initrd.2
21. cp initrd.2.gz /opt
22. Create following lilo.conf entry (/dev/hda10 is /opt partition):
     image=/opt/vmlinuz
        label=ubuntu
        #read-only
        initrd=/opt/initrd.2.gz
        root=/dev/hda10

23. lilo
24. reboot
25. at LILO: prompt, choose "ubuntu"


Boot crashes with following message:
[   40.316514] List of all partitions:
[   40.327018] No filesystem could mount root, tried:  cramfs
[   40.343538] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(3,10)


NOTE: Copying the contents of ubuntu-8.04-beta-server-i386.iso to /opt and booting as if it were a standalone partition works fine.  <VERIFYING THIS NOW. WILL UPDATE IF REQUIRED.

---

### Post by robert.sherwood@gmail.com on 2008-04-21
Yep, it boots normally, but fails when trying to detect the CDROM drive. There is no CD-ROM drive, so this is perfectly appropriate behavior.

---

