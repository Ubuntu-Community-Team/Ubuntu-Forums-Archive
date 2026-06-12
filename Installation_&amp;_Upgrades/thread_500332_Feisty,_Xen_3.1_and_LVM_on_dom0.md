---
title: "Feisty, Xen 3.1 and LVM on dom0"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by gracedman on 2007-07-13
HELP!! I've been beating my head against the wall on this problem for almost a week including incessant googling!

I am trying to install Xen 3.1 on Feisty using LVM.  I have a small ext3 /boot partition.  The rest is allocated to one volume group VG0 which is itself partitioned into six or more Logical volumes for various domain file systems including the / system for dom0.

Feisty itself is running fine on LVM.  I downloaded Xen from source since we will eventually be customizing the kernels. I thought it would be a simple:

make world KERNELS="linux-2.6-xen0 linux-2.6-xenU"

followed by:

sudo make install KERNELS="linux-2.6-xen0 linux-2.6-xenU"

and editing /boot/grub/menu.lst to read:

title           Xen 3.1 / XenLinux 2.6
root            (hd0,0)
kernel          /xen-3.1.gz dom0_mem=131072
module          /vmlinuz-2.6-xen0 root=/dev/mapper/VG0-dom0root ro console=tty0

Xen could not boot because it could not find the root partition.  I also tried root=/dev/VG0/dom0root.  I thought that it might need an initrd image so I tried using mkinitrd and it failed with messages about the kernel not supporting LVM.

After googling for hours, I came across a post that said to use mkinitramfs so I did:

sudo mkinitramfs -o /boot/initrd.img-2.6.18-xen0 2.6.18-xen0

Xen now boots (I edited menu.lst to load the initrd module) but the dom0 fails with the same style error.  It tries to find the root file system, complains that /dev/mapper/VG0-dom0root doesn't exist and drops to the initrd shell.

I'm actually in the process of downloading Fedora Core 7 because I can't lose much more time on this but I'd really rather standardize on Ubuntu.  Any clues on what I need to do to get this to work? Thanks - John

---

### Post by gracedman on 2007-07-14
I've tried recompiling the dom0 kernel to load LVM support as modules instead of built into the kernel.  That did not help.  I'm still stuck on this.  Any ideas of how to get this to work or how to troubleshoot it further? Thanks - John

---

