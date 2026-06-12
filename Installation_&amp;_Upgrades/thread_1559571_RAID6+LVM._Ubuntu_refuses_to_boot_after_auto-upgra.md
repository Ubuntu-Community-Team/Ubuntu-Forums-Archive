---
title: "RAID6+LVM. Ubuntu refuses to boot after auto-upgrade"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by zofiaifoz on 2010-08-23
Ubuntu (9.10 X64 Server) refuses to boot after auto-upgrade. I have RAID6+LVM installed. After turning on my computer all I got is:


GNU GRUB version 1.97~beta4
[ Minimal BASH-like line editing is supported. For the first world, TAB lists possible command completions. Anywhere else TAB lists the possible device/file completions. ]
sh:grub>



After looking for some answers I tried with several commands:

sh:grub>search -f /vmlinuz

	(the result:vg1-root)
	
sh:grub>search -f /sbin/init

	(the result:vg1-root)

sh:grub> linux  (vg1-root)/vmlinuz root=/dev/vg1/root (tried also with sh:grub> linux  (vg1-root)/vmlinuz root=/dev/sda1)
	
	(the result:[Linux-bzImage, setup=0x3400, size=3bf720] )
	
sh:grub> initrd  (vg1-root)/initrd.img

	(the result:[Initrd, addr=0x377b6000, size=0x839b70] )

sh:grub> boot


After rebooting I came back to sh:grub>


The result of ls command is:

(vg1-srv) (vg1-swap) (vg1-var) (vg1-usr) (vg1-tmp) (vg1-opt) (vg1-home) (vg1-root) (md0) (hd0,1) (hd1) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,1) (hd4) (hd4,1) (hd5) (hd5,1) (hd6) (hd6,1) (hd7) (hd7,1)

Could anyone help me with this problem? What should I do, so the system boots again?

---

### Post by zofiaifoz on 2010-08-24
Nobody? Please help!

---

