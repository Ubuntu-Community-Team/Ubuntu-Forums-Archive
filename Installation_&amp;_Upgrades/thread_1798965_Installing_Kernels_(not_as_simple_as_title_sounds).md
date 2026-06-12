---
title: "Installing Kernels (not as simple as title sounds)"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by Reamer on 2011-07-06
EDIT: PLEASE CLOSE, FINALLY GOT ANSWER ON BACKTRACK FORUMS.

First of all, if this is in the wrong section, mods, please move it. I just took a best guess.

Second, this is actually done on BackTrack 5 which is based off of Ubuntu 10.04, just so when I mention Ubuntu then it doesn't get confusing. I have tried posting in the BackTrack forums but they have to have every thread reviewed by an admin and after 8 hours of waiting (I have waited longer and sometimes never happens) to see if my thread would get posted I am getting more desperate.

Thank you for your patience.

I am trying to replace the 2.6.38 kernel with the 2.6.32-23 kernel because it works much better on my laptop (Dell Inspiron 14R n4010). The files are in .deb files so I used "dpkg -i file.deb" to install them. The headers installed without error, and the image seems to, but I am not 100% what the output I'm getting during the install is saying so I figured I would let y'all take a look at it.

```


root@bt:~# dpkg -i linux-image-2.6.32-23-* > dpkgoutput.txt
Examining /etc/kernel/preinst.d/
Done.
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38
Found initrd image: /boot/initrd.img-2.6.38
Found linux image: /boot/vmlinuz-2.6.38.old
Found initrd image: /boot/initrd.img-2.6.38
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda6
done
Examining /etc/kernel/postrm.d .
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-23.38~kamal~i915bri~3e was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-23.38~kamal~i915bri~3e was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38
Found initrd image: /boot/initrd.img-2.6.38
Found linux image: /boot/vmlinuz-2.6.38.old
Found initrd image: /boot/initrd.img-2.6.38
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda6
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic

```

NOTE: The listed entry for the 2.6.23-32 kernel is for my Ubuntu 10.04 partition and is NOT the kernel that I installed inside BackTrack. Is there a conflict when using the same kernel on two different partitions?

Thank you for all of the help.

---

