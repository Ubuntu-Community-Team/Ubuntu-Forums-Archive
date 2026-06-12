---
title: "2 things - question about root password and installer suggestion"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by linuxpenguin on 2006-06-23
I just tried Ubuntu 6.06's quick-and-easy LAMP server set up.

I feel like an idiot - I don't know root's password!  Did the installer set it to some default password?  If so, what is it?  I need it to install Webmin don't I?

Also, your text-based installer (at least for the LAMP server) is really hard to see on my old projector.  Maybe for the next release you should use something with a little more contrast - maybe black on light blue or something rather than blue on blue.

---

### Post by will_in_wi on 2006-06-23
Ubuntu doesn't do root. You run all superuser commands with sudo which uses your password to authenticate. If you want a root shell though, type sudo -i.

---

### Post by linuxpenguin on 2006-06-23
Thanks, I found a thing through Google that told me how to set up root.

Yes, Ubuntu will do root: turns out you can type "sudo passwd root" to set up the root password.  Sometimes for the few times I actually need to log into the server it's handy to just log in as root.  I know it's not as secure but still. . . I usually don't need to do it.

---

