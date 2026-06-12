---
title: "Akonadi - googledata - kontact problems"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bertmanphx on 2010-03-28
Hello,
I have a couple of problems with Kubuntu 10.04 Beta.  Perhaps they are related, I'm not sure.

Upon boot and login, Kontact always startsup automatically.  It seemed to start this after I configured Akonadi with all of the sources I wanted.  I really don't want it to start each time I log in.

Also, the two googldata resources in Akonadi, one for contacts, one for calendar, never remember my password.  I have to open up akonadi-console and reconfigure it upon each login.

Any input would be appreciated.

bertmanphx

---

### Post by bertmanphx on 2010-04-06
Ok,
I totally removed the googledata sources from Kontact and rebooted.  Still, Kontact started upon log in.  strange.

---

### Post by mrowth on 2010-04-06
If you will excuse the sanity check -- have you already tried System Settings' Autostart and Session Manager modules?

---

### Post by bertmanphx on 2010-04-06
mrowth,
A sanity check is always welcome!  Now that I look carefully, it was set to restore previous session.  I set it to start an "empty session".  I'll see if that fixes it.

Thanks much!

bertanphx

---

### Post by bertmanphx on 2010-04-07
mrowth,
That didn't work.  Still, Kontact starts up.  What other directories can I look in, to see if it's listed there to autostart?  I've checked /home/.kde/Autostart

bertmanphx

---

### Post by mrowth on 2010-04-09
Dunno. Maybe when it's running you could run ksysguard/System Monitor (or ps or what have you) and find out what its command and parent process are. Or maybe that's just a silly idea.

---

