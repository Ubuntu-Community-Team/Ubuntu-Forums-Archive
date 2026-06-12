---
title: "Crash duing upgrade leaves me out in the cold."
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by optimusmedia on 2008-10-20
I'm using the 8.10 beta and was running update-manager when the entire system froze.  After rebooting (and fsck) I now only see an empty desktop. No bars, no icons, no right click, or anything else.  Alt-F1 or F2 don't work (to get me to menu or command prompt).  Ctrl-Alt-F1 will get to me a terminal screen.  I tried to run 'sudo apt-get update' and get this error: 

W: Failed to fetch [http://us.archive.ubuntu](http://us.archive.ubuntu)...... (I get a dozen of these with different paths)

I have tried apt-get clean and apt-get autoclean. Neither helps, so I turn to the wisdom of the forum.

Thanks in advance.

---

### Post by overdrank on 2008-10-20
Moved to Intrepid :)

---

### Post by Duck2006 on 2008-10-20
> Ctrl-F1 or F2 don't work

Should be

Ctrl + Alt + F1 or Ctrl + Alt + F2

---

### Post by optimusmedia on 2008-10-20
thanks overdrank.. I should have thought to post it here to begin with.

---

### Post by optimusmedia on 2008-10-20
> **Duck2006 said:**
> Should be

Ctrl + Alt + F1 or Ctrl + Alt + F2

Yes, those work to get me to terminal.  What I should have said was Alt-F1 will not bring up a menu and Alt-F2 will not bring up the command-line thingy :)

---

### Post by optimusmedia on 2008-10-20
Ok.. I'm an idiot.  I am on a wireless connection and it hit me, I'm not getting a connection yet.  ](*,)

Plugged into the lan and bingo, everythings reupdating.. now hopefully that will fix the empty screen.. when it does, I'll post solved here.

---

