---
title: "kernel module is not added to initrd.img although it seems everything is in place"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by lifeboy on 2011-11-15
I'm building a client boot image for LTSP and have used ltsp-build-client to create the chroot environment for my client.

The server runs Ubuntu Maverick 10.10 64bit and the chroot OS is **Ubuntu Lucid 10.04 32bit**.  Essentially I need to run **10.04** since my client CPU (a vortex86 processor) *doesn't have the cmov instruction*, but is otherwise a 486DX compatible processor.  [SIZE=1][COLOR=DarkGreen](Support for non-cmov processors was stopped in Ubuntu from Maverick upwards)[/COLOR][/SIZE]

So, I have tested my setup with a notebook and all is well. 

However with the vortex86 client _*I need the r6040 ethernet driver kernel module*_.  This is in the Ubuntu sources, but is not compiled into the kernel by default.  I have downloaded and extracted the sources in the chroot at /usr/src/linux-source-2.6.32/ and then copied the /boot/config/config-2.6.32-34-generic file to .config in the sources.  

Then I installed the required tools to build from sources and compiled the modules as follows:

```
# make ARCH=i386 oldconfig && make ARCH=i386 prepare
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
# make ARCH=i386 modules_prepare
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CALL    scripts/checksyscalls.sh
# make ARCH=i386 CONFIG_R6040=m M=drivers/net
  WARNING: Symbol version dump /usr/src/linux-source-2.6.32/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST 274 modules
  CC      drivers/net/3c501.mod.o
  LD [M]  drivers/net/3c501.ko
<snip>
  CC      drivers/net/r6040.mod.o
  LD [M]  drivers/net/r6040.ko
<snip>

```Then, I copied the newly build module (r6040.ko) to /lib/modules/2.6.32-34-generic/kernel/drivers/net/ and added r6040 into the file /lib/modules/2.6.32-34-generic/modules as below:
```
# cat /lib/modules/2.6.32-34-generic/modules.dep | grep r6040
kernel/drivers/net/r6040.ko: kernel/drivers/net/mii.ko

```Inspecting the module shows this:

```
# modinfo /lib/modules/2.6.32-34-generic/kernel/drivers/net/r6040.ko 
filename:       /lib/modules/2.6.32-34-generic/kernel/drivers/net/r6040.ko
version:        0.25 20Aug2009
description:    RDC R6040 NAPI PCI FastEthernet driver
license:        GPL
author:         Sten Wang <sten.wang@rdc.com.tw>,Daniel Gimpelevich <daniel@gimpelevich.san-francisco.ca.us>,Florian Fainelli <florian@openwrt.org>
srcversion:     2396609C2FD05526B238E25
alias:          pci:v000017F3d00006040sv*sd*bc*sc*i*
depends:        mii
vermagic:       2.6.32-34-generic SMP mod_unload modversions 586 

```Just for comparison, I did this for one of the modules that ***does*** load correctly:

```
# modinfo /lib/modules/2.6.32-34-generic/kernel/ubuntu/aufs/aufs.ko 
filename:       /lib/modules/2.6.32-34-generic/kernel/ubuntu/aufs/aufs.ko
version:        2-standalone.tree-20091207
description:    aufs -- Advanced multi layered unification filesystem
author:         Junjiro R. Okajima <aufs-users@lists.sourceforge.net>
license:        GPL
srcversion:     DAA70C879577CB4901122FF
depends:        
vermagic:       2.6.32-34-generic SMP mod_unload modversions 586 
parm:           nwkq:the number of workqueue thread, aufsd (short)
parm:           brs:use <sysfs>/fs/aufs/si_*/brN (int)

```As can be seen, the vermagic is the same as matches the kernel version in both cases.

Also, since r6040.ko depends on mii.ko I also did:

