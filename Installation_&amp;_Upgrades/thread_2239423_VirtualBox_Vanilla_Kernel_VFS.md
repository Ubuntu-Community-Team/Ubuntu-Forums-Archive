---
title: "VirtualBox Vanilla Kernel VFS"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by 3246251196 on 2014-08-13
I have tried to search for the answer for this for a while but I am stuck.

I have created a machine in virtualbox which is running Ubuntu 0610. I am then compiling kernel version 2.6.15. I have been using

```

make defconfig
make
make modules_install
make install
cd /boot
updateramfs -u -k 2.6.15
update-grub

```

I have then went into menu.lst and removed quiet so I can see some more output.

Then I am hitting a brick well when booting with:

```

VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

So, I tried

```

make yestoallconfig (paraphrased)

```

Then installed that version of the kernel - which does not show the error. But it gets stuck on some other ACPI issue. Anyway, I would prefer a default stripped down config. I guess I can run diffs between the configs and look at those but I am just wondering if someone knows off hand what the issue is.

I have configured the kernel to allow AHCI support for SATA as that seems to the configuration of the drives in the VB machine in settings. Still - a kernel panic.

I have tried setting the UUID rather than /dev/sda1 but that does not improve the situation. Perhaps I need to configure more things to be configured...

My devices.map shows (hd0) /dev/sda.

Basically, I just wish to install a vanilla kernel and boot into that. Does anyone know specifically what the issue is in my configuration file?

Cheers.

---

### Post by 3246251196 on 2014-08-16
Okay, I have found that running 0504 Ubuntu Hoary Hedgehog rather than 0610 worked a bunch better.

This is all because it is nice to be able to know that you can compile the kernel suggested in the book "Understanding the Linux Kernel (O'Reilly) Edition 3". This book works with 2.6.11.

Soon after 0504 (HH) mkinitrd was deprecated in favour of mkinitramfs. Also, the binutils were - naturally - upgrades to version greater than 2.15* to 2.16*; this means the annoyance of having to patch some source code to get things to compile. Things changed to far, like tring to merge some branch into trunk after too many changes have happened. I found that using this older version which, by default, used kernel version 2.10.* helped a lot. It has the gcc-3.3, bin-utils 2.15 etc.

This enabled

```

make defconfig
make
make modules
make modules_install
make install
cd /boot
initrd -o /boot/initrd.img-2.6.11 2.6.11 **
update-grub
reboot

```

to just *work*.

So, it probably was downgrading to a version of Ubuntu of about that era that sorted the issue out. However, there is still an unknown because this time, when creating a virtual machine, I removed the vdi disk from SATA and put it into IDE. I wanted to try and make a simple system with a bog-standard IDE Master/Slave (HDD/CDROM). Perhaps all the VFS errors were happening because of the SATA drivers. So this is also something to consider.

Cheers,

_** initrd (at least the version back in ~~ 2005) has a bad feature in which if you just give a relative path the command seems to run successfully. There is no information passed to stdout or stderr. However, when running as ls you will find that the image has not been created. It demands the absolute path of the image; hence the use of /boot/init*. I guess I should have ran an echo $? to see what the exit status was. Maybe it brings back some non-zero value which would indicate a lack of success, but nevermind._

---

