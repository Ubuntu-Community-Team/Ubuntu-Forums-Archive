---
title: "GRUB2 configuration unclear"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2011-07-17
Hi,

I need to debug upstart because it really doesn't start the jobs at system start that it should do. The upstart documentation says I need to add the kernel parameter "--verbose". Googling a bit further said I need to specify that parameter in the /etc/default/grub file. I found two lines where I can add it: GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT.

The grub documentation remains unclear about what is good for which. Shall I add my verbose parameter to the one or the other? What's the difference between the two anyway? The _DEFAULT currently contains "nomodeset" and the other is empty. Does one replace the other, or will one be appended to the other?

I don't want to screw up my system with this because I only have SSH remote access to that server.

Could somebody please help me out (or update the documentation and tell me)?

I'm on Ubuntu 10.4.

---

### Post by Quackers on 2011-07-17
Does "quiet splash" appear in one of them?
What jobs aren't starting?

---

### Post by ygoe on 2011-07-17
Here's my current /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""

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

```

My own logstate job isn't starting. I have created other jobs that do start. The logstate job doesn't even seem to be regarded, my logger call in the script doesn't get called. But I can start, stop and status the job interactively though. It is there, it is readable and it is okay. upstart just doesn't see it when booting. (See [my other thread]("http://ubuntuforums.org/showthread.php?t=1748525") about it.)

---

