---
title: "Amarok/xine engine problem"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by LHZ on 2005-10-12
I have a problem with amaroK. I've installed amaroK and libxine1 (but not xine itself) and for my user account everything works fine (my account is the only one with sudo privileges). 

However, when other user accounts start amaroK, it loads with the 'void' audio engine (which has no output to speak of). If you select the xine engine manually, you get the error message 'xine could not initialize any audio drivers'.

I've searched around on these boards and the amaroK boards, but couldn't find anything. I think something's wrong with the file permissions, but I don't know which files, or where to find them.

Does anybody have an idea? Thanks in advance.

---

### Post by mlomker on 2005-10-12
> I've searched around on these boards and the amaroK boards, but couldn't find anything. I think something's wrong with the file permissions, but I don't know which files, or where to find them.


Have you added your additional users to the 'audio' group?

```

sudo usermod -G audio *username*

```

---

### Post by aysiu on 2005-10-12
I have an idea, but I don't know if it'll work. In the user options, there are various "groups" you can add users to. Make sure the new users are in the same groups as your account is in (except sudoers).

---

### Post by LHZ on 2005-10-13
Thanks, both of you! Adding the other users to 'audio' worked like a charm.

(also, sorry I made my first post in the wrong forum. I feel like an idiot)

---

### Post by mp3guy on 2005-11-27
The same thing happened to me and mlomker's solutioned worked a treat, thanks alot!

---

