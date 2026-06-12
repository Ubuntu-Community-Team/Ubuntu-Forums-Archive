---
title: "Post 9.10 install and updates ... can no longer login!"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by clarkejr on 2009-11-25
I installed 9.10 (not an upgrade) yesterday and all was working fine. Ran the update manager today and installed recent updates (including new kernel ... not sure if this is relevant or not).
After reboot and during the graphical startup screen, some errors appear as small text on the screen but they are too brief to read, and then I go to the graphical login but with no list of users to choose from.
I've booted from the LiveCD so I can write this post ... any ideas on what I need to do to get a working login prompt again? Not even sure where to begin looking... Thanks.

---

### Post by clarkejr on 2009-11-25
Any ideas on what I could do to get this system back to functioning again?

Considering re-installing 9.04 ?

---

### Post by clarkejr on 2009-11-25
I've been reading some of the other users problems after install and more importantly the update to a new kernel.

Because I only have Ubuntu on this machine, I wasn't seeing the grub menu. I tried pressing "shift" while it was starting but it didn't appear to do anything (I'm doing something wrong). So I read the "Grub2" community documentation and founf out that by editing /etc/default/grub and commenting out GRUB_HIDDEN_TIMEOUT=0, then running "sudo update_grub", I was at least able to see my startup options (I had to ssh login from another machine to do all of this).

Unfortunately none of this has helped me.

I have tried the 30.15 recovery mode and booting with the original 30.14 kernel but both leave me at the same point ... which is a graphical login and no users to select from.

I hope this helps someone as there appear to be a lot of us with broken systems post updates on our new Karmic installs.

---

### Post by clarkejr on 2009-11-26
OK ... so maybe not the perfect solution to my problem, but I can login to my sytem again and everything else is working just fine.
The instructions at [http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/](http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/) helped me to disable the "user list" login and now requires me to type in my username and password (via a graphical window) which is more secure anyway.

---

