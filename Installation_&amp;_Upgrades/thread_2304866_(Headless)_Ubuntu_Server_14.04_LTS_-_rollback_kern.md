---
title: "(Headless) Ubuntu Server 14.04 LTS - rollback kernel?"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by PartisanEntity on 2015-11-30
After running ```
sudo apt-get dist-upgrade
``` today, it installed ```
linux-image 3.13.0-68
```.

This seems to have broken something because the server will not boot.

However if I select a previous version such as ```
3.13.0-67
``` then the server boots fine.

How can I make it start with ```
3.13.0-67
``` by default?

And would I still have the option to upgrade the next time there is a kernel update?

Based on what I read one can edit ```
/etc/default/grub
``` apparently, but I am not wrapping my head around it.

Here are the contents of that file in case it helps:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset"
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
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by deadflowr on 2015-11-30
What's odd to me is that I got an update for 3.13.0-70 today..?
Perhaps re-run an update to see if you get that too.

---

