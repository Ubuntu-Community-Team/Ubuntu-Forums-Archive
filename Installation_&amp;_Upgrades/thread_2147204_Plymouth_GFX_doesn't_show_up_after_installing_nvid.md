---
title: "Plymouth GFX doesn't show up after installing nvidia-current."
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by huckpie on 2013-05-21
Title says all. For some reason, even if I edit the Grub config file by uncommenting the resolution settings, the Ubuntu logo wouldn't show up after I install the non-free Nvidia drivers. It would typically appear when you use the default nouveau driver, but the latter drivers won't cut it either as the GUI's too sluggish.

Here's my grub settings:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=off"

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

Oh, and I'm running on a clean 13.04 install on a DG31PR board, using kernel version 3.8.0-21.

---

### Post by huckpie on 2013-05-27
Sorry for the bump, but anyone?

---

