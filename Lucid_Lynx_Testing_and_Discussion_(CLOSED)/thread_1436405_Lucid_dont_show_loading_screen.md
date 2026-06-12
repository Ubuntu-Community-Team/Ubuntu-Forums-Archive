---
title: "Lucid dont show loading screen"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pjalegria on 2010-03-22
Hi

I have made the upgrade to my karmic UNR to Lucid, everything works well only at boot, i dont have lucid loading screen, it shows only messages :cry:
How can i fix that???

Thanks

---

### Post by pjalegria on 2010-03-22
come on guys...

---

### Post by Xorlathor on 2010-03-22
You expect an answer 24 minutes after you post? Patience is a virtue; use it. 

Yes, that means I have no answer. Sorry.

---

### Post by pjalegria on 2010-03-22
My grub...

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop pciehp.pciehp_force=1 enable_mtrr_cleanup"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

