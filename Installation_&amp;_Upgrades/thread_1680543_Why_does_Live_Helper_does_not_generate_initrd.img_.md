---
title: "Why does Live Helper does not generate initrd.img if a custom kernel is applied"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by alexanderzubin on 2011-02-02
I'm trying to understand why Debian Live Helper (version 2.0~a19-1) is not creating initrd.img-2.6.36 image if a custom linux-image-2.6.36_amd64.deb is applied to liveISO/config/chroot_local-packages/ folder.

I'm compiling my kernel using the following command:

fakeroot make-kpkg clean
fakeroot make-kpkg --initrd --revision 1 kernel_image

and I've tried initramfs-tools (0.92o) LENNY and initramfs-tools (0.98.8) 
SID

with the following command for custom kernel (--linux-packages "none"):

lh config \
        --syslinux-timeout 15 -b iso -d sid -a amd64 \
        --binary-indices none \
        --apt-recommends true --linux-packages "none" \
        --linux-flavours "" \
        --packages "squashfs-tools live-initramfs \ 
             openssh-server atftp bc lshw grub-legacy \
             wput ethtool parted"
lh build

I see the following behavior:

######
Setting up linux-image-2.6.36 (1) ...^M
^M
 Hmm. There is a symbolic link /lib/modules/2.6.36/build^M
 However, I can not read it: No such file or directory^M
 Therefore, I am deleting /lib/modules/2.6.36/build^M
^M
^M
 Hmm. The package shipped with a symbolic link /lib/modules/2.6.36/source^M
 However, I can not read the target: No such file or directory^M
 Therefore, I am deleting /lib/modules/2.6.36/source^M
^M
Running depmod.^M
Examining /etc/kernel/postinst.d.^M
Setting up openssh-blacklist (0.4.1) ...^M

#######

If however I use the previous command, but with --linux-packages "", the default Debian kernel gets installed (linux-image-2.6.32-5-amd64 (2.6.32-30)) and initrd.img is generated for my kernel custom kernel and the default one


###############

Setting up linux-image-2.6.32-5-amd64 (2.6.32-30) ...^M
Running depmod.^M
Running update-initramfs.^M
update-initramfs: Generating /boot/initrd.img-2.6.32-5-amd64^M
Examining /etc/kernel/postinst.d.^M
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.32-5-amd64 /boot/vmlinuz-2.6.32-5-amd64^M
Setting up linux-image-2.6.36 (1) ...^M
^M
 Hmm. There is a symbolic link /lib/modules/2.6.36/build^M
 However, I can not read it: No such file or directory^M
 Therefore, I am deleting /lib/modules/2.6.36/build^M
^M
^M
 Hmm. The package shipped with a symbolic link /lib/modules/2.6.36/source^M
 However, I can not read the target: No such file or directory^M
 Therefore, I am deleting /lib/modules/2.6.36/source^M
^M
Running depmod.^M
Examining /etc/kernel/postinst.d.^M
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.36 /boot/vmlinuz-2.6.36^M
update-initramfs: Generating /boot/initrd.img-2.6.36^M
Setting up openssh-blacklist (0.4.1) ...^M

########

I do not understand how the default kernel is compiled and packaged and why my custom kernel skips this step and fails couple line after

P: Begin install linux-image...
cp: cannot stat `chroot/boot/initrd.img-*': No such file or directory
P: Begin unmounting filesystems...

---

### Post by alexanderzubin on 2011-02-02
BTW. I'm using kernel-package (12.036)

---

### Post by alexanderzubin on 2011-02-04
I was able to install official SID kernel-image (linux-image-2.6.32-5-amd64_2.6.32-30_amd64.deb) on Lenny Live CD, by simply copying the file into ./config/chroot_local-packages. However, still no luck with custom made kernel (linux-image-2.6.36-amd64_2.6.36_amd64.deb).

P: Begin installing local packages lists...
P: Begin install linux-image...
cp: cannot stat `chroot/boot/initrd.img-*': No such file or directory
P: Begin unmounting filesystems...

:confused:


the initrd.img-* is not getting created on my custom kernel but it is constantly updated if I install official kernel image.

---

### Post by alexanderzubin on 2011-02-04
The official debian linux-image is calling for

Running update-initramfs.

