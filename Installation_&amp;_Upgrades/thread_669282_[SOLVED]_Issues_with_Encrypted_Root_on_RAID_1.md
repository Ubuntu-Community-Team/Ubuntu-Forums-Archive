---
title: "[SOLVED] Issues with Encrypted Root on RAID 1"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by gdi2k on 2008-01-16
I'm attempting install Ubuntu on an encypted root filesystem, on top of a RAID 1. 

I used the Alternate Installer to setup the partitions, RAID and encryption. I created 2 RAID 1 arrays as follows: 
[LIST=1]
[*]Boot partition (unencrypted of course)
[*]Root Partition (encrypted)
[/LIST]

It all insalled fine. However, at the end of the installation, the installer reported that it was unable to install the LILO bootloader, I would have to install a bootloader myself. 

(Side note: I thought Ubuntu only used grub? grub was not featured at all in the installer menus, only LILO). 

So I rebooted using the Live CD and installed grub myself, which worked fine. Grub's menu.lst looks like this: 

```
# For booting GNU/Linux
title           Ubuntu!
root            (hd0,1)     
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/md1_crypt ro
initrd          /initrd.img-2.6.22-14-generic
```

During the boot process, I see that the raid arrays are started, but the system halts at **"Waiting for root filesystem..."**. Eventually it times out and drops me into the busybox shell with the following message: 
```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/md1_crypt does not exist. Dropping to a shell.
```

Sure enough, only "control" is listed under /dev/mapper/ 

However, by entering the following in busybox's shell, I am able to continue to boot: 
```
cryptsetup luksOpen /dev/md1 md1_crypt
CTRL+d
```

What am I missing? 

Something that occurred to me is: How would grub know to associate /dev/mapper/md1_crypt with /dev/md1 ? Do I set that somewhere? I've looked through the initramfs stuff and compared it to a laptop with encrypted root, and all looks to be in good order. 

Any help appreciated!

---

### Post by gdi2k on 2008-01-16
After some more googling, I now realise that I need to populate my /etc/crypttab, then do a update-initramfs -u to update initramfs. 

My thinking was that crypttab was probably just for non-root encrypted file systems, as it couldn't be read during boot anyway (as root is encrypted). Now it all makes sense. 

:)

---

