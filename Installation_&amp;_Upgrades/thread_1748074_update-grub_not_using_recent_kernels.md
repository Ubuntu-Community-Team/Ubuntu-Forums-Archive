---
title: "update-grub not using recent kernels?"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2011-05-03
I have this strange problem on ubuntu 10.04 64 bit, that when running update-grub, it will only put the oldest kernel into the grub menu, despite the fact that I have recent kernels around as well.

in particular:

```

# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-31-server
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-server
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.32-29-server
Found kernel: /boot/vmlinuz-2.6.32-29-generic
Found kernel: /boot/vmlinuz-2.6.32-28-server
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found kernel: /boot/vmlinuz-2.6.32-27-server
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-server
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-server
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-server
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

but in /boot/grub/grub.conf :

```

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9294882-2d73-4d1d-9646-209c83a757d6
    linux   /boot/vmlinuz-2.6.32-24-generic root=UUID=e9294882-2d73-4d1d-9646-209c83a757d6 ro   quiet splash
    initrd  /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9294882-2d73-4d1d-9646-209c83a757d6
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux   /boot/vmlinuz-2.6.32-24-generic root=UUID=e9294882-2d73-4d1d-9646-209c83a757d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd  /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

```

my /etc/default/grub looks like this:

```

# cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

what is going wrong here?

I'd like to see the most recent kernels in the grub menu, with the most recent being on top.

---

### Post by akos.maroy on 2011-05-03
looking at the output, it seems that update-grub generates /boot/grub/menu.lst instead of /boot/grub/grub.cfg

what would it do that?

---

### Post by dino99 on 2011-05-03
grub2 is used now and conflict with the old grub-legacy file (menu.lst)

wonder why you dont have removed those oldish kernels ? Only let the 2 more recent ones installed, its safe enough

from synaptic:
- remove/purge ALL the related grub installed packages
( then with nautilus: search menu.lst then remove it)
- remove the oldish kernels
- then install grub-pc & grub-common

reboot

---

### Post by oldfred on 2011-05-03
Did you use SUM - Startup Manager? We have seen several users use SUM and have this issue. It seems like it creates a menu.lst and then grub update starts updating menu.lst not grub.cfg.

Try this which is the command update-grub is supposed to run.

sudo grub-mkconfig -o /mnt/boot/grub.cfg

---

