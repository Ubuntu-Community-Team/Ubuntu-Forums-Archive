---
title: "New Install of 7.10 -- VT font?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Mesa Mike on 2007-10-30
Red Hat 9.0 was getting long in the tooth, so I just installed 7.10 on my Dell GX270.

So far, pretty good. 

However a few observations:

When I switch to a VT with CTRL-ALT-Fx, the font is HUGE. It makes the VT useless.
Where should I look to change this?

All the IDE disks show up as SCSI devices. I suppose this is as it should be, but that was a bit confusing at first. Whatever. It works.

Also, I'm used to seeing stuff fly by on the screen as the system boots up. What I get now is just a blank screen until the window system starts up and displays the login screen. I'd really rather see evidence that the boot up process is actually in process, even if I can't read the stuff that fast. Can I change this behavior?

---

### Post by rbmorse on 2007-10-30
On the last question, open /boot/grub/menu.lst with a root-permissioned text editor. Find the line that reads  

## END DEFAULT OPTIONS ## ##

and below that find the section pertaining to your 7.10 installation.  Remove the keyword "quiet" from the line beginning with "kernel."

---

### Post by Mesa Mike on 2007-10-30
OK, did that.

Now I get some bootup messages for about a second, then the screen goes blank for the rest of the bootup.

What else?

---

### Post by Mesa Mike on 2007-10-30
OK, I got the blank screen during bootup and huge ugly font on virtual consoles fixed by eliminating the "splash" parameter on the kernel line in my grub config.

---

### Post by rbmorse on 2007-10-30
My bad.  I knew it was either "splash" or "quiet" and guessed wrong. 

Glad you got it working.

---

