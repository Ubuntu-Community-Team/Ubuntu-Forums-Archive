---
title: "Ubuntu install on Mylex DAC960 single chan SCSI"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by tamixltd on 2007-02-07
Have a machine with a Mylex DAC960 SCSI raid controller and 36G SCSI, runs the controller setup software well (think its called DACCF), the diags give nothing wrong and it initializes the system disk and Ubuntu then loads from CD, the install runs up to where partitioning needs to take place then tells me there's no disk to install on!    Desperately need help!

---

### Post by ivoks on 2007-05-31
Hit Alt+F2, do 'modprobe DAC960' and then try reinitializing disk.

If that goes well, after the installtion finishes, don't reboot. Hit Alt+F2 once again and then mount your root partition to /target, and do:

mount -t proc proc /target/proc
mount -t sysfs sys /target/sys
(if you have /boot on separate partition, mount it on /target/boot)
chroot /target
echo 'DAC960' >> /etc/initramfs-tools/modules
update-initramfs -u
exit
umount /target/sys
umount /target/proc
umount /target
reboot

---

