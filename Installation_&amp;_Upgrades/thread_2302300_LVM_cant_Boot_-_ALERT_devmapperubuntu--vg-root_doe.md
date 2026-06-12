---
title: "LVM cant Boot - ALERT /dev/mapper/ubuntu--vg-root does not exist DROPPING to Shell"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by Saugat_Singh on 2015-11-09
My system boots to GRUB and then when I choose a kernel , it drops me to the BusyBox shell with 
 /dev/mapper/ubuntu--vg-root  does not exist   

I have a posted the picture of my current system. 
[ATTACH=CONFIG]265452[/ATTACH]

and grub file
[COLOR=#373E4D][FONT=helvetica]GRUB_DEFAULT=0#GRUB_HIDDEN_TIMEOUT=0GRUB_HIDDEN_TIMEOUT_QUIET=trueGRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"GRUB_CMDLINE_LINUX=""# Uncomment to enable BadRAM filtering, modify to suit your needs# This works with Linux (no patch required) and with any kernel that obtains# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"# Uncomment to disable graphical terminal (grub-pc only)#GRUB_TERMINAL=console# The resolution used on graphical terminal# note that you can use only modes which your graphic card supports via VBE# you can see them in real GRUB with the command `vbeinfo'#GRUB_GFXMODE=640x480# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux#GRUB_DISABLE_LINUX_UUID=true# Uncomment to disable generation of recovery mode menu entries#GRUB_DISABLE_RECOVERY="true"# Uncomment to get a beep at grub start#GRUB_INIT_TUNE="480 440 1"[/FONT][/COLOR]

---

