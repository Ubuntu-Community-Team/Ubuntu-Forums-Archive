---
title: "[SOLVED] &amp;quot;Alert! &amp;lt;root file system&amp;gt; does not exist&amp;quot; during boot after updating Gutsy"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by alina.bolero on 2007-11-02
Things were going as well as could be expected for Gutsy running on my HP Pavilion dv8000.  Then I noticed that my repositories were unchecked in my package manager.  The updater then promptly informed me of about 600 waiting updates.  I kicked them off, started a reboot, and it never came back up.

I get this during boot:

```

ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold
...
Begin: Waiting for root file system ... ...
Marking TSC unstable due to: possible TSC halt in C2
Time: acpi_pm clocksource has been installed

```

it then hangs for a few minutes, and then says

```

Done.
Alert! /dev/hda3 does not exist. Dropping to a shell!

```

I then cat out my loaded modules and boot line as suggested

```

(initramfs) cat /proc/modules
thermal ...
processor ...
fan ...
capability ...
commoncap ...
(initramfs) cat /proc/cmdline
root=/dev/hda3 ro

```

My root file system is a reiserfs.  I'm suspicious that perhaps there is a reiserfs kernel module that is not getting loaded.  Any thoughts on how to fix this?

-Alina

---

### Post by alina.bolero on 2007-11-02
Trying to figure out this initramfs stuff.

I went ahead and added reiserfs to my /etc/initramfs-tools/modules:

```

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
reiserfs

```

I then, from the live CD, chrooted into my root filesystem to update initramfs:

```

$ sudo /bin/bash
# mkdir /mnt/hda3
# mount /dev/hda3 /mnt/hda3
# mount /dev/hda1 /mnt/hda3/boot
# mount -t proc none /mnt/hda3/proc
# mount -o bind /dev /mnt/hda3/dev
# chroot /mnt/hda3 /bin/bash
# ldconfig
# source /etc/profile
# update-initramfs -u -k 2.6.22-14-generic
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
cp: cannot stat `/lib/udev/hotplug.functions': No such file or directory
cpio: ./lib/udev/ide.agent: Cannot stat: No such file or directory

```

rebooting .... and .... nope

cat /proc/modules shows reiserfs in the list now, but I still get the same error.

I'm out of ideas.  Anyone?

---

### Post by alina.bolero on 2007-11-02
well this just keeps getting weirder.  Once I chroot in, I took a stab at reinstalling the bootloader ala:

```

# /usr/sbin/grub-install --no-floppy /dev/hda
Could not find device for /boot: Not found or not a block device.

```

so I tried to use grub directly instead ...

```

# grub
grub> find /grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/grub/stage2 /grub/menu.lst
"... succeeded
Done.

grub> quit

```

my menu.lst looks like this:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/hda3 ro
initrd          /initrd.img-2.6.22-14-generic

```

