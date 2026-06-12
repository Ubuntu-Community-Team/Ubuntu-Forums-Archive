---
title: "Boot menu"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by pokerjo on 2012-03-12
Hi sorry if this is in the wrong place or if it has been answered before but im not sure what to search.

I have a tripple boot system, OSX, Ubuntu, Windows7. I use a Chameleon boot loader to select which OS to boot.

When i select Ubuntu in the Chameleon boot loader screen i then get another boot menu to choose which OS to boot into, is there a way to stop this happening, i.e. like the editing the boot.plist for the Chameleon boot loader, when i select Ubuntu in the Chameleon boot loader screen i want to go straight into the OS with out any other menus.

Many thanks for any help with an answer or pointing me in the right direction with what to search.

Im sure i dont need to say but im a massive Ubuntu/Linux noob.

thanks  :D

---

### Post by sudodus on 2012-03-12
When running Ubuntu, in the file
```
/etc/default/grub
``` you can edit as root
```
sudo nano /etc/default/grub
```

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

``` to set timeout=0 and it necessary select another default (grub default=0 means that the first line is selected) and run
```
sudo update-grub
``` afterwards

---

