---
title: "Login crash cycle, failsafe works"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by havarlan on 2008-01-24
Alright, I just ran through the install process on my desktop.  I go to login for the first time and it attempts to login, starts playing the login sound, screen blacks(though doesn't change res or anything like that) and then pops back to the login screen.  I couldn't find any error messages.  If i run failsafe gnome session, it will load fine.  

I installed the nvidia drivers, which work dandy.  I updated a bunch of things that it suggested I update, including compiz.  I am able, in failsafe gnome, to run my monitors at full res just fine.  However, all other login session options crash back to the login screen.  I tried removing the associated gnome files, however that did not change anything.

any help would be appreciated!  It is slightly amusing to me that my install experience with ubuntu, contrary to everyone else i know, is more difficult than the install for opensolaris(plus getting compiz fusion on that) !  :O

-edit

After being unable to get nvidia drivers to detect stuff, manually installed or installed through ubuntu's restricted drivers/apt-get repositories, i ran across the program [Envy]("http://albertomilone.com/nvidia_scripts1.html").

The drivers set up through envy worked like a charm!

---

### Post by mikejordan on 2008-01-25
Same problem here. Could it be related to recent updates?

---

### Post by CameO73 on 2008-01-25
I had the same problem. It *is* related to Compiz (probably in combination with nVidia driver 169.04). There are a couple of ways to deal with this:[LIST]
[*]Login to the safe Gnome session (change session in the login screen). Then start Synaptic and remove Compiz. Logout and login. Everything works (except for Compiz)
[*] -or- Install the latest nVidia drivers (169.09) -- just get it from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us). Compiz works with this driver, although I've already experienced my first Compiz crash since I updated yesterday (it will revert back to the default window manager).[/LIST]No idea what the exact cause for this is. I did notice a warning message during the driver update (about the GLX driver). Or maybe it has something to do with the hardware (I'm running on a Asus Geforce 8800GT).

---

