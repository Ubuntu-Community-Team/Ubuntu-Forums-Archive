---
title: "Really weird problem while booting"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by TB2 on 2007-08-21
Hi,

I installed Ubuntu on a free partition as a 2nd OS besides XP. Now this is, how the booting process looks like on my machine - ever since I installed it.

1. Everything until grub is fine, and grub shows its menu. I can choose the different modes, memtest or XP. I use two screens, and my GeForce 8800 only shows the BIOS and all that on the primary display.
2. The primary screen goes black and then to stand-by (the seconday is still/already in standby).
3. I wait a couple of seconds, until I don't hear the harddisks working anymore.
4. Nothing happens. Ever. If I press some keys, like CTRL-ALT-F1 or random keys, some of them give a system beep at random, some of them don't. E.g. "right arrow" gives a beep, the other arrow keys don't. If numlock is off, 3, 5, 6 and 9 also beep. BUT... if I press CTRL-ALT-DEL the gdm login shows up after 3 seconds or so... o.ô
5. I can login, nearly everything works fin (except for shutdown)

So I don't have a clue, why this is happening. I have never seen the Ubuntu logo and the progress bar since I installed the OS. nVidia drivers are installed, I run compiz-fusion and all that fancy stuff, grub seems to be fine... I don't get it.

One thing worth mentioning might be, that if I start in recovery mode, I see the verbose booting process, and the screen doesn't go black. I also get an error "File system check failed blabla", but I don't think it has anything to do with the actual problem, as the screen turns black almost immediatly after I choose to start Ubuntu in Grub. The only thing I can see before it turns black ist that Grub stuff:

Kernel alive
Kernel direct mapping tables up to 10000000 @ 8000-d1000

This is kinda annoying. Does anyone have an idea why CTRL-ALT-DEL doesn't act as "reboot" if pressed in that situation and why this is happening? Btw when I had trouble configuring the screens it happened, that CTRL-ALT-DEL didn't work to show up gdm. In that case pressing the keys a second time rebooted the machinie.

Any ideas?

---

### Post by HW_Hack on 2007-08-22
Hmmmm  - not really an expert but heres something to try

When de-bugging its always best to simplify

- try un-plugging the power cord of your 2nd monitor and see if ubuntu boot ok on your primary monitor

I assume your XP partition still boots and runs fine 

ctl+alt+del    only works on pretend operating systems :)

---

### Post by TB2 on 2007-08-23
I inserted "vga=791" into the krenel line in /boot/grub/menu.list and this solved the problem of the ubuntu logo and status bar not showing up, and it also surfaced why this CTRL-ALT-DEL thing happened. It actually was the fchk error which opened a maintenance console which was only cloasable by CTRL-ALT-DEL (ant not CTRL-D as stated)

---

### Post by mrfelker on 2007-08-23
After the boot message (blah as you say) do you get a prompt to enter the root password (but you probably don't have one if you use sudo)  or CTL-D.  Hit CTRL+D and you will get the graphic login to Ubuntu.  I've never fixed the problem using the recovery mode.  If you don't have data you have to save I'd just re-isntall Ubuntu

---

### Post by TB2 on 2007-08-24
I guess I'll fix the problem some day ;) And if not, I think I'll just get Ubuntu to ignore or workaround the issue. Everything else is working, so I don't care too much about pressing CTRL-ALT-DEL when booting ;)

---

