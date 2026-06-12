---
title: "Installing 11.04: new GRUB or old GRUB?"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by apocalypsemystic on 2011-05-17
So I started installing 11.04 on my 2007 black macbook that runs Mac os snow leopard, vista, and ubuntu 10.10 and boots with mac rEFIt. My upgrade froze during install, so I went to a virtual tty and killed a random emacs process that I had been running before install that was taking up 100% cpu. I killed the frozen update manager and used sudo dpkg --configure -a to and update to continue. 

Now I am at a screen with the message "A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified. What do you want ot do about modified configuration file grub?" And I can "install the package maintainer's version," "keep the local version currently installed" or view various diffs of things. I have no idea what route to take and I am afraid of screwing something up. Can anyone help? Thanks.

---

### Post by garvinrick4 on 2011-05-17
> Now I am at a screen with the message "A new version of configuration  file /etc/default/grub is available, but the version installed currently  has been locally modified. What do you want ot do about modified  configuration file grub?" And I can "install the package maintainer's  version," "keep the local version currently installed" or view various  diffs of things. I have no idea what route to take and I am afraid of  screwing something up. Can anyone help? Thanks.
Here is that cfg file below:
Do you know what changes you made, mine only has a difference in the 1024x768 
some have made changes to boot with different option in grub_cmdline_linux or grub default line. If you make no changes do not worry about it. If you do not remember having to do things with this page to boot do not worry about it. If you worry keep local version installed.
You can always upgrade if you want. 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
 GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by apocalypsemystic on 2011-05-17
hmm. it looks like the only things that have changed have been commented lines anyway. shall I use the new grub from the package manager?

---

### Post by garvinrick4 on 2011-05-17
> hmm. it looks like the only things that have changed have been commented  lines anyway. shall I use the new grub from the package manager? 	
Your decision, your machine, you call it, I just showed you what config file it is. Good luck partner. You should have chosen a longer handle.

---

### Post by apocalypsemystic on 2011-05-17
I went ahead and got the new one and after some other issues it looks like unity is up and running.

---

