---
title: "No serial console after 16.04 server fresh install"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by rob-marshall17 on 2016-05-28
Hi,

I ran into the same problem with 15.10 so I have been using 14.04 but I figure this is probably just something stupid...

I did a fresh install, via the serial console, of Ubuntu 16.04 Server on a Dell R710. After the normal installation there doesn't appear to be any ssh access and even though my /etc/default/grub file has:

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.


~ # mount /dev/sda1 /mnt
~ # cat /mnt/etc/default/grub
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
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --unit=0 --speed=9600 --stop=1"

and I created the file:

~ # cat /mnt/etc/init/ttyS0.conf
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.


start on stopped rc RUNLEVEL=[12345]
stop on runlevel [!12345]


respawn
exec /sbin/getty -L 9600 ttyS0 vt102

When I boot the system after the installation I see no output on the console during the boot and I don't get a login prompt. Which is particularly frustrating because apparently the default installation doesn't install SSH and/or it's blocked. So even though I can ping the node and see that it's up, I can't login.

Any suggestions? I tried to follow the "Serial Console HowTo" but I get the feeling it's outdated.

Thanks,

Rob

---

