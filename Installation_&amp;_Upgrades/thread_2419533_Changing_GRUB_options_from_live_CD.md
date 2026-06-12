---
title: "Changing GRUB options from live CD"
date: 2019-05-23
forum: Installation &amp; Upgrades
---

### Post by spearhead2 on 2019-05-23
After a fresh install of Ubuntu-Mate on a newly purchased laptop, I cannot login - everything freeze. There are some things I'd like to test in order to make it start - re-installation of graphic card drivers and using some boot options (mostly nomodeset and modprobe.blacklist). The problem is that no GRUB menu is showing up, so I am unable to either boot using a recovery mode to access the console or edit boot options with e button. Tried Space, Shift and Escape keys, and most of F1-12, but I was only able to enter BIOS. It goes as follow: I start the laptop it automatically picks default, normal boot option, goes into login screen and then freeze. I can't go to virtual terminal either. So my goal is to change GRUB options from the Live-CD, which I can boot normally. 

Here's the disk in question:
```
$ sudo fdisk -l /dev/sda
Disk /dev/sda: 223.6 GiB, 240065183744 bytes, 468877312 sectors
Disk model: WDC WDS240G2G0B-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0C64BE04-FD58-4617-9EC1-D6EFE2F0A8B1

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 468875263 467824640 223.1G Linux filesystem
```
Using Live-CD I can mount it just fine
```
ubuntu-mate@ubuntu-mate:~$ sudo mount /dev/sda1 /mnt
ubuntu-mate@ubuntu-mate:~$ sudo mount /dev/sda2 /opt
ubuntu-mate@ubuntu-mate:~$ ls /mnt/
EFI  boot
ubuntu-mate@ubuntu-mate:~$ ls /opt/
bin  boot  cdrom  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swapfile  sys  tmp  usr  var  vmlinuz
```
Then I update /etc/default/grub as follows (adding GRUB_TIMEOUT, GRUB_HIDDEN_TIMEOUT and more boot options):
```

$ cat /opt/etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force nomodeset modprobe.blacklist=nouveau"
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
Finally I try to update GRUB with following
```

$ sudo grub-install --root-directory=/opt /dev/sda --force
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.

```
I've added --force flag to avoid error:
```

grub-install: error: will not proceed with blocklists.

```
It doesn't help - GRUB menu doesn't show, and I still cannot login. So my question is - what else I need to do to force GRUB menu to show from a LiveCD?

---

### Post by oldfred on 2019-05-23
Grub does not like blocklists. Or hardcoded addresses.
Generally gpt partitioning is now used with UEFI boot.
If using BIOS boot on gpt drive, you must have a 1 or 2MB unformatted partition with the bios_grub flag.
But best not to mix BIOS & UEFI as they may load drivers differently.

If UEFI boot you use escape key from UEFI screen before grub menu. But if UEFI fast boot is on, you may not have time to press any key as fast boot immediatley jumps to booting system. It does not take the very few seconds to rewrite hardware info to drive for operating system to use, it assumes not changes so boot is quick. You can try a full cold boot from power totally off, instead of warm boot. Systems usually do not use fast boot from power on.
Note that UEFI fast boot is different than Windows fast start up, but both are intended to make Windows seem like it does not take as long to boot.

---

### Post by spearhead2 on 2019-05-23
Managed to boot my system after following [https://askubuntu.com/a/831241](https://askubuntu.com/a/831241)

---

