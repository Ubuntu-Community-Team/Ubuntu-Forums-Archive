---
title: "No boot splash image after upgrading from 9.10 to 10.04"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2010-08-02
When I boot 10.04 I get no splash image. I just get "disabling IRQ #18" followed by a blinking cursor and then a few more lines of text just before 10.04 runs.
Here's my /etc/default/grub:

[ code]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=795"

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
[ /code]

Is there anything else I need to check or change such as the contents of /lib/plymouth ?

Please can the team advise?

---

