---
title: "Upgraded 14.10 to 15.04, lost all TTYs"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by sdgiffin on 2015-08-02
This week, I finally upgraded from 14.10 to 15.04 because 14.10 is now End Of Life, and I was running Cinnamon instead of Unity (if that makes a difference) and now when I boot, I no longer have access to TTYs 1-6 - there's just a blank, black screen and I'm wondering how I get my TTYs back and why they vanished in the first place!

Is there some config setting in [FONT=courier new]/lib/systemd/system/getty@.service[/FONT] that turns TTY access on or off?

Any insight would be great as I'm thinking that I'm going to reinstall upstart and see if that fixes anything unless somebody has a better idea.

---

### Post by dino99 on 2015-08-03
i suppose the TTYs are not gone, you simply does not see them, due to the screen issue. Pay attention to the graphic installation, you should be able to boot on recovery mode to fix that problem

---

### Post by sdgiffin on 2015-08-04
> **dino99 said:**
> i suppose the TTYs are not gone, you simply does not see them, due to the screen issue. Pay attention to the graphic installation, you should be able to boot on recovery mode to fix that problem

I have an AMD (ATI) Radeon HD 6670, and I'm using the v15.200 drivers from the Vivid "Restricted" repository (trying to build from the Catalyst download fails because of a variety of dependency errors which seem to be recursive but which is moot because the newest Catalyst download is v15.200 anyway), and I'm running kernel 3.17.1-031701-generic (x64) because the drivers never worked properly on anything higher.

In X, the graphics work fine. In GRUB, the graphics work fine. During boot, the graphics work fine. Once the desktop loads however, I get only a blank screen when switching to the TTYs. My [FONT=courier new]/etc/default/grub[/FONT] is the same as it was before the upgrade:
```
evilsupahfly@black-beast:~ $ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
#GRUB_CMDLINE_LINUX="cgroup_enable=memory"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080x32,auto
GRUB_BACKGROUND="/boot/portugal.png"
GRUB_GFXPAYLOAD_LINUX="keep"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 4 440 4 440 4 349 3 523 1 440 4 349 3 523 1 440 8 659 4 659 4 659 4 698 3 523 1 415 4 349 3 523 1 440 8"
```

I don't know what else to do since switching back to upstart didn't fix anything.

---

