---
title: "Problem after update / can not login"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by JarekMk on 2007-04-05
Hi evryone,

I'm from Poland :)

Yesturday i updated my Ubuntu 7.04, and after reboot can't login.

I write my login password and then beck to login window... 

How i can fix this problem ?

I've Gnome and beryl update to date 

br

---

### Post by shavenlunatic on 2007-04-05
same here.. everytime the kernel or X updates, i have problems...

I will be working on it tonight so any help on this thread will be usefull, and if I manage to get logged in, I will post how I managed :)

---

### Post by mertulas on 2007-04-05
Same here... I can only start the computer in a different session where Beryl is unloaded (default gnome session), I then can access the beryl settings manager but as soon as I start Beryl the system just goes back to X windows login screen... So annoying, cant use beryl anymore.

---

### Post by mertulas on 2007-04-05
Same here... I can only start the computer in a different session where Beryl is unloaded (default gnome session), I then can access the beryl settings manager but as soon as I start Beryl the system just goes back to X windows login screen... So annoying, cant use beryl anymore. :confused:  (sorry for double post, couldn't find how to delete the first one)

---

### Post by justsee on 2007-04-05
Just ran the latest updates and I have the very same issue. Log in fine, but flashes the nvidia logo and then returns me to login screen. This happens regardless of whether I change sessions (usually running xgl / beryl).

Does anyone know which updates have triggered this? I'll login to console and see what I can find but this is a major pain!

---

### Post by Hellion DarkLord on 2007-04-05
I have the same problem.  only I can't enter the user and password.  I would not update the xserver update and see if that works.  It did for me, but you may be suffering from another unrelated problem.

---

### Post by shavenlunatic on 2007-04-05
if you have envy, i think you can boot to a prompt and type envy and re-install all you video stuff, apparantley that can help..

i manually installed my nvidia drivers and stuff so I'm a bit screwed on that front

---

### Post by mertulas on 2007-04-05
Hmm you might try logging as root (i know it is not very safe but just to solve this problem) and then remove beryl and reinstall it again, that might work. I uninstalled and reinstalled beryl now (from automatix bleeder) and will see the result after i reboot now. Hope it works.

---

### Post by shavenlunatic on 2007-04-05
Strangely, before I updated, I set gnome as my desktop manager, not beryl, so I doubt this is causing the problem (unless beryl still tries to "load" but just doesn't actually manage the desktop,  is this is the case.. it could be right)

---

### Post by mertulas on 2007-04-05
Well reinstalling Beryl did not solve the problem but I noticed something else, whenever the screensaver activates, the x system restarts as well so it should be something related with 3d graphic drivers not the beryl (as beryl uses your 3d card, just like my screensaver) The cause of this problem should be my nvidia drivers not the beryl...

Now i will retry installing my nvidia drivers (dont forget to back up xorg.conf file before, if you want to try as well) and let you know guys.

---

### Post by sblanzio on 2007-04-05
same problem here, today I can't login gnome at all. Both normal and emergency session. I just can load kde, but if i try to launch beryl-manager it flashes to black screen and after a while it loads nvidia splash screen and comes back to login screen.

Looking for a workaround.

EDIT:
reinstalling nvidia drivers with envy seems to have solved this problem by now. However i saw there was an error i've never seen during envy installation... it said something like "Error /.../..../..../libglx. so' is not a symbolic link"... don't know what it is but now it seems to work. 
Oh, and I have edgy.

---

### Post by hanzomon4 on 2007-04-05
This is a driver issue reinstalling the nvidia drivers fixes the problem. Perhaps this should be sticked somewhere, I just found this thread by chance....

---

### Post by shavenlunatic on 2007-04-05
right, reinstalling nvidia drivers works, for those of you who don't know how and/or don't have envy (i can't seem to work with envy), just do the following:

boot into failsafe terminal (or alt into a terminal) and run

```

sudo apt-get install --reinstall nvidia-glx

```

hit CTRL-ALT-BACKSPACE or reboot

log in, everything running fine.. solved :)




edit: Beryl isn't running though, will re-install that but at least ya can do it from the GUI now :)

---

### Post by angkor on 2007-04-05
> **shavenlunatic said:**
> 
edit: Beryl isn't running though:)

I rolled back to the previous version of the xserver-xorg package in synaptic to get beryl back to life. I'll post a better solution when I find one.

---

### Post by hanzomon4 on 2007-04-05
If you installed the drivers from nvidia kill X, re-run the installer script, and restart X.

```
sudo /etc/init.d/gdm stop
```
```
sudo sh ./NVIDIA-Linux-x86-1.0-9xxxxxx.pkg1.run
```
```
sudo /etc/init.d/gdm restart
```

---

### Post by alessandrop65 on 2007-04-07
sudo apt-get install --reinstall nvidia-glx


That did the trick for me, and I had no problems with Beryl. Thanks Shavenlunatic!

Cheers,
Alex-

---

