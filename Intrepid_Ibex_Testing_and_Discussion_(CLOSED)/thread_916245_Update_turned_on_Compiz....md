---
title: "Update turned on Compiz..."
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by exploder on 2008-09-10
One of todays updates turned on Compiz. I can turn off Compiz but every time I restart, Compiz comes right back on by itself.

Anyone else notice this?

---

### Post by MaX on 2008-09-11
Nope, but for me it cleared all my compiz settings and reverted back to "basic" mode.
Also alot of stuff stopped working in Compiz.

I'm still using the old kernel (2.6.26-5-generic ) since nvidia refuses to work on the newer.

---

### Post by ronacc on 2008-09-11
like max I lost my settings but still have to start compiz each boot , for me it won't stay activated nor will fusion icon .

---

### Post by Nullack on 2008-09-12
Yeah Ive got this. I run compiz off (because it doesnt work with 3d apps properly) and only turn it on for testing purposes. Now it fails to remember my preference for leaving it off and comes on at every boot.

Has anyone bugged this yet?

---

### Post by Nullack on 2008-09-12
Ive confirmed the bug

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/256494](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/256494)

---

### Post by danbuter on 2008-09-12
This happened about a month ago, as well. I just wish Ubuntu would kill Compiz. It's the source of more problems than any other program in linux.

---

### Post by Nullack on 2008-09-12
Agreed, and it doesnt work with 3d apps. The whole video stack is broken and wont be fixed until a standard video memory manager is implemented. I turn it off unless testing compiz specifically.

---

### Post by Cenotaph on 2008-09-12
try using gconf-editor, somewhere there is an option to select the default window manager (dont know exactly where sorry, but i think its desktop -> window manager), just select metacity and you should be ok.

this happened to me too, it seems that appearance -> visual effects is buggy

---

### Post by dawynn on 2008-09-12
Just a thought.  It doesn't really help anyone that wants to have Compiz available for testing...

Try removing every package with "compiz" in the name.

Seriously, if you don't want compiz -- you could just take it off your system.  Ubuntu-desktop has it as a recommends, but it is not dependent on it (so you can keep the Ubuntu-desktop package on your system, without compiz packages).

I stripped it off because I wanted Gnome without all the heavy resource requirements.  Gnome works fine without it in both Hardy and Intrepid.

---

### Post by mziel on 2008-09-12
> **Cenotaph said:**
> try using gconf-editor, somewhere there is an option to select the default window manager (dont know exactly where sorry, but i think its desktop -> window manager), just select metacity and you should be ok.

After changing /desktop/gnome/applications/windows_manager/default from /usr/bin/compiz to /usr/bin/metacity and relogin it works with metacity as a default WM.

---

### Post by danbuter on 2008-09-12
I tried deleting compiz a month ago. I ended up having to reinstall, because everything got screwed up on my screen.

---

