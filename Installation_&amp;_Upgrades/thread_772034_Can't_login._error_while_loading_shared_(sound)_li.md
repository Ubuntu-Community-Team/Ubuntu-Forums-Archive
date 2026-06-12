---
title: "Can't login. error while loading shared (sound) libraries"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by 3n1gm4 on 2008-04-28
Hi all.
I installed hardy yesterday, and it was cool :)
My problem is that my sound card seems impossible to be used by linux (i've a Realtek ALC655, of the AC'97 series). I'm not asking (now) to help me to install that sound card, my real problem is that seahorse does not log me in cause of the sound card (i guess).

As I log in a popup appears telling me the session lasted less than 10 seconds, and tell me that a log file is created in ~/.xsession-errors

Here is the contents of the file:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/seahorse-agent: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

Is there any way to disable sounds so that seahorse-agent will not look for libasound.so ??

Thank you very much :)

---

### Post by DeadTaco on 2008-11-02
I know I'm bumping an old thread here, but did you ever find a solution to this problem?  I just installed the realtek linux drivers, and now I cannot boot up due to the exact same problem.  Suggestions?

---

### Post by nroussi on 2008-12-10
Ok this is happening to me too. I installed the realtek linux audio drivers and I get the exact same error. Anyone know how to fix this?

---

