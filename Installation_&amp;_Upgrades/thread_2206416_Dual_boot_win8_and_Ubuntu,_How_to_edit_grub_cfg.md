---
title: "Dual boot win8 and Ubuntu, How to edit grub cfg?"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2014-02-18
Got a call asking for a dual boot win8 and Ubuntu on a rather old Latitude D430 laptop.

Quite simple: with a blank 80Gb Hdd, use win8 DVD delete all partitions and allocate 47Gb for windows, it automatically created a small NTFs partition for its bootloader (I guess). Leave 30 some Gb unallocated space for Ubuntu late.

After win8 installation is done. Boot with Ubuntu Live Usb,

1. Select install Ubuntu
2. Select Something else (custom installation)
3. Add ext4 partition 20Gb for /
4. Select partition / for grub install location
5. Create /home and swap partitions within a logical closure, that used up all the hdd space left.
6. When Ubuntu installation is done, restart the system and it automatically boots into win8 as if nothing done about Ubuntu. 
    This is because Ubuntu partition / is not active and nothing altered within window partitions.
7. Search on web, find no clear enough instructions about how to make a linux partition active for me. I boot the system with 
    a mac os installer usb. Using its utility (terminal, diskutil and finally, fdisk) to set partition / active.
8. Reboot without usb drives, the grub boot menu appears with several boot options including boot to windows 8, and it worked!

One more thing: How to config grub to shorten the count down time for default boot option? And How to make win8 the default OS (not for me)?

Thanks for your help

---

### Post by Bucky Ball on 2014-02-19
You DON'T edit grub.cfg. You edit /etc/default/grub then run 'sudo update-grub'. Your changes are then sent to grub.cfg.

Open a terminal and:

sudo nano /etc/default/grub

Look for the timeout lines and experiment. Don't forget 'sudo update-grub' after you finish tweaking and close the file. Generally a good idea to make a copy of important files before tweaking. ;)

PS: You can also boot from the Live Ubuntu install media to make partitions active (among other things) using Gparted from a Live desktop.

---

### Post by oldfred on 2014-02-19
Active has nothing to do with grub. That is seen as the boot flag in Linux. And Windows in BIOS mode uses boot flag to know which partition to boot from. Grub does not use boot flag.
But if still booting Windows then you did not install grub2's boot loader to MBR.

You still have to turn off fast boot or the always on hibernation with Windows 8.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by elim-qiu on 2014-02-23
> **Bucky Ball said:**
> You DON'T edit grub.cfg. You edit /etc/default/grub then run 'sudo update-grub'. Your changes are then sent to grub.cfg.

Open a terminal and:

sudo nano /etc/default/grub

Look for the timeout lines and experiment. Don't forget 'sudo update-grub' after you finish tweaking and close the file. Generally a good idea to make a copy of important files before tweaking. ;)

PS: You can also boot from the Live Ubuntu install media to make partitions active (among other things) using Gparted from a Live desktop.

Thanks Bucky Ball!  I modified the timeout value and it works immediately.
But I don't know how to make windows as boot default. Looks like grub detect windows at runtime....

Below is the complete content of the file /etc/default/grub:


```
root@eLnx:/etc/default# cat grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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
root@eLnx:/etc/default# 


```

---

### Post by fdrake on 2014-02-23
this will help [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)
check the dafault entry section

---

### Post by Bucky Ball on 2014-02-23
All good if you want to install Grub Customizer, but you may not. Quicker way by tweaking the file explained [HERE]("https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries").

Check point 1 under 'Specific Entries - 2/ GRUB_DEFAULT='

That's what you're looking for to change the default OS. Same file, /etc/default/grub. ;)

PS: Nothing against Grub Customizer. I used to use it all the time, once upon a time.

---

