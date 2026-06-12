---
title: "grub stopped having a time out after todays update"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-08-27
After today mornings upgrade grub no longer times out. Is this intentional?
This is my /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

GRUB_CMDLINE_LINUX=""

---

### Post by jppr on 2009-08-27
[https://launchpad.net/ubuntu/karmic/+source/grub2/1.96+20090826-3ubuntu1](https://launchpad.net/ubuntu/karmic/+source/grub2/1.96+20090826-3ubuntu1)

---

