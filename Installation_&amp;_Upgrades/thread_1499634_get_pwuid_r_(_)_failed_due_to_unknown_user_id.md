---
title: "get pwuid_r ( ) failed due to unknown user id"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2010-06-02
On a fresh install of Lucid I get the error message
GLib - WARNING **: get pwuid_r ( ) failed due to unknown user id
at start up
I'm not sure, but firefox & synaptic won't start up from the desktop & I think this may have something to do with it.  From the command line 'gksudo synaptic' gives an error of pid already in use

---

### Post by sisyphus1978 on 2010-06-02
I got that. Restart? Worked for me.

---

### Post by sdbrogan on 2010-06-02
I always get it & wonder if it's related to the other problems.

---

### Post by sisyphus1978 on 2010-06-02
I have no problem with sudo, firefox or synaptic.

> I always get it

I've only had it once or twice (maybe only today) and a reboot resulted in a perfect boot. However I did write over my Karmic install with my Lucid install, so maybe this is something to do with a corrupt home directory. Maybe create a new user and see if that helps?

---

### Post by sdbrogan on 2010-06-02
Thanks - I'll give that a try.  Does anyone know what a pwuid_r( ) is, or why it should fail ?  I had the message once on my netbook, & it wouldn't boot up; but on restarting it was all right.

---

### Post by Ken Jannot on 2010-06-10
I get that message at the tail end of my installation when I try to install (with a cd) 10.4 over 9.10 -- it starts the installation, then that message pops up. The installation goes no further. Can anyone tell me why this would be?

---

### Post by thepocketdrummer on 2010-08-19
I'm having this problem too with an old Asus laptop. I'm going to try via USB and see if that works.

---

### Post by thepocketdrummer on 2010-08-19
laptop won't boot from USB... grrr

Same error from live-cd too. Everything seems to freeze when this happens, too.

---

