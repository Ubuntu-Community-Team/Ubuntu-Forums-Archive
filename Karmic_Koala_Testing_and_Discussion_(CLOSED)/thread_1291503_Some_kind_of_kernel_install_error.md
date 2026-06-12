---
title: "Some kind of kernel install error?"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by !@!@! on 2009-10-14
Example of me installing scanmem:
```
sudo aptitude install scanmem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  libreadline5{a} scanmem 
The following partially installed packages will be configured:
  linux-generic linux-headers-2.6.31-13-generic 
  linux-headers-2.6.31-14-generic linux-headers-generic 
  linux-image-2.6.31-13-generic linux-image-2.6.31-14-generic 
  linux-image-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 176kB of archives. After unpacking 492kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://ca.archive.ubuntu.com karmic/main libreadline5 5.2-6 [147kB]
Get:2 http://ca.archive.ubuntu.com karmic/universe scanmem 0.07-7 [28.6kB]
Fetched 176kB in 2s (78.4kB/s)      
Selecting previously deselected package libreadline5.
(Reading database ... 162076 files and directories currently installed.)
Unpacking libreadline5 (from .../libreadline5_5.2-6_amd64.deb) ...
Selecting previously deselected package scanmem.
Unpacking scanmem (from .../scanmem_0.07-7_amd64.deb) ...
Processing triggers for man-db ...
Setting up linux-image-2.6.31-13-generic (2.6.31-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-13.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-13.44 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-13-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-13-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-14-generic (2.6.31-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-14-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-14-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-14-generic; however:
  Package linux-image-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.14.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-13-generic (2.6.31-13.45) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        close failed in file object destructor:
Error in sys.excepthook:

Original exception was:
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-13-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-13-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.31-14-generic (2.6.31-14.46) ...
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-14-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-14-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already

 linux-headers-generic depends on linux-headers-2.6.31-14-generic; however:
  Package linux-headers-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libreadline5 (5.2-6) ...

Setting up scanmem (0.07-7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.31-13-generic
 linux-image-2.6.31-14-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-13-generic
 linux-headers-2.6.31-14-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-headers-2.6.31-14-generic (2.6.31-14.46) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-14-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-14-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-14-generic (2.6.31-14.46) ...
Running depmod.
close failed in file object destructor:
Error in sys.excepthook:

Original exception was:
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-14-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-14-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-14-generic; however:
  Package linux-image-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-13-generic (2.6.31-13.45) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-13-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-13-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-13-generic (2.6.31-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-13.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-13.44 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-13-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
debconf: Unable to load Debconf::Element::Dialog. Failed because: Can't locate Debconf/Element/Dialog.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 24) line 2, <GEN0> line 2.
BEGIN failed--compilation aborted at (eval 24) line 2, <GEN0> line 2.

Can't locate object method "new" via package "Debconf::Element::Dialog" (perhaps you forgot to load "Debconf::Element::Dialog"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN0> line 2.
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-13-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.14.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-14-generic; however:
  Package linux-headers-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.31-14-generic
 linux-image-2.6.31-14-generic
 linux-image-generic
 linux-headers-2.6.31-13-generic
 linux-image-2.6.31-13-generic
 linux-generic
 linux-headers-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```

After updating I now get this error after installing/updating/upgrading (anything w/ aptitude). What do I need to do? :d

P.S.: Nothing is actually wrong, fglrx functions, I can boot fine, but there seems to be something wrong with it configuring itself. :s

---

### Post by sadahalli on 2009-10-14
Same here..After running the Update manager, a message was displayed to run the command 'sudo dpkg --configure -a' manually. When I run this, I get the following message.

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.31-14-generic (2.6.31-14.46) ...
Running depmod.
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/fs/ocfs2/ocfs2.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/char/synclink.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/usb/serial/ipaq.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/infiniband/hw/mthca/ib_mthca.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/ubuntu/aufs/aufs.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-14-generic; however:
  Package linux-image-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-13-generic (2.6.31-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
cpio: ./lib/udev/ata_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-13-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.14.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
cpio: ./lib/udev/ata_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-13-generic
dpkg: subprocess installed post-installation script returned error exit status 1
naveensn@naveensn-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.31-14-generic (2.6.31-14.46) ...
Running depmod.
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/fs/ocfs2/ocfs2.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/char/synclink.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/usb/serial/ipaq.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/drivers/infiniband/hw/mthca/ib_mthca.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/kernel/ubuntu/aufs/aufs.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-14-generic; however:
  Package linux-image-2.6.31-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.31-13-generic (2.6.31-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
cpio: ./lib/udev/ata_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-13-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.14.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-13-generic
cpio: ./lib/udev/ata_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-13-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by !@!@! on 2009-10-15
Anyone help please? Problem still persists. VERY annoying how long it takes just to install an app because of it configuring the kernel every time.

EDIT:

SOLUTION!
>It's nvidia-common. I don't know what the f*ck I'm doing so don't try this at home... lol
>ALSO NOTE: if you have an nVidia card...obviously common sense to not delete this...
> sudo rm /etc/kernel/header_postinst.d/nvidia-common && sudo rm /etc/kernel/postinst.d/nvidia-common


---

