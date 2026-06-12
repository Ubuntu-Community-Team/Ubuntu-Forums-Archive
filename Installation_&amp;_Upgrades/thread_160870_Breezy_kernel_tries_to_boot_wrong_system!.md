---
title: "Breezy kernel tries to boot wrong system!"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by johnpipe on 2006-04-15
Hi, I've been searching for info on the symptoms I've been having in trying to get 2.6.12 to boot on  breezy (I had a problematic upgrade which didn't install the new kernel and had to do a manual kernel install).

When selecting the new kernel from lilo (multi-boot system), the initrd boots and tries to bring up redhat (which doesn't work, of course) from hda9 instead of ubuntu on hdb9, which seems to have something to do with what's going on with the initial ramdisk (breezy has no problem booting from the hoary kernel).  

I decided to check what I could of the differences between initrd for 2.6.10 (hoary kernel)  v.s. 2.6.12 (breezy kernel):

johnpipe@linus:~$ file /boot/initrd.img-2.6.10-5-386
/boot/initrd.img-2.6.10-5-386: Linux Compressed ROM File System data, little endian size 4399104 version #2 sorted_dirs CRC 0xabeab197, edition 0, 2601 blocks, 328 files
johnpipe@linus:~$ file /boot/initrd.img-2.6.12-10-386
/boot/initrd.img-2.6.12-10-386: gzip compressed data, from Unix, max compressionjohnpipe@linus:~$

The 2.6.10 kernel boots OK, but the 2.6.12 doesn't. I suspect the initrd itself being the cause of the problem, unless there have been changes to account for the above differences.

Does anyone know why the ubuntu hoary kernel has a cramfs as it's initrd, and breezy doesn't? Is it supposed to be this way? The 2.6.12 initrd is as installed from the kernel package.

Here are the pertinent lilo.conf entries (multi-boot system w/ 5 distributions):

boot=/dev/hda
map=/boot/map
install=/boot/boot.b

# other, non-pertinent lilo entries, have been omitted from this posting

image=/lilo/ubuntu/boot/vmlinuz-2.6.10-5-386
        label=ubuntu
        initrd=/lilo/ubuntu/boot/initrd.img-2.6.10-5-386
        read-only
        root=/dev/hdb9
        append=irqpoll # work-around kernel-bug affecting eth0; 
                                  #should not need for 2.6.12.


image=/lilo/ubuntu/boot/vmlinuz-2.6.12-10-386
        label=ub2612
        initrd=/lilo/ubuntu/boot/initrd.img-2.6.12-10-386
        read-only
        root=/dev/hdb9

Any clues to solving this boot problem are appreciated!

Thanks,  Johnpipe

---

