---
title: "No Boot messages shown"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by dharma_initiative on 2011-08-28
Hi everybody,

my Ubuntu Server sometimes doesn`t boot. So i wantet to look if there is something in the boot messages.

Normally they should appear when booting the system up.
For each task there is a line with the descritption and at the end of the line there is "[OK]" or "[FAIL]"

But my system doesn`t show this info. It shows a blank screen and then only shows me the login prompt.

Is there any way to disable this behaviour=

Thank you

---

### Post by dino99 on 2011-08-28
to have a friendly & no worrying bootup, ubuntu have installed plymouth (5 dots you see while booting, but sometimes you get a black screen during a few seconds before to see it) to hide all these comments. If you need/want to see them, while you select your boot line inside grub menu, edit it (E) then remove "splash" and finally validate wiyh ctrl+x to boot.

To make it permanent:
sudo gedit /etc/default/grub

sudo update-grub

note: replace gedit by nano if you dont have a graphic interface

---

### Post by dharma_initiative on 2011-08-28
Hi,

thank you for your quick reply.

In my **/etc/default/grub** there is nothing with "splash"
If i boot and edit the boot line there is nothing with splash too.

Heres the **/etc/default/grub**:

```
    IW   /etc/default/grub            Row 35   Col 1    7:33  Ctrl-K H for help
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
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

---

