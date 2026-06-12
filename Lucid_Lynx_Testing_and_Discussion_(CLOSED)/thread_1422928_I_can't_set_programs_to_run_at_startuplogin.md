---
title: "I can't set programs to run at startup/login"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by setherd on 2010-03-06
Does anyone else have this problem:
under system->preferences-> startup applications
add a program to run at startup.

as an example I have the "drapes" program (it changes your desktop wallpaper automatically) set to run.

but it won't](*,)

the update manger won't run either, so I constantly have to run (sudo apt-get update && apt-get upgrade)
the only programs listed to run that actually are (as far as I can tell) are the avant window navigator, bluetooth manager, and dropbox.

I can't understand why dropbox would run but update-manager won't.

I filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/518740](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/518740)

can anyone else try this and see if I am all alone here? For me this is a major bug that should be fixed before final.

---

### Post by cariboo on 2010-03-06
Drapes is actually a panel applet, it hasn't run properly for me since Intrepid. I normally use wallpaper-tray, which is in the repositories.

---

### Post by setherd on 2010-03-06
> **cariboo907 said:**
> Drapes is actually a panel applet, it hasn't run properly for me since Intrepid. I normally use wallpaper-tray, which is in the repositories.
I had the same experience. Unfortunately Wallpaper-tray isn't in the repositories anymore (some dependency error, I asked about it)
While Drapes hadn't worked for me beofre, it works fine now (I still prefer wallpaper-tray) You might want to give it a shot.

I used drapes as an example, Thinkpad buttons also don't work for me (command "sudo tpb-d")

---

### Post by pturegano on 2010-03-17
I found it [at]("http://archive.ubuntu.com karmic/universe wallpaper-tray 0.5.5-0ubuntu3"):

  [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe wallpaper-tray 0.5.5-0ubuntu3

Pere

---

### Post by setherd on 2010-03-18
it may work but supposedly there are package dependencies that can't be met in Lucid.


and I still can;t get 99% of things including update manager to run at login :(

---

### Post by cariboo on 2010-03-18
How are you trying to get programs to run on startup?

---

### Post by setherd on 2010-03-18
> **cariboo907 said:**
> How are you trying to get programs to run on startup?

system -> preferences -> startup applications.

even the default ones don't run.

but SOME do, like dropbox, AWN, but update manger won't.

---

