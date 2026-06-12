---
title: "Unable to complete update to 3.19.0-16"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by nlee2 on 2015-05-14
My new install of ubuntu 15.04 desktop cannot completely update to 3.19.0-16 because update-grub hangs. It finishes generating grub.cfg.new and sits there forever. I manually rename grub.cfg. Clean up the dpkg updates and lock to reboot. Everything seems ok but the next time I run apt-get upgrade, it tries to run update-grub again. How do I fix/avoid this?

---

### Post by TheFu on 2015-05-15
Could be out of storage on /boot? In a terminal, please run 
[B]df -i
df -h[/B]
to check and post the results back here with "code tags" so things line up.  Then we can decide the next step if that really is the issue.

---

### Post by nlee2 on 2015-05-15
Thank you for your help. More background. Ubuntu 15.04 desktop is installed as a gen2 vm in Hyper-v so it is a efi boot.After the initial install I noticed that update-grub would hang after generating grub.cfg.new. At that time, I renamed it to grub.cfg and continued. Since I ran apt-get dist-upgrade, I am unable to ignore the update-grub problem.

```

Filesystem      Inodes  IUsed  IFree IUse% Mounted on
udev            251989    419 251570    1% /dev
tmpfs           254772    556 254216    1% /run
/dev/sda2      1149120 227519 921601   20% /
tmpfs           254772      5 254767    1% /dev/shm
tmpfs           254772      3 254769    1% /run/lock
tmpfs           254772     17 254755    1% /sys/fs/cgroup
/dev/sda1            0      0      0     - /boot/efi
cgmfs           254772     13 254759    1% /run/cgmanager/fs
tmpfs           254772     29 254743    1% /run/user/1000

Filesystem      Size  Used Avail Use% Mounted on
udev            985M     0  985M   0% /dev
tmpfs           200M  5.0M  195M   3% /run
/dev/sda2        18G  5.1G   12G  32% /
tmpfs           996M   80K  996M   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           996M     0  996M   0% /sys/fs/cgroup
/dev/sda1       511M  3.4M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           200M   48K  199M   1% /run/user/1000

Setting up linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.19.0-16-generic
) points to /boot/initrd.img-3.19.0-16-generic
 (/boot/initrd.img-3.19.0-16-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-16-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.19.0-16-generic
) points to /boot/vmlinuz-3.19.0-16-generic
 (/boot/vmlinuz-3.19.0-16-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-16-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic


```

---

### Post by dino99 on 2015-05-15
from a terminal, try > sudo apt-get purge grub* then > sudo apt-get update  && sudo apt-get install -f  and finally > sudo apt-get install grub-pc

---

### Post by nlee2 on 2015-05-15
What do I choose here?

```

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                 
                 &#9474; GRUB install devices:                      &#9474;                 
                 &#9474;                                            &#9474;                 
                 &#9474;    [ ] /dev/sda (21474 MB; Virtual_Disk)   &#9474;                 
                 &#9474;    [ ] - /dev/sda2 (18791 MB; /)           &#9474;                 
                 &#9474;                                            &#9474;                 
                 &#9474;                                            &#9474;                 
                 &#9474;                   <Ok>                     &#9474;                 
                 &#9474;      

```

I went ahead with /dev/sda and ended up where I started

```

Creating config file /etc/default/grub with new version
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic

```

---

### Post by TheFu on 2015-05-15
Never used efi boot inside a VM.
Doesn't that require a separate partition to hold the boot code? Not sure.  Also, doesn't that partition need to be formated FAT32 or something like that?

It would be easier to just use BIOS booting, unless you have some highly specific reason for wanting efi involved. Post
[B]
sudo parted -l[/B] output.

Thanks for the code tags.Very helpful.

---

### Post by nlee2 on 2015-05-15
I went with default install of Ubuntu 15.04 desktop in a gen2 vm in Hyper-v. The only option I see is to disable secure boot which I did. Went with gen2 vm to be able to boot from scsi vhd rather than ide.

```

Model: Msft Virtual Disk (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   19.3GB  18.8GB  ext4
 3      19.3GB  21.5GB  2144MB  linux-swap(v1)

```

---

### Post by TheFu on 2015-05-15
Don't know anything about hyper-v or "gen2 vm" - sorry.  Can you rebuilt with BIOS (not efi?)? 

That is probably the shortest answer for a solution.  

If you care to solve THIS problem, don't think I can help.

---

