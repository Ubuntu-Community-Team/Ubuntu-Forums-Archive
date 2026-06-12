---
title: "Dual boot lost after 24.04 upgrade"
date: 2024-09-24
forum: Installation &amp; Upgrades
---

### Post by jrmsco on 2024-09-24
Acer laptop dual booted with Win 10 and (default) Ubuntu 22.04.
I ran the 24.04 upgrade (via Synaptic package manager) and it ran perfectly.
During the process it detected the Win 10 installation.
When I restarted the machine, boot up went straight into Ubuntu 24.04 - no Windows choice.
Anyone know how I can fix this without a whole lot of re-installation ?
Many thanks.

---

### Post by yancek on 2024-09-24
You were successfully booting both your earlier version of Ubuntu and windows 10 successfully, correct.  Did you have both installed on the same physical drive?  Were you booting both from a grub menu?  Try running:  sudo update-grub from Ubuntu and see what happens.  Watch the output and you should see an entry for windows and if you do, reboot and select it to see if it boots.  os-prober may be disabled so try update-grub and if it fails, post back with warning or error messages you see.

---

### Post by jrmsco on 2024-09-25
Thank you Yancek for your input.
I've used dual-boot for years with few problems (usually always caused by M'soft !)
Both OS's are on the one SSD - both were started from a GRUB menu. The grub menu has just 'disappeared'.
I ran update-grub - it found the Win10 installation and said it was adding it to the menu.
Command output as follows...

jrm@jrm-Aspire-7740:~$ sudo update-grub
[sudo] password for jrm: 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found linux image: /boot/vmlinuz-6.8.0-40-generic
Found initrd image: /boot/initrd.img-6.8.0-40-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sda1
Adding boot menu entry for UEFI Firmware Settings ...
done
jrm@jrm-Aspire-7740:~$ 

Sorry to say but the re-start was no different - slightly longer tan normal wait then straight into Ubuntu.

---

### Post by tea for one on 2024-09-25
Can you show your configuration from /etc/default/grub?

---

### Post by jrmsco on 2024-09-25
Hi Yancek,
Update to my previous reply - IT'S WORKING.
I re-ran update-grub a couple of times and finally, the boot list appeared.
Boot-up, login and apptest on both systems working 100%.
Quite why it has started to work, I cannot say but I am greatly relieved.
THANKS for your input.

---

### Post by jrmsco on 2024-09-25
Problem solved - see above - thanks for your interest.

---

### Post by jrmsco on 2024-09-26
Unfortunately the problem is not solved as it has appeared again but is now reproducible.
If I hit F2 (BIOS access) at bootup, the grub menu appears randomly.
Sometimes the bootup will go into the BIOS - sometimes it is ignored and sometimes the menu will appear.
Very erratic behaviour and I can't make any sense of it.
The contents of etc/default/grub are as follows...

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
#GRUB_DISABLE_OS_PROBER=false

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal
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

I am a bit puzzled as to what is happening here particularly when pressing F2.

Any help greatly appreciated.

---

### Post by tea for one on 2024-09-26
I think that you should edit your Grub configuration
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
[s]GRUB_TIMEOUT_STYLE=hidden[/s] [COLOR="#0000FF"]#change hidden to menu[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[s]#GRUB_DISABLE_OS_PROBER=false[/s] [COLOR="#0000FF"]#remove the comment symbol # at the beginning of the line[/COLOR]
GRUB_DISABLE_OS_PROBER=false 

```
```
sudo update-grub
```
Power off and then boot.
Happy days or Sleepless nights?

---

### Post by jrmsco on 2024-09-26
Thank you tea for one  - that's solved it.
Fully tested and working correctly every time.
Once again, many thanks.

---

