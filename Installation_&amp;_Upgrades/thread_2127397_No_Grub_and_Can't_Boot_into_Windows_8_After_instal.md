---
title: "No Grub and Can't Boot into Windows 8 After installing Ubuntu 12.10"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by THPubs on 2013-03-19
First, I installed Windows 8 in my desktop PC. (Not pre-installed... I did it by myself). Then I booted the Ubuntu dvd in UEFI mode (Did the same with Windows 8) and installed Ubuntu 12.10 64bit. Everything went perfectly. After rebooting, there's no grub! The system took me directly to Ubuntu! I can't log into Windows 8. Please help! Earlier, I used Boot Repair and it messd up with my Windows EFI files. So I was unable to boot Windows even after removing Ubuntu. I can't use boot repair. Now this is a new fresh install, Please tell me how to boot into both Windows 8 and Ubuntu!

Here is my /etc/defaults/grub :

> # If you change this file, run 'update-grub' afterwards to update
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
#GRUB_GFXMODE=1024×768
#GRUB_GFXPAYLOAD_LINUX=1024×768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by oldfred on 2013-03-20
We need a link to BootInfo from Boot-Repair.

But grub2's os-prober does not create correct entries for UEFI dual boot. It still creates the old BIOS entries that do not work with UEFI. So you have to use Boot-Repair to add correct entries. 
And if you do not have secure boot do not check that and have Boot-Repair rename files. That should not be needed except for those pre-installed systems that only boot the Windows efi boot file.

Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.p...769482&page=71]("http://ubuntuforums.org/showthread.php?t=1769482&page=71")
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in  case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or  secure boot
signed GRUB file shimx64.efi.

grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+s...2/+bug/1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383")
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

