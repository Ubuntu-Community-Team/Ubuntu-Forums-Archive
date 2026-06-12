---
title: "Process:238 Glib-Warning?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NoVista on 2010-04-23
On Lucid, started getting this error about 4 days ago.
It goes right to a black screen, everything is frozen, and in the top left corner, I get the following:

(process:23) Glib-WARNING** getpwid-r(): failed due to unknown user ID (0)

Trying REISUB is unable to get me a reboot.
All I can do is a hard reset. 
I am current on all updates.
I would appreciate some help here.

---

### Post by dino99 on 2010-04-23
> **NoVista said:**
> On Lucid, started getting this error about 4 days ago.
It goes right to a black screen, everything is frozen, and in the top left corner, I get the following:

(process:23) Glib-WARNING** getpwid-r(): failed due to unknown user ID (0)

Trying REISUB is unable to get me a reboot.
All I can do is a hard reset. 
I am current on all updates.
I would appreciate some help here.

googling around, found this:

[http://www.technologyquestions.com/technology/linux/122962-getpwuid_r-failed-due-unknown-user-id.html](http://www.technologyquestions.com/technology/linux/122962-getpwuid_r-failed-due-unknown-user-id.html)

Just a follow up. Running nscd* fixed this.
[*] - [http://tldp.org/HOWTO/archived/LDAP-...TO/pamnss.html](http://tldp.org/HOWTO/archived/LDAP-...TO/pamnss.html)

---

### Post by NoVista on 2010-04-23
Well, those links seem to provide information way above my noobish ways :(

If it matters, I should point out, i reset or changed my password via the "password and encryption key" in the main menu a few days ago, as I was recommended to do so for an unrelated queation to this . Not sure because of that if I changed something for the worse.

---

### Post by cariboo on 2010-04-23
If you need to change your user password, it is done in **About Me**, available when you left-click your user name.

---

### Post by NoVista on 2010-04-23
glxinfo just confirmed GLX has been regressed back to version 1.2 from 1.4 and it solved the problem :)

---

