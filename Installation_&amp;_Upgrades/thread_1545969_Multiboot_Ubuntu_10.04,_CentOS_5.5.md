---
title: "Multiboot Ubuntu 10.04, CentOS 5.5"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by ublintu on 2010-08-04
Hi,
I decided to install my 4th OS, centos. I had some problem and I want to share my experience in this case. After several install and a few kernel panic message, I could successfully dual booted with Ubuntu 10.04 and centos5.5.
First:
Boot from DVD and I got kernel panic. A bios update solved my problem (MSI).
Second:
When I installed centos without grub and after the install when I wanted to boot in I got something like this: Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
after 4 days I found out this:

1. I installed every OS, Ubuntu was the last one.
2. I left an unpartitioned free place for centos
3. I installed centos at last. During centos installation, at partitioning, choose "create custom layout"
4. Choose the free place as / and on the next screen you can choose, do NOT install grub.

5. Reboot > in grub choose Ubuntu 10.04 (in my case centos5 already  was listed there, but don't go there), because we need to edit the  grub.cfg file in ubuntu
My original grub.cfg file, (centos part) was like this:

menuentry "CentOS release 5.5 (Final) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bc47e87e-88c6-4756-8f47-361298b23a16
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb3
}

I changed it for this:

menuentry "CentOS release 5.5 (Final) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bc47e87e-88c6-4756-8f47-361298b23a16
    linux /boot/vmlinuz-2.6.18-194.el5 root=UUID=bc47e87e-88c6-4756-8f47-361298b23a16
        initrd /boot/initrd-2.6.18-194.el5.img
}

save, restart and this time I could boot in to centos
I hope this will help to the others.

EDIT:
After Ubuntu kernel update, you need to edit grub.cfg again!

---

### Post by clem.chong@gmail.com on 2010-10-03
This article helped me a lot,thank you.
NOTE:"bc47e87e-88c6-4756-8f47-361298b23a16" is a variable depend on your machine,you should look up the value after "search --no-floppy --fs-uuid --set" to set the correct value.

---

