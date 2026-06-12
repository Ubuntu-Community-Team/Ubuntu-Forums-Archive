---
title: "Updating"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by Paulo Valadares on 2014-07-26
I have updated to the last Ubuntu release.
It installs perfectly .
When I try open the program appears the wallpaper ,I sign in then nothing more happens .I have to turn off on the main switch.
Somebody can help me ?

---

### Post by ibjsb4 on 2014-07-26
Please clarify

You updated from what release ?? to ??

What release did you start with?
You say the latest release; that should mean 14.04 but could also mean 14.10.
What flavor (xubuntu, ubuntu, lubuntu) and what desktop (unity, gnome)?
If your trying to run the Unity desktop, what are your computer specs (cpu, ram, video)?

---

### Post by Paulo Valadares on 2014-07-26
well system is  AMD Atlhom X2 with 8Gby of Ram  and 5,5 Tby of harddisks
The Ubuntu was 13.04  updated to 14.04 with Gnome
Thanks anyway

---

### Post by Bashing-om on 2014-07-26
Paulo Valadaresl Hekko ;

An update from an End_Of_life version ... humm, did you make it to the current release ?
Show us the outputs of terminal commands:
```

lsb_release -a
cat /etc/issue
uname -r

```

and the quest 
[INDENT][INDENT][INDENT]will begin anew
[/INDENT][/INDENT][/INDENT]

---

### Post by varunendra on 2014-07-26
Welcome to the forums Paulo,

> **Paulo Valadares said:**
> It installs perfectly .

Installs? Was it upgraded using the "Upgrade to..." offer button in 13.04 update manager or a clean install (booted from Live DVD, installed from there overwriting the existing 13.04 installation)?

If I remember correctly, upgrading from 13.04 to directly 14.04 is not possible, so I am assuming you did a clean install. But please confirm that.

And by -
> The Ubuntu was 13.04 updated to 14.04 **with Gnome**
..do you mean installing [Ubuntu Gnome]("http://ubuntugnome.org/download/")?

Lastly, at the login screen, can you log into virtual TTYs by pressing 'Ctrl-Alt-F1' (or ..F2, F3.... etc., Ctrl-Alt-F7 will bring you to the GUI again). If yes, are you able to run normal commands (for example, "ls", "mount" etc.) there?

---

