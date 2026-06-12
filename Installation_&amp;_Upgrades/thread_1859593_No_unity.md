---
title: "No unity?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by eliastoon on 2011-10-14
Okay so my 11.10 upgrade went fine for my first use. Then I rebooted my computer. I can get past the login screen, but once the screen loads, I am missing the unity sidebar, and the right hand part of the global menu bar. I can see my desktop with all my files and can navigate around nautilus it seems, but I don't have the ability to do much else. Where is unity? I don't know all the correct terms for many of these things but I have no unity side bar, and on the top bar the only things displayed are File through Help. No other icons. Any help would be appreciated. Thanks.

---

### Post by rgezikov on 2011-10-14
+1. I have the same problem. Previous version was 11.04.
I used recommendation from [this page]("http://www.addictivetips.com/ubuntu-linux-tips/get-classic-start-menu-in-ubuntu-11-10-oneiric-ocelot/") to install Gnome shell. I got some shell, looks little bit different from Gnome as I remember it, but allows to start other applications at least.

I found also that Google Chrome crashes immediately after start, but FireFox works.

---

### Post by rgezikov on 2011-10-14
Btw, forgot to add: when you log in and see just Nautilus menu you can hit Ctrl-Alt-Del to logout. Then there is an option to start recovery console. That's not a solution, of course.

---

### Post by garvinrick4 on 2011-10-14
Open a terminal and: (ctrl/alt/t)
```
unity --reset
```

---

### Post by eliastoon on 2011-10-14
Yeah already tried that. Nothing on unity --replace or unity --reset. Thanks though

---

### Post by eliastoon on 2011-10-14
Okay so after awhile of messing around I think I have it. Up top you should still have the option to select go. Navigate to Go>File System>Usr>Applications>CCSM (Compiz Manager). Reselect Unity Plugin within there! Fixed mine.

---

### Post by RawwrBag on 2011-10-14
Yup, unity --reset seems to be broken. From the recovery console it segfaulted but from my gimped X session it just hung forever. Is there a bug on this yet?

---

### Post by rgezikov on 2011-10-14
I went to recovery console from login screen and typed 'unity --reset'.

First frame around console window appeared and then disappeared in couple of seconds. Then there was a kilometer of output to the window.

Then there were many error like:
"compiz (core) - Error: Could not load plugin '...'"

Now it hangs with last line 'Setting Update "run_key"'.

Any idea what to do now? Should I cancel this command?

---

### Post by rgezikov on 2011-10-14
I tried the same after logging to Ubuntu shell that is supposed to be Unity. A result is the same.

Does anybody know what causes "compiz (core) - Error: Could not load plugin '...'" messages and how to fix that?


Btw, in Go I don't have File System. how can I start CCSM from command line?

---

### Post by LostOverThere on 2011-10-14
> **rgezikov said:**
> I tried the same after logging to Ubuntu shell that is supposed to be Unity. A result is the same.

Does anybody know what causes "compiz (core) - Error: Could not load plugin '...'" messages and how to fix that?


Btw, in Go I don't have File System. how can I start CCSM from command line?
Control-Alt-T to start the terminal, and then simply type ccsm.

---