```
# modinfo /lib/modules/2.6.32-34-generic/kernel/drivers/net/mii.ko 
filename:       /lib/modules/2.6.32-34-generic/kernel/drivers/net/mii.ko
license:        GPL
description:    MII hardware support library
author:         Jeff Garzik <jgarzik@pobox.com>
srcversion:     0AC37502D4358344E7C3F7B
depends:        
vermagic:       2.6.32-34-generic SMP mod_unload modversions 586 

```So I added this line to modules.alias

```
# cat /lib/modules/2.6.32-34-generic/modules.alias | grep r6040
alias pci:v000017F3d00006040sv*sd*bc*sc*i* r6040

```Then I finally (after lots of troubleshooting after rebuilding the initramfs and still not finding the r6040 module in the kernel) added this line to /etc/modules and /etc/initramfs-conf/modules.  

```
# cat /etc/modules | grep r6040
r6040
# cat /etc/initramfs-tools/modules | grep r6040
r6040

```It was also suggested somewhere that a file r6040 should be created with content as follows

```

# cat /usr/share/initramfs-tools/modules.d/r6040 
r6040

```I'm pretty sure some of this is superfluous, but here what I then do and find:

```
# update-initramfs -c -k 2.6.32-34-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-34-generic
# umount proc
# exit
exit
# ltsp-update-image --arch=i386
Parallel mksquashfs: Using 12 processors
Creating 4.0 filesystem on /opt/ltsp/images/i386.img.tmp, block size 131072.
[========================================================================================================================================-] 137175/137175 100%
Squashfs 4.0 filesystem, data block size 131072
    uncompressed data, uncompressed metadata, uncompressed fragments
    duplicates are removed
Filesystem size 2054102.44 Kbytes (2005.96 Mbytes)
    90.50% of uncompressed filesystem size (2269661.72 Kbytes)
Inode table size 5571474 bytes (5440.89 Kbytes)
    100.00% of uncompressed inode table size (5571474 bytes)
Directory table size 3529694 bytes (3446.97 Kbytes)
    100.00% of uncompressed directory table size (3529694 bytes)
Number of duplicate files found 50281
Number of inodes 167280
Number of files 138751
Number of fragments 8936
Number of symbolic links  12413
Number of device nodes 86
Number of fifo nodes 0
Number of socket nodes 0
Number of directories 16030
Number of ids (unique uids + gids) 19
Number of uids 3
    root (0)
    man (6)
    libuuid (100)
Number of gids 18
    root (0)
    video (44)
    audio (29)
    tty (5)
    fuse (104)
    kmem (15)
    disk (6)
    shadow (42)
    netdev (106)
    crontab (102)
    mail (8)
    lpadmin (107)
    mlocate (105)
    utmp (43)
    staff (50)
    src (40)
    libuuid (101)
    adm (4)
# ltsp-update-kernels 
Updating /var/lib/tftpboot directories for chroot: /opt/ltsp/i386

```After this I inspect the new kernel image:

```
# lsinitramfs /opt/ltsp/i386/boot/initrd.img-2.6.32-34-generic | egrep r6040
```and find the module is not there. 

:confused: *[COLOR=Blue]Why is this and what am I doing wrong?[/COLOR]*

This doesn't seem to be a specific LTSP problem, but rather a more generic kernel module loading issue.  I cannot use modprobe to add the module into the kernel in the chroot, since modprobe looks for the servers kernel and although the manpage for modprobe lists a -S option to specify the kernel version, Ubuntu balks at this.

---

### Post by lifeboy on 2011-11-21
I posted the solution to the problem on the XCore86 forums at [http://www.deviceonchip.com/index.php?option=com_kunena&func=view&catid=5&id=631&limit=6&limitstart=12&Itemid=85#656](http://www.deviceonchip.com/index.php?option=com_kunena&func=view&catid=5&id=631&limit=6&limitstart=12&Itemid=85#656)

---

### Post by matt_symes on 2011-11-21
Hi

Thanks for posting the solution you found. This is the kind of thing that interests me as well. :biggrin:

Kind regards

---

