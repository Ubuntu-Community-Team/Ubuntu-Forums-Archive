---
title: "glibc detected memory corruption"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by bronenos on 2011-04-17
I reinstalled Kubuntu few days ago and now getting errors on any attempt to install software about glibc detects memory corruption.
As result, any packages finish their installation process but have problem in post-installation scripts. I think it means clearing garbage. And actually it doesn't work.

I can't understand: the problem is inside glibc library or grub-probe (where it appears) or somewhere else?
How to fix? Thanks.

```

bronenos@KuBro:~$ sudo apt-get install swi-prolog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
swi-prolog is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic                                                                            
 *       nvidia-current (260.19.06)...                                                                                                      [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                                                                                        [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
*** glibc detected *** grub-probe: malloc(): memory corruption: 0x0876e0a0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xdaf501]
/lib/libc.so.6(+0x6f2fc)[0xdb22fc]
/lib/libc.so.6(__libc_malloc+0x63)[0xdb3f33]
grub-probe[0x804db32]
grub-probe[0x8057447]
grub-probe[0x8057057]
grub-probe[0x80571aa]
grub-probe[0x806fb1b]
grub-probe[0x80499e3]
grub-probe[0x804a1e8]
/lib/libc.so.6(__libc_start_main+0xe7)[0xd59ce7]
grub-probe[0x80496f1]
======= Memory map: ========
00110000-00112000 rwxp 00000000 00:00 0 
00112000-0012c000 r-xp 00000000 08:04 2752592    /lib/libselinux.so.1
0012c000-0012d000 r-xp 00019000 08:04 2752592    /lib/libselinux.so.1
0012d000-0012e000 rwxp 0001a000 08:04 2752592    /lib/libselinux.so.1
0029c000-0029d000 rwxp 00000000 00:00 0 
0048f000-00491000 r-xp 00000000 08:04 2757131    /lib/libdl-2.12.1.so
00491000-00492000 r-xp 00001000 08:04 2757131    /lib/libdl-2.12.1.so
00492000-00493000 rwxp 00002000 08:04 2757131    /lib/libdl-2.12.1.so
00505000-00506000 r-xp 002a1000 08:04 1835955    /usr/lib/locale/locale-archive
00534000-00550000 r-xp 00000000 08:04 2752770    /lib/libdevmapper.so.1.02.1
00550000-00551000 r-xp 0001b000 08:04 2752770    /lib/libdevmapper.so.1.02.1
00551000-00553000 rwxp 0001c000 08:04 2752770    /lib/libdevmapper.so.1.02.1
00683000-00684000 r-xp 00000000 00:00 0          [vdso]
00684000-00884000 r-xp 00000000 08:04 1835955    /usr/lib/locale/locale-archive
00ada000-00af6000 r-xp 00000000 08:04 2757125    /lib/ld-2.12.1.so
00af6000-00af7000 r-xp 0001b000 08:04 2757125    /lib/ld-2.12.1.so
00af7000-00af8000 rwxp 0001c000 08:04 2757125    /lib/ld-2.12.1.so
00b9d000-00b9e000 rwxp 00000000 00:00 0 
00d43000-00e9a000 r-xp 00000000 08:04 2757128    /lib/libc-2.12.1.so
00e9a000-00e9c000 r-xp 00157000 08:04 2757128    /lib/libc-2.12.1.so
00e9c000-00e9d000 rwxp 00159000 08:04 2757128    /lib/libc-2.12.1.so
00e9d000-00ea0000 rwxp 00000000 00:00 0 
00fd5000-00fef000 r-xp 00000000 08:04 2752572    /lib/libgcc_s.so.1
00fef000-00ff0000 r-xp 00019000 08:04 2752572    /lib/libgcc_s.so.1
00ff0000-00ff1000 rwxp 0001a000 08:04 2752572    /lib/libgcc_s.so.1
08048000-08077000 r-xp 00000000 08:04 1840348    /usr/sbin/grub-probe
08077000-08078000 r-xp 0002e000 08:04 1840348    /usr/sbin/grub-probe
08078000-08079000 rwxp 0002f000 08:04 1840348    /usr/sbin/grub-probe
08079000-080a1000 rwxp 00000000 00:00 0 
0876a000-0880f000 rwxp 00000000 00:00 0          [heap]
b7700000-b7721000 rwxp 00000000 00:00 0 
b7721000-b7800000 ---p 00000000 00:00 0 
bfe4c000-bfe6d000 rwxp 00000000 00:00 0          [stack]
Aborted
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 134
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-28-generic (2.6.35-28.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
 * dkms: running auto installation service for kernel 2.6.35-28-generic                                                                            
 *       nvidia-current (260.19.06)...                                                                                                      [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                                                                                        [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
*** glibc detected *** grub-probe: malloc(): memory corruption: 0x09d320a0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xe1f501]
/lib/libc.so.6(+0x6f2fc)[0xe222fc]
/lib/libc.so.6(__libc_malloc+0x63)[0xe23f33]
grub-probe[0x804db32]
grub-probe[0x8057447]
grub-probe[0x8057057]
grub-probe[0x80571aa]
grub-probe[0x806fb1b]
grub-probe[0x80499e3]
grub-probe[0x804a1e8]
/lib/libc.so.6(__libc_start_main+0xe7)[0xdc9ce7]
grub-probe[0x80496f1]
======= Memory map: ========
002ea000-00304000 r-xp 00000000 08:04 2752592    /lib/libselinux.so.1
00304000-00305000 r-xp 00019000 08:04 2752592    /lib/libselinux.so.1
00305000-00306000 rwxp 0001a000 08:04 2752592    /lib/libselinux.so.1
00370000-0038c000 r-xp 00000000 08:04 2752770    /lib/libdevmapper.so.1.02.1
0038c000-0038d000 r-xp 0001b000 08:04 2752770    /lib/libdevmapper.so.1.02.1
0038d000-0038f000 rwxp 0001c000 08:04 2752770    /lib/libdevmapper.so.1.02.1
0038f000-0058f000 r-xp 00000000 08:04 1835955    /usr/lib/locale/locale-archive
00918000-00919000 r-xp 002a1000 08:04 1835955    /usr/lib/locale/locale-archive
0091e000-0093a000 r-xp 00000000 08:04 2757125    /lib/ld-2.12.1.so
0093a000-0093b000 r-xp 0001b000 08:04 2757125    /lib/ld-2.12.1.so
0093b000-0093c000 rwxp 0001c000 08:04 2757125    /lib/ld-2.12.1.so
00974000-00975000 rwxp 00000000 00:00 0 
00a68000-00a69000 r-xp 00000000 00:00 0          [vdso]
00ad2000-00aec000 r-xp 00000000 08:04 2752572    /lib/libgcc_s.so.1
00aec000-00aed000 r-xp 00019000 08:04 2752572    /lib/libgcc_s.so.1
00aed000-00aee000 rwxp 0001a000 08:04 2752572    /lib/libgcc_s.so.1
00caf000-00cb1000 r-xp 00000000 08:04 2757131    /lib/libdl-2.12.1.so
00cb1000-00cb2000 r-xp 00001000 08:04 2757131    /lib/libdl-2.12.1.so
00cb2000-00cb3000 rwxp 00002000 08:04 2757131    /lib/libdl-2.12.1.so
00d69000-00d6b000 rwxp 00000000 00:00 0 
00db2000-00db3000 rwxp 00000000 00:00 0 
00db3000-00f0a000 r-xp 00000000 08:04 2757128    /lib/libc-2.12.1.so
00f0a000-00f0c000 r-xp 00157000 08:04 2757128    /lib/libc-2.12.1.so
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                     00f0c000-00f0d000 rwxp 00159000 08:04 2757128    /lib/libc-2.12.1.so
00f0d000-00f10000 rwxp 00000000 00:00 0 
08048000-08077000 r-xp 00000000 08:04 1840348    /usr/sbin/grub-probe
08077000-08078000 r-xp 0002e000 08:04 1840348    /usr/sbin/grub-probe
08078000-08079000 rwxp 0002f000 08:04 1840348    /usr/sbin/grub-probe
08079000-080a1000 rwxp 00000000 00:00 0 
09d2e000-09dd3000 rwxp 00000000 00:00 0          [heap]
b7600000-b7621000 rwxp 00000000 00:00 0 
b7621000-b7700000 ---p 00000000 00:00 0 
bfdab000-bfdcc000 rwxp 00000000 00:00 0          [stack]
Aborted
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 134
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bronenos on 2011-04-17
Removed all linux images, that solve this issue

---

