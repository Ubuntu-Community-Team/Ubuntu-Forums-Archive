---
title: "Boot in Ubuntu"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by frozonecom on 2011-05-26
Hi. I just want to ask if there is a way to make grub bootloader automatically boot to ubuntu every start up. And only make the bootloader appear when I press a certain key(ie. F7) so that I can boot to windows when I do not want to boot on Ubuntu.

I hope someone can help me with this. :)

---

### Post by lmarmisa on 2011-05-26
This is a good guide for GRUB2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

According to the default GRUB config (file /etc/default/grub) you should be able to boot into Ubuntu automatically. Try to reduce the parameter GRUB_TIMEOUT to 2 or 3 seconds if you wish a faster boot. Open a terminal and type this command:

```

sudo gedit /etc/default/grub

```

Change GRUB_TIMEOUT to 3 or any other value which you wish:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
[COLOR="Blue"]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR="blue"]GRUB_TIMEOUT=3[/COLOR]
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

Save & exit.

Then type this command:

```

sudo update-grub

```

And finally reboot your system.

If you do not press any key at startup, the system will boot into Ubuntu. Use the arrows keys for selecting Windows at startup.

---

### Post by frozonecom on 2011-05-30
Thanks for the help! :) That actually did the trick!

---

