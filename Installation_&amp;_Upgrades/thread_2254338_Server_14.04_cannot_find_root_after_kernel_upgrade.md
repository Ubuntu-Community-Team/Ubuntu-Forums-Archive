---
title: "Server 14.04 cannot find root after kernel upgrade"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by Samloops on 2014-11-26
Greetings All,

I am running Ubuntu Server 14.04 on two identical computers that I am about to deploy into a production environment.  Recently I've run into an issue with the last two upgrades of the Ubuntu kernel which are preventing the servers from booting, requiring a roll-back to the previous version.  I'm stumped as to what the issue may be.  Obviously I can't deploy until I understand what is happening here.

The issue most recently cropped up today with an upgrade to 3.13.0-40-generic #66 from -39.  I have two machines running on ASUS Z87-Plus motherboards with single SATA hard drives, configured using the default Ubuntu partitioning and unencrypted LVM.  I did not specifically update the kernel, but do have automatic security updates turned on.  One of the servers acts as an rsync clone of the master and reboots nightly... hence, I catch the error in the morning when the back-up server has failed to reboot.  As the main server has also downloaded the new version of the kernel, it also fails when doing a manual reboot.  Both machines can be brought up again if I roll back to the previous kernel.

In the boot sequence, the first indication of a problem is:

ata8: SATA link down (SStatus 0 SControl 300)
Begin: Running /scripts/init-premount... done
Begin: Mounting root file system... 
Begin: Running /scripts/local-top ... done
system-udevd[156]: renamed network interface eth0 to em1
Gave up waiting for root device.  Common problems:
  - Boot args (cat /proc/cmdline)
  (snip)
ALERT! /dev/mapper/avh--server--20--vg-root does not exist.  Dropping to a shell!

It then drops to a BusyBox shell with an (initramfs) prompt.

When I interrupt grub and examine the command sequence, I can see no difference between that for the successfully-booting -39 kernel and the failed -40.  Both grub sequences specify the root in the same way - as an identical UUID number.  All of the -40 kernel files exist in /boot and look to be reasonable sizes.

I would normally attribute this non-booting behavior to a bad download and corrupted kernel files, but the same thing ocurred when upgrading from -32 to -39.  I resolved that issue only by eventually reinstalling Ubuntu on both servers and regenerating data files from a backup.  Also, if this were only occurring on the backup server, I would think that I'm rsyncing something over from the master that I should not be, but the fact that it occurs on both the master and the backup make me think that there is something else going on.

I believe that this error only first appeared with -39, and now with -40.  Previous kernel upgrades caused no problems on either machine.  Has a module been removed in these kernels that I need?  

Thanks in advance for any thoughts.

Sam Longiaru
Kamloops, BC Canada

---

### Post by mastablasta on 2014-11-26
what happens if you switch the SATA cable with a new one?

had something similar happen in windows. turns otu it was a bad cable (poor contact).

cause it looks like it can't find the root device.

---

### Post by Samloops on 2014-11-26
Yes, it suggests that it is unable to find the root device, but it can find it when I direct grub to use the older kernel... and the behavior is identical on both machines.  That would tend to suggest either a software problem or an introduced incompatibility between the boot software and the existing hardware.  That's why I was wondering about any required modules. 

For the installation of Ubuntu, I accepted the default to install using LVM.  I don't normally use LVM, but decided to accept it here to help with future expansion.  The fstab for avh-server-20 is as follows:

/dev/mapper/avh--server--20--vg-root   /   ext4   errors=remount-ro   0   1
#/boot was on /dev/sda1 during installation
UUID=2523c...932   /boot   ext2   defaults   0   2
/dev/mapper/avh--server--20-vg-swap_1   none   swap   sw   0   0

and the grub boot command for -40 (fails by not finding boot device) is as fololows:

setparams 'Ubuntu'
     recordfail
     load_video
     gfxmode $linux_gfx_mode
     insmod gzio
     insmod part_msdos
     insmod ext2
     set root='hd0,msdos1'
     if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1  --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 2523c...932
     else
          search --no-floppy --fs-uuid --set=root 2523c...932
     fi
     linux /vmlinuz-3.13.0-40-generic root=/dev/mapper/avh--server--20--vg-root ro splash xvga=1024x768x24 $vt_handoff
     initrd /initrd.img-3.13.0-40-generic
     

The grub boot for -39 (which works) is identical save for the following:

setparams 'Ubuntu, with Linux 3.13.0-39-generic'

and all references as above to -40-generic are set to -39-generic.  Other than that... nothing different.

So this makes me think that it is not grub itself or the way the system is being loaded.  -40 seems to be missing the ability to properly map the root device.

Does that provide any aditional clues to anyone?  


Thanks,

Sam

---

### Post by MAFoElffen on 2014-11-30
I didn't see this as solved, so... still need help? 

Is it 64 bit server? Is it on MBR disks or GPT?

If you can boot that server from a Secure Boot remix LiveCD disk? Please post the results of:
```
sudo blkid
sudo fdisk -l
sudo pvdisplay

```
From those results, I can tell you how to mount an LVM filesystem and chroot into it, to diagnose, or to make repairs.

EDIT-- Warning: If you run boot repair from that disk... use it just to post a report to postbin, not to fix it. It sometimes thinks that an LVM filesystem is erroneously using mdadm (linux RAID) when it was not.

---

