---
title: "Gave up waiting for root device. Ubuntu 16.04"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by peterb518 on 2017-02-12
I've been trying to install Ubuntu 16.04 from a USB drive for the last few days and running into the following issue on boot:


```
    Gave up waiting for root device. Common problems:
      — Boot args (cat /proc/cmdline)
        — Check rootdelay= (did the system wait long enough?)
        — Check root= (did the system wait for the right device?)
      — Missing modules (cat /proc/modules; ls /dev)
    ALERT! UUID=<drive-uuid> does not exist.   
    Dropping to a shell! 
    
    BusyBox v.1.20.2 (Ubuntu 1:1.20.2-1ubuntu1) built-in shell (ash)   
    Enter 'help' for list of built-in commands.  
    
    (initramfs)
```


One thing to note from above: I can't use the shell (no response) after `(initramfs)` above in comparison to some solutions I've seen

For some context, I'm installing it on hard drive on a computer that has two other hard drives: one with a Windows 7 install and the other that's just NTFS storage. The Ubuntu installation is on `/dev/sdc1` and the boot loader the same. 

Here are the things that I've tried to fix this, using a Live Ubuntu and chroot:

1. Validated that the UUID that appears after `blkid` is the same as that in `/etc/fstab`
2. Replaced the <file system> path in `/etc/fstab` with `/dev/sdc1`. I get the same error of "Gave up waiting for root device" except the UUID is replaced with `/dev/sdc1`
3. After doing 2, uncommenting `GRUB_DISABLE_LINUX_UUID=true` in `/etc/default/grub`. Running update-grub afterwards.
4. Adding `rootdelay=40` and, separately, `rootwait` to GRUB_CMDLINE_LINUX in `/etc/default/grub`. Running update-grub afterwards.

I just don't understand how it's asying the device does not exist, since I have to go through the boot loader (on the same drive) to even start Ubuntu.

If it's an additional hint, when I try to run the Ubuntu recovery mode, it ends up looping on the line `Begin: Running /scripts/local=block ... done.` before giving me the original "Gave up" error.

---

### Post by oldfred on 2017-02-12
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you want to run Boot-Repair fixes, only use advanced mode and total uninstall of grub and reinstall of grub to sdc drive only. Boot-Repair's default fix is to install grub to all MBR, and usually you want different boot loaders in different drives.
Also check update kernel so it should update initramfs.

---

