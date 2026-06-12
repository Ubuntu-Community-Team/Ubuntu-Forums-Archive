---
title: "Issues after installing linux-image-2.6.35-7-generic"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by anero on 2010-07-09
Hi guys,

I'm running Ubuntu 10.04 and after yesterday's updates (installed through Update Manager) I'm facing some issues on my box.

After installing 2010-07-8 update my keyboard and touchpad (I'm using a Dell Inspiron 1525) stopped working. Using a USB keyboard I was able to run Update Manager again today (2010-07-09) and the issue with the keyboard/touchpad was fixed, but now the wireless card stopped working (the led indicator doesn't turn on when switching on/off the WI-FI).

Below are the logs from both updates, I assume it's an issue with the kernel image.

Thanks,
Diego.

[I]Log started: 2010-07-08  09:14:43
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239258 files and directories currently installed.)
Preparing to replace libpam-modules 1.1.1-2ubuntu2 (using .../libpam-modules_1.1.1-2ubuntu5_i386.deb) ...
Unpacking replacement libpam-modules ...
Processing triggers for man-db ...
Setting up libpam-modules (1.1.1-2ubuntu5) ...

Selecting previously deselected package linux-image-2.6.35-7-generic.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 239258 files and directories currently installed.)
Unpacking linux-image-2.6.35-7-generic (from .../linux-image-2.6.35-7-generic_2.6.35-7.10~lucid1_i386.deb) ...
Done.
Preparing to replace libpam-runtime 1.1.1-2ubuntu2 (using .../libpam-runtime_1.1.1-2ubuntu5_all.deb) ...
Unpacking replacement libpam-runtime ...
Processing triggers for man-db ...
Setting up libpam-runtime (1.1.1-2ubuntu5) ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 243069 files and directories currently installed.)
Preparing to replace libpam0g 1.1.1-2ubuntu2 (using .../libpam0g_1.1.1-2ubuntu5_i386.deb) ...
Unpacking replacement libpam0g ...
Setting up libpam0g (1.1.1-2ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 243069 files and directories currently installed.)
Preparing to replace app-install-data-partner 12.10.04 (using .../app-install-data-partner_12.10.04.3_all.deb) ...
Unpacking replacement app-install-data-partner ...
Preparing to replace libatk1.0-dev 1.30.0-0ubuntu2 (using .../libatk1.0-dev_1.30.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libatk1.0-dev ...
Preparing to replace libatk1.0-0 1.30.0-0ubuntu2 (using .../libatk1.0-0_1.30.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libatk1.0-0 ...
Preparing to replace gir1.0-atk-1.0 1.30.0-0ubuntu2 (using .../gir1.0-atk-1.0_1.30.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement gir1.0-atk-1.0 ...
Preparing to replace libatk1.0-data 1.30.0-0ubuntu2 (using .../libatk1.0-data_1.30.0-0ubuntu2.1_all.deb) ...
Unpacking replacement libatk1.0-data ...
Preparing to replace linux-generic 2.6.32.23.24 (using .../linux-generic_2.6.35.7.8~lucid1_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.32.23.24 (using .../linux-image-generic_2.6.35.7.8~lucid1_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.35-7.
Unpacking linux-headers-2.6.35-7 (from .../linux-headers-2.6.35-7_2.6.35-7.10~lucid1_all.deb) ...
Selecting previously deselected package linux-headers-2.6.35-7-generic.
Unpacking linux-headers-2.6.35-7-generic (from .../linux-headers-2.6.35-7-generic_2.6.35-7.10~lucid1_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.32.23.24 (using .../linux-headers-generic_2.6.35.7.8~lucid1_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.34-5.12~lucid1 (using .../linux-libc-dev_2.6.35-7.10~lucid1_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for software-center ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for python-central ...
Setting up linux-image-2.6.35-7-generic (2.6.35-7.10~lucid1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-7-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-7-generic
Found initrd image: /boot/initrd.img-2.6.35-7-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic

Setting up app-install-data-partner (12.10.04.3) ...

Setting up libatk1.0-0 (1.30.0-0ubuntu2.1) ...

Setting up libatk1.0-dev (1.30.0-0ubuntu2.1) ...
Setting up gir1.0-atk-1.0 (1.30.0-0ubuntu2.1) ...
Setting up libatk1.0-data (1.30.0-0ubuntu2.1) ...
Setting up linux-image-generic (2.6.35.7.8~lucid1) ...
Setting up linux-generic (2.6.35.7.8~lucid1) ...
Setting up linux-headers-2.6.35-7 (2.6.35-7.10~lucid1) ...
Setting up linux-headers-2.6.35-7-generic (2.6.35-7.10~lucid1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic

Setting up linux-headers-generic (2.6.35.7.8~lucid1) ...
Setting up linux-libc-dev (2.6.35-7.10~lucid1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2010-07-08  09:20:30

Log started: 2010-07-09  13:10:09
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 262922 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-7-generic 2.6.35-7.10~lucid1 (using .../linux-image-2.6.35-7-generic_2.6.35-7.11~lucid2_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-7-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-7-generic
Found initrd image: /boot/initrd.img-2.6.35-7-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace libpng12-dev 1.2.42-1ubuntu2 (using .../libpng12-dev_1.2.42-1ubuntu2.1_i386.deb) ...
Unpacking replacement libpng12-dev ...
Preparing to replace libpng12-0 1.2.42-1ubuntu2 (using .../libpng12-0_1.2.42-1ubuntu2.1_i386.deb) ...
Unpacking replacement libpng12-0 ...
Preparing to replace linux-headers-2.6.35-7 2.6.35-7.10~lucid1 (using .../linux-headers-2.6.35-7_2.6.35-7.11~lucid2_all.deb) ...
Unpacking replacement linux-headers-2.6.35-7 ...
Preparing to replace linux-headers-2.6.35-7-generic 2.6.35-7.10~lucid1 (using .../linux-headers-2.6.35-7-generic_2.6.35-7.11~lucid2_i386.deb) ...
Unpacking replacement linux-headers-2.6.35-7-generic ...
Preparing to replace linux-libc-dev 2.6.35-7.10~lucid1 (using .../linux-libc-dev_2.6.35-7.11~lucid2_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace glippy 0.0.5.6-2 (using .../glippy_0.0.5.9-1_i386.deb) ...
Unpacking replacement glippy ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up linux-image-2.6.35-7-generic (2.6.35-7.11~lucid2) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-7-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-7.10~lucid1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-7.10~lucid1 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-7-generic
Found initrd image: /boot/initrd.img-2.6.35-7-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic

Setting up libpng12-0 (1.2.42-1ubuntu2.1) ...

Setting up libpng12-dev (1.2.42-1ubuntu2.1) ...
Setting up linux-headers-2.6.35-7 (2.6.35-7.11~lucid2) ...
Setting up linux-headers-2.6.35-7-generic (2.6.35-7.11~lucid2) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-7-generic /boot/vmlinuz-2.6.35-7-generic

Setting up linux-libc-dev (2.6.35-7.11~lucid2) ...
Setting up glippy (0.0.5.9-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2010-07-09  13:13:24[/I]

---

### Post by dino99 on 2010-07-09
you have enough kernels to boot on, if one of them is broken , use the other

why all that blah blah ? (useless)

---

### Post by mikewhatever on 2010-07-09
Did I miss something, or was 2.6.35 really provided as an update for Lucid? I don't think it's been out of testing yet.

---

### Post by anero on 2010-07-09
2.6.35 was provided as update from official PPA

---

### Post by turezky on 2010-07-11
I have the same issue. Had to rollback to 2.6.32.
Is the problem w/ wifi solved yet? How can completely remove the newer kernel safely?

---

