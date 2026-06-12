---
title: "Grub problems after 11.04 Upgrade"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Dr_Jez on 2011-07-05
First post, sorry for any mistakes.

I have a dual boot Win7/Ubuntu laptop. I have been running it dual since 10.04, Lucid with no problems, and I upgraded to 10.10 also without problems. However, when I upgraded to 11.04 I began to get error messages on boot up. 

Importantly - both Win7 and Ubuntu still work fine, so it could be worse, but clearly something is not right in GRUB. 

I could solve this by wiping Ubuntu and reinstalling from the Live CD, but that teaches me nothing, so I would like to get to the bottom of the problem. 

The following is what I get if I try to update grub:

jez@jez-laptop:~$ sudo update-grub

[sudo] password for jez: 

Generating grub.cfg ...

Found linux image: /boot/vmlinuz-2.6.38-8-generic

Found initrd image: /boot/initrd.img-2.6.38-8-generic

Found linux image: /boot/vmlinuz-2.6.32-25-generic

Found initrd image: /boot/initrd.img-2.6.32-25-generic

Found memtest86+ image: /boot/memtest86+.bin

Found Windows Recovery Environment (loader) on /dev/sda1

Found Windows 7 (loader) on /dev/sda2

error: syntax error.

error: Incorrect command.

error: syntax error.

error: line no: 153

Syntax errors are detected in generated GRUB config file.

Ensure that there are no errors in /etc/default/grub

and /etc/grub.d/* files or please file a bug report with

/boot/grub/grub.cfg.new file attached.

done

All help gratefully received.

---

### Post by Dr_Jez on 2011-07-05
Grub config file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=771"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

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

---

