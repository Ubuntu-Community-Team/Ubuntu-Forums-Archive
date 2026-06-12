---
title: "vga=791 does not work in ubuntu 10.04"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by xuancong on 2010-07-07
hi,
 
I edited the /boot/grub/grub.cfg to set boot option, replace "quiet splash" by "vga=791". It gives me black screen. 
 
But after GUI boots up, if I press Ctrl+Alt+F1(~F6), the resolution do changes correctly, but nothing can be drawn, except my existing desktop. Pressing Alt+F7 can go back as normal. Obviously a bug!
 
Anyone got a fix, if cannot, then how to change console resolution in ubuntu 10.04 after boot since default console is really too small? 
 
Xuancong

---

### Post by drs305 on 2010-07-07
Grub 2 works a lot differently than Grub legacy, and using "vga=" is deprecated in G2. Rather than directly edit the grub.cfg file, Grub 2 has different files in which to set preferences.

In your case, the setting should be placed in /etc/default/grub.

Take a look at this section of [_Grub 2 Basics_]("http://ubuntuforums.org/showthread.php?t=1195275"):
"VGA Deprecated" Message on Boot
It's in Section 17 - Selected Problems & Bugs

---

### Post by xuancong on 2010-07-08
Still no use, my /etc/default/grub now look like this
> 
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
GRUB_GFXMODE=1024x768

But Alt+F1 console is still low resolution. The method doesn't work, how?
 
XC

---

### Post by dabl on 2010-07-08
This might help you:  [http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

---

### Post by linwhwylb on 2010-09-11
> **dabl said:**
> This might help you:  [http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

Nice! This link helps me.

Thansk!

---

