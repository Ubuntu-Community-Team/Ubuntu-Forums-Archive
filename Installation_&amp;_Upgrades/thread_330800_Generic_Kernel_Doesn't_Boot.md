---
title: "Generic Kernel Doesn't Boot"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by ben::zen on 2007-01-03
I'm using ubuntu 6.10, and I run an Intel Pentium D 805 processor. I would like to be able to run both processors in SMP, but whenever I try to boot the kernel, it will show the splash screen, and hang. I switch to TTY1, but all it shows is what GRUB shows on bootup, nothing different. I can leave it sitting for some time, and it will do nothing. I thought this was the right board, but I wasn't sure.

---

### Post by bernied on 2007-01-03
If you managed to install on this hardware, then you know that a linux kernel will run on it. If you know how to gain access to your install using the live-cd (install cd), then you could try altering the kernel options in the file /boot/grub/menu.lst

If this is all gibberish to you, say so, and someone here will do their best to step you through it.

First question - does the live-cd boot up ok?

---

### Post by ben::zen on 2007-01-10
Sorry- I ws having trouble logging into the forums. Well, no, the livecd won't boot. It just sits for a long time, then gives me an error about how the TTY1 won't work. I've tried numerous times, but it always gives me the same error.

---

### Post by bernied on 2007-01-11
So you don't even get any boot options? - you might try hitting a few random F keys. Maybe F1. This might give you boot options.
[EDIT]Also try hitting Esc key during boot process.

If you are able to change boot options, then you can try disabling acpi, using either 'noacpi' or 'acpi=off'.

A couple of other threads that might apply to you:
[This one](http://www.ubuntuforums.org/showthread.php?t=7867)
[Another](http://www.linuxforums.org/forum/ubuntu-help/64750-live-cd-not-loading.html)

If you cannot change boot options, then you could also try the 'alternate install CD' but that might involve another download.

Some more information about your hardware might be helpful. Most problems have happened before to other people, unless you have really new stuff.

---

### Post by bernied on 2007-01-11
[A link](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface) to describe acpi. Sometimes this doesn't work - the install will work without it and you can get it working later.

---

