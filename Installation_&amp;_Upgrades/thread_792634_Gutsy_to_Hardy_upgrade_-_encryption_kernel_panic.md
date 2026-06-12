---
title: "Gutsy to Hardy upgrade - encryption kernel panic"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by squegie on 2008-05-13
Ok, I had Ubuntu Gutsy (7.10) with full disk encryption (the alternate install cd/dm-crypt).  Today I did the update manager method to upgrade to Hardy Heron (8.04).  Before, I had done a kernel update with my encrypted filesystem and had no issues, so I thought another kernel update would still work.

kernel 2.6.24-16-generic will kernel panic
kernel 2.6.24-16-generic will kernel panic

VFS: Cannot open root device "mapper/workaround-root" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

kernel 2.6.24-14-generic will go to busy box
kernel 2.6.24-14-generic (recovery) will go to busy box

I've tried to edit the root line in grub, but I'm just guessing.  Another thread said about root is not called cryptroot, but I don't know how that applies to grub lines.

grub entry:
root (hd0,0)
kernel /vmlinuz-2.6.24-16-generic  root=/dev/mapper/workaround-root ro quiet splash
quiet

I did see some threads about booting a live cd and running cryptmount to access the data, and this may come to that, but this laptop system has my working cd burner, so I'd like to try what I can with grub.  My old kernels may still be on there.

So:
The last kernel available to Gutsy, what version was that (can I enter it into grub to boot from that kernel)?

Can someone give me some grub foo to get my system booting?

Even if I get a live cd burnt and mount that partition, what would I do to get grub/kernel image fixed so it will boot?

Time is currently 4:20AM ET.  By 6:30ET I will be done with work and sleeping.  So I encourage much posting for me to pick up at 6PM when I get back to work.  :-)

---

### Post by squegie on 2008-05-13
So I figured out that there is an initrd backup of 2.6.22-14-generic that I was able to get grub to boot from, so I can get into my system now.

I'm trying to figure out how to add the dmcrypt modules to the 2.6.24-16-generic initrd using the initrd tools.  

Most references seem to talk about adding an entry to /etc/mkinitramfs/modules, but that directory does not exist.  I'm going to try creating the directory and that file, but I fear that more is needed.

If anyone can point me at a good tutorial (or the quick answer) I'd appreciate it.  I'll post back.

---