good ref on grub repair:  [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair")

rebooting ...and .... nope

**pounding head against wall repeatedly**    whaaaaaaa!!!!!

also did an update in the chroot for good measure:

```

# apt-get update
# apt-get dist-upgrade

```

but it didn't help

---

### Post by Schuva on 2007-11-02
Try a reinstall?

---

### Post by alina.bolero on 2007-11-02
> **Schuva said:**
> Try a reinstall?

OK.   If anyone has anything PRODUCTIVE to add !!!!!!!!!!   :mad:

love you hun!

---

### Post by alina.bolero on 2007-11-02
The whole SLAB/SLUB change with the new Gutsy kernel breaking suspend on my lappy with an ATI card was really pissing me off as well, so it seems it might be time to compile the kernel myself in hopes of fixing this problem as well.

I'm now following Sean's Blog on [Fixing the Suspend Problem with Ubuntu 7.10 Gutsy Gibbon and Proprietary ATI Driver]("http://blog.vaxius.net/?p=19")

```

# apt-get install build-essential kernel-package linux-source
# cd /usr/src
# rm linux
# tar xvfj linux-source-2.6.22.tar.bz2
# ln -s linux-source-2.6.22 linux
# cd /usr/src/linux
# make menuconfig
# make-kpkg clean
# make-kpkg --append-to-version=-with-slab kernel_image kernel_headers --initrd binary
# cd ..
# dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb

```

.config posted to: [http://pastebin.ca/759284]("http://pastebin.ca/759284")

that kernel will at least boot, but a few things seem to be broken, probably based on poor kernel option selections on my part.  The most annoying problem though is that X won't start.  I'm suspicious that I may need to reinstall the ati driver, so I'm continuing on with my own slightly modified version of Sean's blog ...

```

# apt-get install module-assistant dh-make debhelper debconf libstdc++5
# cd /usr/src
# wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run
# ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
# mv /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/fglrx/libGL.so.1.2.xlibmesa.bak
# dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb xorg-driver-fglrx-dev_8.42.3-1_i386.deb fglrx-amdcccle_8.42.3-1_i386.deb
# rm /usr/src/fglrx-kernel*.deb
# apt-get -f install
# rm -f linux
# ln -s linux-headers-2.6.22.9-with-slab linux
# export KERNELDIRS=/usr/src/linux
# module-assistant prepare
# module-assistant update
# module-assistant build fglrx
# module-assistant install fglrx

```

the module-assistant install fglrx command yelled at me about:

```

Package fglrx-kernel-source was not built successfully, see /var/cache/modass/fglrx-kernel-source*buildlog* for details!

```

but when I went and looked at /var/cache/modass/fglrx-kernel-source.buildlog.2.6.22.9-with-slab.1194179042 I didn't see any sign of errors, and it responded with:

```

Selecting previously deselected package fglrx-kernel-2.6.22.9-with-slab.
(Reading database ... 159466 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.22.9-with-slab (from .../fglrx-kernel-2.6.22.9-with-slab_8.42.3-1+2.6.22.9-with-slab-10.00.Custom_i386.deb) ...
Setting up fglrx-kernel-2.6.22.9-with-slab (8.42.3-1+2.6.22.9-with-slab-10.00.Custom) ...

```

subsequent runs say:

```

Version 8.42.3-1+2.6.22.9-with-slab-10.00.Custom of fglrx-kernel-2.6.22.9-with-slab already installed, skipping.

```

so I'm running with the assumption that's a good install.   continuing ...

```

# mkdir /lib/modules/2.6.22.9-with-slab/volatile
# ln -s /lib/modules/2.6.22.9-with-slab/misc/fglrx.ko /lib/modules/2.6.22.9-with-slab/volatile/fglrx.ko

```

rebooting ...

well, I was able to boot up and even start X, but things are running horribly!   no WORSE!  the HD is thrashing, usb mouse doesn't work, touchpad is flaky, no audio, and the logs are just chalked full of errors.

but besides that ..... heh

I'm now going to start some posts about these specific errors related to my new kernel, since this thread seems to have turned more into a personal blog, than a help forum!    -aside from the snide remark from the aforementioned lovely young lady  **grumble**

---

### Post by alina.bolero on 2007-11-05
well, whatever the Gutsy update broke, it CAN be fixed by making a change to the kernel options, I just don't know which one!  I've compiled my own kernel, selecting options myself, and gotten past the "Alert! <root file system> does not exist" problem.  However, my kernel seems to leave much to be desired.  If I base my /usr/src/linux/.config off of either config-2.6.20-16-generic or config-2.6.22-14-generic, I end up getting the boot hang.

There are so many differences between what I had selected and what the "official" kernel has it makes it very difficult to find the culprit.  I tried compiling reiserfs directly into the kernel, thinking that might help, but it didn't.

:confused:

---

### Post by alina.bolero on 2007-11-05
Don't know why I didn't notice this before.   The last line of my dmesg when my boot hangs is:

```

Adding 996020k swap on /dev/hda2.  Priority:-1 extents:1 across:996020k

```

made sure my swap was enabled this time in my chroot when building the kernel, and added the following to my /etc/initramfs-tools/modules

```

ide_disk
ata_generic
lib_ata
scsi_mod
reiserfs

```

it didn't help, still hangs in the same place.

I'm really saddened by Gutsy.  I was holding out alot of hope for this distro.  I'm now considering my options for a complete reinstall, since I'm at the ended of my rope and already wasted more than 30 hours on this issue.

---

### Post by alina.bolero on 2007-11-06
well, for the official solution, refer to Schuva's comment above.   sigh ........

---

