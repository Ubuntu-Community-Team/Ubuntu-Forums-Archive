---
title: "Grub problems with boot sequence for encrypted drive"
date: 2022-01-05
forum: Installation &amp; Upgrades
---

### Post by billyjoepiano on 2022-01-05
I was able to get something nearly identical working on a CentOS system recently.  But I'm quite a bit more experienced with Ubuntu, so not sure why I've experienced so much difficulty with this.

Here's the situation:

There is only 1 drive (/dev/sda) with 2 partitions.
[LIST]
[*]First partition (/dev/sda1) is relatively small (512MB) unencrypted ext4 volume.  This is the boot partition (more on this in a minute...)
[*]Second partition (/dev/sda2) is encrypted with LUKS1.  Once un-encrypted, it has two logical volumes -- the root filesystem (ext4) and a swap partition.
[/LIST]

I need to be able to unlock the encrypted volume remotely via ssh, which is why I need the UN-encrypted volume to initiate an ssh server daemon during the initramfs phase of boot.  I'm using dropbear (dropbear-initramfs) to accomplish this, and so far it's worked great.... AFTER I get past the grub stage that is..

The problem seems to be that no matter what I do with the grub configuration, I keep getting dropped into a grub> shell at boot (NOT a rescue shell) where the prefix and root variables are set incorrectly -- prefix=(hd0)/boot/grub and root=(hd0).  All I have to do is manually 'set prefix=(hd0,msdos1)/boot/grub' and then 'normal' , and voila... it brings up the normal grub menu and automatically commences boot after a brief countdown.  From there on out, everything works exactly as expected.

Strangely -- I've done this manual grub boot sequence so much now, that I've discovered (for whatever inexplicable reason) I don't even need to enter 'set root=(hd0,msdos1)/' , 'insmod normal' , or 'insmod linux'.  Like, I say... Just set prefix then 'normal'.  I can't entirely explain why that is, but it definitely makes it easier when you have to manually enter this boot sequence a dozen times each hour, whilst trying to debug the problem.

I have spent the last two days scouring the internet about how to fix this, and have tried just about every possible configuration (and then some!) that can be found.  Including, but not limited to:
[LIST]
[*]Running 'chroot /boot' prior to grub-install, grub-mkconfig, and update-initramfs.  (Note that the boot partition is mounted to /boot once the main system is running).  And this of course also requires 'mount --bind' 'ing some of the system directories like /dev , /sys , /etc , /usr , ETC within the /boot directory prior to chroot-ing
[*]Various configurations of the /etc/default/grub file.  If its something that comes up in the first two pages of a google search, I've probably tried it.  And probably tried it in various combinations with other configurations.  I always run grub-mkconfig and update-initramfs after any changes to /etc/default/grub... and often grub-install as well just for good measure (though from what I can tell that one isn't really necessary each time)
[*]Variations of 'grub-install', including with --force /dev/sda1 , with --boot-directory= , and some other optional flags/settings
[*]Variations on the file structure of the boot partitions.  I have tried it with its own /boot directory (putting grub.cfg at /boot/boot/grub/grub.cfg once mounted to the running FS), as well as with everything in the root of the partition and a 'boot' symlink pointing back to './'
[*]I've tried changing the configs in some of the files in /boot/grub/ , based on some suggestions I've seen from searches ... but this usually just breaks things even worse.
[/LIST]


There has to be some kind of simple solution to this!  All I need is for grub to look in (s0,msdos1)/ instead of (s0) for the prefix and root variables !!!!!  What am I doing wrong here!!!????!?!?

----------

p.s.
I don't *think* this is related, but maybe I should mention this machine is a VM running on Linode (it's a 'Nanode' , tiny VM).  The CentOS system I recently configured with a nearly identical arrangement was also a VM, but running on an ESXi host.  Like I say, probably not related to the problem, but might be worth mentioning???

---

### Post by billyjoepiano on 2022-01-05
pps

I also should mention that this is a strictly CLI ubuntu-server (no desktop or GUI) so it seems I am unable to run the boot-repair utility I've seen suggested multiple times.

---

