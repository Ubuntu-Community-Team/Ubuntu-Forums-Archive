---
title: "No servers were defined error on boot"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by sm00nie on 2006-09-13
Hi all,

I just grabbed ubuntu today (using Zenwalk as well for the past 2 odd weeks) and when I boot into Ubuntu I'm greeted with an error that reads:

"No servers were defined in the configuration file and XDMCP was disabled."

Would anyone have any ideas how to fix this ?

Thanks,
Shawn

---

### Post by K.Mandla on 2006-09-14
Just to be clear, is this when you boot an install or live CD, or is this after a successful installation?

---

### Post by sm00nie on 2006-09-14
This is right after the installation, when it loads up the gui.

---

### Post by K.Mandla on 2006-09-14
Sounds like some sort of miscommunication between X and your video hardware. Can you tell us what kind of machine you're using, and what kind of video card it has?

---

### Post by sm00nie on 2006-09-14
I went to System -> Administration -> Logon Window, Security tab, clicked Configure X Server, and I added a server (Standard Greeter). 

The error pop up seems to be gone now :D.

Thanks :)

---

### Post by BLTicklemonster on 2007-01-05
The error I got goes as such:

> No servers were defined in the configuration file and XDMCP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration. Note that automatic and timed logins are disabled now.

It's a GDM error for sure, as I'm having fits with mine, and have posted two threads about my problems, neither with a single reply. :(

I have been looking it all over (with no internet connection at the house at present, thank you) and have narrowed it down to...

searching here for an answer, duh.

I'll try the above correction when I get home tonight and get back with the results, as the intardnet ought to be back up by then.

My problem started suddenly without warning, and I'm at a loss to explain it. I'm running Edgy, btw. I could no longer log on to ubuntu as I had before, rather a generic looking login window suddenly appeard. So last night, after trying all kinds of things, I edited gdm.conf to look the same as gdm.conf-custom, then ran the command that is mentioned in that file, and could not connect to a server, and a problem was mentioned with a daemon and /var/somewhere I can't rememeber/gdm.pid (I think) couldn't be found, so it used the exact same file (extraordinary, by my way of thinking). gdm-restart command was not to be found, either. So I logged off and back on, at which time I noticed for the first time, the above quoted error message. 

So something took, but didn't take well enough.


Hopefully tonight will have some success.

---

### Post by BLTicklemonster on 2007-01-07
Didn't do any good. Still having the same problem.

---

### Post by Linux_uptime on 2007-10-24
> **sm00nie said:**
> I went to System -> Administration -> Logon Window, Security tab, clicked Configure X Server, and I added a server (Standard Greeter). 

The error pop up seems to be gone now :D.

Thanks :)

Worked like a charm!  Thanks

---

