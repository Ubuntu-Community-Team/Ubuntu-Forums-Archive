---
title: "Make GRUB autoload Ubuntu faster"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by RedBluespot on 2010-11-17
[B]I'm running om 10.10. I tried BURG, and then I wanted to change back to GRUB.
So I did the following:[/B]

*sudo grub-install /dev/sda*
[I]sudo update-grub
[/I]
Now I'm back with GRUB... but...


**Problem 1.** I have Ubuntu as the only OS on my system so I don't want the option to press ESC and choose OS everytime I start up my computer. I just want Ubuntu to auto load everytime without text, countdowns and such tidies things.

**Problem 2.** When Ubuntu is booting up it says somthing like "booting from (hd0,0) ext4" or something. I don't want text there either. I just want the "Ubuntu screen".



**This is my /etc/default/grub :**
[I]GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" quiet"
[/I]

---

### Post by RedBluespot on 2010-11-17
Ok, I opened */boot/grub/menu.lst* and changed:

[I]## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
  
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
  **timeout        0**
  
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
  
# Pretty colours
#color cyan/blue white/blue
[/I]
So now it just skips that part.



I still got "*booting from (hd0.0 ext4)*".
GRRRR!!!** How can I make it hide that text?** I don't care what it's booting from.
I just want a nice clean start up.

---

### Post by sikander3786 on 2010-11-19
I feel it a known plymouth issue rather than Grub. There have been problems since Ubuntu switched to plymouth in 10.04.

A workaround here.

[http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/](http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/)

---

