---
title: "Bootup resolution problem under Ubuntu 7.10"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by matpiw on 2007-11-16
Hello,
I've just upgraded to Ubuntu 7.10 and I can't get 1024x768 resolution during boot up or neither in any of the consoles (I mean those under Ctrl-Alt-F1 through F6). Under 7.04 everything was working fine, so I have no idea what's the problem. Standard 640x480 resolution works fine, but when I change it to any higher one (via vga parameter in the grub config file), the screen just stays black during boot up. Thanks for any help.

---

### Post by scorp123 on 2007-11-16
> **matpiw said:**
>  Under 7.04 everything was working fine, so I have no idea what's the problem. Standard 640x480 resolution works fine, but when I change it to any higher one (via vga parameter in the grub config file), the screen just stays black during boot up.  As they say at Microsoft: "It's not a bug ... it's a feature!" ... Sorry for this sarcasm -- I am just as frustrated about this as you probably are. But it's sad truth: Canonical disabled the Framebuffer devices and therefore you can't get any higher text modes beyond 80x25 ... They claim that framebuffers break suspend + hibernate on some machines. 

Workaround --if you really want to enable framebuffers again--
Follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

And then the ones here:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

This should fix the resolution + the Ubuntu splash screen during boot + shutdown.

---

### Post by matpiw on 2007-11-16
Thanks! This worked perfectly. Now I can finally access my tty's :)

---

