---
title: "Edit grub.cfg to incorporate &quot;noapic nolapic&quot;"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by idiotonuni on 2010-02-08
Can someone please explain to me how to edit the new grub.cfg file.  For some reason when I start any version of linux none of my usb ports are powered unless I use these boot parameters (noapic nolapic).  I have no idea why and I don't really care why, all I want to do is edit grub.cfg so it will incorporate these parameters automatically at startup.  Links to others posts will be gladly appreciated.  Thanks in advance and sorry for the negative tone.

P.S. Why change from the old menu.list?

---

### Post by Herman on 2010-02-08
You are not supposed to edit /boot/grub/grub.cfg directly.
Instead, the file you should edit is called /etc/default/grub, and you may open it with the text editor gedit,
```
gksudo gedit /etc/default/grub
```It should look something like this, 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
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
```You should add your boot options like so, 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[COLOR=Blue]**noapic, nolapic**[/COLOR]"

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
```Save the file and close it and then run 'sudo grub-mkconfig -o /boot/grub/grub.cfg', to write the changes persistently to your grub.cfg.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by akatsuki5 on 2010-02-16
Herman...Thank You!!

I'm no longer getting a Kernal panic msg upon boot, thanks again.

---

