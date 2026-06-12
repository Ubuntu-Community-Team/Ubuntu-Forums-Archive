---
title: "Gutsy Upgrade Problem - Screen updates are choppy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by foulox on 2007-10-23
Hi everyone,

This is my first post to these forums.  So please be easy on me.  I am using a Dell X1 which has a 915gsm video card.  When I was running 7.04 things were fine not great but fine, like I couldn't get two monitors running and I had to shutdown gdm if I ever wanted to switch between my laptop screen, a monitor or a projector, which wasn't so bad.

Now that I'm upgraded to 7.10 when ever I move a window around a screen or scroll through a document or a webpage the display is extremely choppy.  How can I fix this?  I doesn't matter if I have Desktop Effects on or off.  It is really so annoying that I'm considering doing a complete wipe and re-install, and if that doesn't work, then I was going to roll back to 7.04, but I would love to use this to get a little smarter and  understand why this is happening.

---

### Post by cygnis1 on 2007-10-23
This also happened to me.  See this post:
[http://ubuntuforums.org/showthread.php?t=580721](http://ubuntuforums.org/showthread.php?t=580721)

---

### Post by foulox on 2007-10-23
Thanks for the reply

I did exactly what that post said- 

sudo apt-get remove xserver-xgl

And now it's working great.  And Compiz is still working for me.

---

### Post by cygnis1 on 2007-10-23
Glad I could help.
Cygnis1

---

