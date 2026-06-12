---
title: "Update Question"
date: 2024-09-24
forum: Installation &amp; Upgrades
---

### Post by ffuentesb on 2024-09-24
Hello, New Here but not to Ubuntu :)
It seems that 22.04 is plagued with upgrade issues if you happen to have an nvidia gpu...

I just got an OEM system that came with Ubuntu 22.04 (HP Z2 Mini G9 with RTXA2000) off the box works beautifully to an extend lol, there seem to be a bit of lag on the GUI that is a bit annoying so naturally I proceed to do the updates...When the system reboots my nvidia rendering crashes and the system defaults to using llvmpipe.
It seems that this is an occurrence under 22.04? 
Is there a fix. I see people posting to use noveou only?

The system came preinstalled with:
 bookworm/sid
NVRM version: NVIDIA UNIX x86_64 Kernel Module  535.154.05  Thu Dec 28 15:37:48 UTC 2023
GCC version:  gcc version 12.3.0 (Ubuntu 12.3.0-1ubuntu1~22.04) 


I am running:


Operating System: Ubuntu 22.04
KDE Plasma Version: 5.24.7
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel Version: 6.5.0-1013-oem (64-bit)
Graphics Platform: X11
Processors: 32 × 13th Gen Intel® Core™ i9-13900K
Memory: 62.5 GiB of RAM
Graphics Processor: NVIDIA RTX A2000 12GB/PCIe/SSE2

Yes I installed KDE :P

---

### Post by ffuentesb on 2024-09-25
BumP :)

---

### Post by oldfred on 2024-09-25
your system may be new enough that it needs 24.04.1 to have latest kernel & drivers.
Also is UEFI Secure Boot on? You then have to create a MOK - machine owner key to authorize the proprietary nVidia driver for Secure Boot.

---

### Post by ffuentesb on 2024-09-25
Thanks for this info.
I disable secure boot.

I found that after the update grub never changes me to the new kernel and grub is defaulted to 0 which boots to the OEM kernel and during the update it upgrades me to 6.8 from 6.5...
After I found this I was able to default to the new generic kernel and I was able to boot with no nvidia issues.

Linux 0scur0 6.8.0-45-generic #45~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Sep 11 15:25:05 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


Just curious, is this normal that grub is not setting me to boot to the new kernel when upgrading?

Thanks!

---

### Post by oldfred on 2024-09-26
I have not done an upgrade since 10.04? or there abouts.
I have at least 2 / (root) partitions and keep two LTS versions, older one & newer one when it comes out. And data in separate data partition(s).

Grub should update to latest kernel. 
We may need to review settings in /etc/default/grub.
But Ubuntu's grub scripts normally also provide a link to newest kernel as vmlinuz & initrd.img to make it easier to manually boot if issues.
You can post these in code tags.

ll /boot  # that is el el, not i.
cat /etc/default/grub

---

### Post by ffuentesb on 2024-09-26
```
root@0scur0:/boot# lltotal 196924
drwxr-xr-x  5 root root     4096 Sep 25 17:02 ./
drwxr-xr-x 20 root root     4096 Sep 22 18:18 ../
-rw-r--r--  1 root root   278900 Jan 16  2024 config-6.5.0-1013-oem
-rw-r--r--  1 root root   287058 Sep 11 08:33 config-6.8.0-45-generic
drwxr-xr-x  4 root root     4096 Dec 31  1969 efi/
drwxr-xr-x  5 root root     4096 Sep 25 21:41 grub/
drwxr-xr-x  4 root root     4096 Sep 22 18:13 HP/
lrwxrwxrwx  1 root root       27 Sep 25 17:00 initrd.img -> initrd.img-6.8.0-45-generic
-rw-r--r--  1 root root 76708002 Sep 25 17:02 initrd.img-6.5.0-1013-oem
-rw-r--r--  1 root root 77731439 Sep 25 17:02 initrd.img-6.8.0-45-generic
lrwxrwxrwx  1 root root       25 Sep 22 18:13 initrd.img.old -> initrd.img-6.5.0-1013-oem
-rw-r--r--  1 root root   182800 Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root   184476 Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root   184980 Feb  6  2022 memtest86+_multiboot.bin
-rw-------  1 root root  8252552 Jan 16  2024 System.map-6.5.0-1013-oem
-rw-------  1 root root  8657806 Sep 11 08:33 System.map-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 Sep 25 17:00 vmlinuz -> vmlinuz-6.8.0-45-generic
-rw-r--r--  1 root root 14222216 Jan 29  2024 vmlinuz-6.5.0-1013-oem
-rw-------  1 root root 14911880 Sep 11 08:59 vmlinuz-6.8.0-45-generic
lrwxrwxrwx  1 root root       22 Sep 25 17:00 vmlinuz.old -> vmlinuz-6.5.0-1013-oem
root@0scur0:/boot# 

```


I made the following changes:

GRUB_DEFAULT=saved (**Used to be 0 here**)
GRUB_SAVEDEFAULT=true
#GRUB_TIMEOUT_STYLE=hidden



```
root@0scur0:/boot# cat /etc/default/grub# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=3
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
GRUB_DISABLE_OS_PROBER=true
GRUB_RECORDFAIL_TIMEOUT=5
root@0scur0:/boot#
```

---

### Post by oldfred on 2024-09-26
Since HP, has it modified grub scripts to not update from OEM kernel(s)?
HP often with dual boot, defaults UEFI to boot Windows even after efibootmgr changes boot order to Ubuntu. You have to change boot order in UEFI settings.

---

### Post by ffuentesb on 2024-09-26
Not a dual boot machine (bought with Ubuntu pre loaded  from their factory as I am tired of building custom...I am old LOL) BUT I wouldn't get it pass them that they have done something crazy. I am going to investigate further. Thanks!

---

### Post by oldfred on 2024-09-26
The few other OEM type installs I have seen have a custom grub as they keep a copy of ISO in a partition and add a grub entry to boot ISO as the image restore like in Windows image restore. but when ISO gets beyond standard support not sure it provides much.

I keep several flash drives & external SSDs with current ISO and grub to boot them for same purpose, but keep mine up to date.
I keep current LTS as main working install, but have older LTS still installed and just downloaded ISO of 24.10 to add to a test install partition. 
I keep data separate, but not /home so I can access data from all installs. And backup data regularly.

---

