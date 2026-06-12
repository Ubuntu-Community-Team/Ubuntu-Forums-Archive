---
title: "BURG and Burg-Manager doesn't save the default OS to boot"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by InTheMarket on 2010-11-26
Most of my family uses Windows 7, so I'm trying to get burg to respect that like grub does.

In Burg-Manager (the only way I found to edit burg info) I set default OS to boot as windows 7. However, it still picks Ubuntu.
Here's my etc/default/burg config file:
```

# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

GRUB_DEFAULT=2
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
GRUB_SAVEDEFAULT=true

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# In the boot menu, use hotkey 'r' to popup a resolution selection menu.
GRUB_GFXMODE=saved

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# GRUB_THEME's value can be 'saved' or a specific BURG theme name, you can also
# set it to the pathname of a GRUB2 theme file.
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=saved

# GRUB_FOLD's value can be 'saved', 'true' or 'false'.
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved

# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="

# For a complete list of supported variables, refer to this wiki page:
# http://code.google.com/p/burg/wiki/ConfigurationVariables

```It might be just me and lack of sleep, but I scanned through that file and dunno which thing to change to make it select windows as default OS to boot.

Any help?
It may be relevant that I have Start-Up Manager installed, but it shouldn't matter, as that has windows as the default too. And it seems like BURG-manager overrides it anyways.

Thank you for your help

---

### Post by InTheMarket on 2010-11-30
Bump, anyone, any ideas?

---

### Post by InTheMarket on 2010-12-04
Tried modifying the grub2 files as well, no such luck.

---