My custom kernel does not :(

---

### Post by alexanderzubin on 2011-02-04
I've managed to fix the build process. I had to copy the script "/usr/share/live-helper/examples/hooks/all_chroot_update-initramfs.sh" to liveISO/config/chroot_local-hooks/.


Now my ISO boots into busybox with my custom kernel. The new problem i see now is that AUFS support is not available in kernel 2.6.36. SquashFS yes, AUFS no.


Damn.....

---

### Post by alexanderzubin on 2011-02-07
To resolve issue with AUFS on kernel 2.6.36 use the steps

# git clone [http://git.c3sl.ufpr.br/pub/scm/aufs/aufs2-standalone.git](http://git.c3sl.ufpr.br/pub/scm/aufs/aufs2-standalone.git) aufs2-standalone.git
# cd aufs2-standalone.git
# git checkout origin/aufs2.1-36
# git checkout -b origin/aufs2.1-36


# cd ../linux-2.6.36
# patch -p1 < ../aufs2-standalone.git/aufs2-kbuild.patch
# patch -p1 < ../aufs2-standalone.git/aufs2-base.patch
# patch -p1 < ../aufs2-standalone.git/aufs2-standalone.patch

# cp -v -r ../aufs2-standalone.git/{include/,fs/,Documentation/} .

# make

This will create the kernel 2.6.36 with AUFS support

---

### Post by alexanderzubin on 2011-02-07
Then you can do

# make menuconfig 

to set these the AUFS parameters

CONFIG_AUFS_FS=y
CONFIG_AUFS_BRANCH_MAX_127=y
# CONFIG_AUFS_BRANCH_MAX_511 is not set
# CONFIG_AUFS_BRANCH_MAX_1023 is not set
# CONFIG_AUFS_BRANCH_MAX_32767 is not set
CONFIG_AUFS_SBILIST=y
# CONFIG_AUFS_HNOTIFY is not set
# CONFIG_AUFS_EXPORT is not set
# CONFIG_AUFS_RDU is not set
# CONFIG_AUFS_SP_IATTR is not set
# CONFIG_AUFS_SHWH is not set
CONFIG_AUFS_BR_RAMFS=y
CONFIG_AUFS_BDEV_LOOP=y
# CONFIG_AUFS_DEBUG is not set


fakeroot make-kpkg --initrd --append-to-version=-amd64 --revision=2.6.36 kernel_image.

Enjoy.

---

### Post by alexanderzubin on 2011-02-10
To start building custom Live CD with custom initrd for kernel modules and vmxnet3 modules use the commands below.


lh config \
        --syslinux-timeout 15 -b iso -d lenny -a amd64 --binary-indices none \
        --apt-recommends true --memtest none --linux-packages "none" --linux-flavours "" \
        --packages "openssh-server atftp wput ethtool"
mkdir -p /liveISO/config/chroot_local-includes/etc/default
mkdir -p /liveISO/config/chroot_local-includes/etc/initramfs-tools/
cp -f linux-image-2.6.36-amd.deb /liveISO/config/chroot_local-packages/
cp -f /initramfs-tools_0.98.8_all.deb /liveISO/config/chroot_local-packages/
cp -f /live-boot_2.0.15-1_all.deb /liveISO/config/chroot_local-packages/
cp -f /live-boot-initramfs-tools_2.0.15-1_all.deb /liveISO/config/chroot_local-packages/
cp -f /live-config_2.0.15-1_all.deb /liveISO/config/chroot_local-packages/
cp -f /live-config-sysvinit_2.0.15-1_all.deb /liveISO/config/chroot_local-packages/
cp -f /live-initramfs_2.0.15-1_all.deb /liveISO/config/chroot_local-packages/
cp -f /squashfs-tools_4.1-3_amd64.deb /liveISO/config/chroot_local-packages/
cp -f /liblzma2_5.0.0-2_amd64.deb /liveISO/config/chroot_local-packages/
cp -f /vmxnet3_8.4.5-324285_amd64.deb /liveISO/config/chroot_local-packages/
cp -f /modules_list /liveISO/config/chroot_local-includes/etc/initramfs-tools/modules
cp -f /all_chroot_update-initramfs.sh /liveISO/config/chroot_local-hooks/
cp -f 01-update_password.sh /liveISO/config/chroot_local-hooks/
cd /liveISO
lh build


These command will create binary ISO with proper initrd.img-2.6.36-amd that will load network and scsi drivers before squashfs is loaded. This is useful for PXE installation, since CD install has access to squashfs regardless of initrd. The main challenge is to load network and HDD drivers in PXE environment in advance. 


To create a custom Debian package for VMware vmxnet3 driver use the following(please note that you will need regular Debian package file for Debian packager):

tar -xf /usr/src/vmxnet3.tar -C /usr/src/modules
cp -f /vmxnet3_Makefile /usr/src/modules/vmxnet3-only/Makefile
mkdir -p /usr/src/modules/vmxnet3-only/debian
cp -f /vmxnet3_rules /usr/src/modules/vmxnet3-only/debian/rules
cp -f /vmxnet3_control /usr/src/modules/vmxnet3-only/debian/control
cp -f /vmxnet3_changelog /usr/src/modules/vmxnet3-only/debian/changelog
cd /usr/src/linux-2.6.36
fakeroot make-kpkg --append-to-version=-amd64 --revision=2.6.36 --added_modules $(CURDIR)/usr/src/modules/vmxnet3-only/ modules_image

This will create file vmxnet3_8.4.5-324285_amd64.deb described above

Enjoy

---

### Post by alexanderzubin on 2011-02-10
Kernel name convention is critical for custom kernel and Live Helper (2.0~a19-1)

For 32bit use this:
linux-image-2.6.36-686_2.6.36_i386.deb

For 64bit use this:
linux-image-2.6.36-amd64_2.6.36_amd64.deb

Command to generate these:

fakeroot make-kpkg --initrd --append-to-version=-686 --revision=2.6.36 kernel_image

fakeroot make-kpkg --initrd --append-to-version=-amd64 --revision=2.6.36 kernel_image

---

