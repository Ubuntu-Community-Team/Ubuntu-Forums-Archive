---
title: "ubuntu 16.04 in Dell 16.04 XPS 15 (9550) Gave up waiting for root device"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by hernaniturpin on 2016-06-21
Hi everyone,


I am trying to install ubuntu 16.04 in my new Dell  XPS 15 (9550) laptop. When I boot via ubuntu usb pen everything seems  to fine.
After install ubuntu in the SSD disk i get the following message

[   1.098479] ACPI PCC probe failed-

Gave up waiting on root device. Common problems:

- Boot args (cat /proc/cmdline)

    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)

- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=74d5eb30-b41b-4582-990d-6b13d919eae6 does not exist. Dropping to a shell!

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs) _


I've been unable to install ubuntu in this laptop... it's a little bit frustating
Please fin below the content of some files that can be helpfull to solve my issue.


/proc/cmdline

```
BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic root=74d5eb30-b41b-4582-990d-6b13d919eae6 ro quiet splash
```

/etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p1 during installation
UUID=74d5eb30-b41b-4582-990d-6b13d919eae6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/nvme0n1p6 during installation
UUID=7981b7b7-6a48-43b7-8fb6-7d7ec6b47b24 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p5 during installation
UUID=aeab5c6a-d1e7-484a-89d6-6003c2dd7ba7 none            swap    sw              0       0
```



grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


Thanks in advance

---

### Post by jeremy31 on 2016-06-21
Can you access the install from the Live USB to check ```
cat /etc/initramfs-tools/modules
```

It needs to have module nvme listed and the initramfs rebuilt if it isn't listed

---

### Post by hernaniturpin on 2016-06-21
[COLOR=#000000][FONT=Helvetica]thanks for your reply jeremy31.
the content of [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]/etc/initramfs-tools/modules is the following[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]# List of modules that you want to include in your initramfs.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# They will be loaded at boot time in the order below.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# Syntax:  module_name [args ...][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# You must run update-initramfs(8) to effect this change.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# Examples:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# raid1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]# sd_mod[/FONT][/COLOR]
```

it does not have any nvme module listed. how do i rebuild the modules?

---

### Post by jeremy31 on 2016-06-21
I can find the commands for a normal hard drive but I am not sure if a simple change will work with your SSD.  I will wait to see if someone more informed replies

I added the nvme tag to see if it helps

---

### Post by jeremy31 on 2016-06-22
Moved to installation

---

### Post by banceu_sergiu_ione on 2016-06-26
As I see, it say : 

> ACPI PCC probe failed

Try reinstall with acpi = off and you may need to select also noapic & nolapic, this will deactivate the ACPI at software and local level. See here how to enter in [BootOptions and configure it]("https://help.ubuntu.com/community/BootOptions").

---

