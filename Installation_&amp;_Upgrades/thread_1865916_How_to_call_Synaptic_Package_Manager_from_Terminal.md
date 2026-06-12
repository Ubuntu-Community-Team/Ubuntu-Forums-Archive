---
title: "How to call Synaptic Package Manager from Terminal?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by ProntoAnthony on 2011-10-20
I recently upgraded both laptop and desktop to 11.10.

I just woke up my laptop from being in a suspended state.

Somehow my laptop is in Unity, but the launcher will not appear.

The top bar indicates "File Edit View Go Bookmark and Help" and the pulldown menus work. Help brings up Ubuntu Help. Nautilus comes up from the Go menu.

Control-Alt-T brings up a Terminal window.

From there I can sudo reboot, but after GRUB menu the laptop just goes right back to the same screen. 

Suddenly I remember what I did just before I left the laptop. I was in Synaptic Package Manager trying which indicator-... app to uninstall so that annoying and useless white envelope would be removed. I removed a few that I shouldn't have. How do I call up Synaptic Package Manager from Terminal so I can compare the list of packages beginning with "indicator-" on the laptop with the list of the desktop and reapply those packages I removed?

---

### Post by JRV on 2011-10-20
```
sudo synaptic
```

---

### Post by coffeecat on 2011-10-20
```
gksu synaptic
```

Also, File -> History will tell you exactly which packages you uninstalled.

---

### Post by ProntoAnthony on 2011-10-20
I added the 2 packages I had removed and then reboot but I'm still unable to improve the situation.

---

### Post by ProntoAnthony on 2011-10-20
I'm trying to fix all packages in case it will help with knuckle-headed users.

Any suggestions would be appreciated.

---

### Post by ajgreeny on 2011-10-20
It is indicator-messages in Lucid;  no idea what it may be in 11.10, but try that.

---

### Post by ProntoAnthony on 2011-10-20
Thanks for trying to help, but my problem is that I can't boot into a usable state. 

Must I resort to a complete re-install? If so, how do I do that from here?

---

### Post by ajgreeny on 2011-10-20
You seem to have got into quite a state, but don't panic!

Have you tried unity 2D from the login screen, or do you autologin?  If you are setup to autologin at the moment andf if you can not use the log-off from the menu use Alt-Gr+Print screen+K to kill the session then try unity 2D from the session menu (the small cog-wheel icon in the username/password box).

If that does not work you could try ```
sudo apt-get install  gnome-session-fallback
``` package from the repos, and then login to the gnome-classic desktop, which will give you a session much like the old classic desktop layout.  One big difference is the need for **Alt+Rt Click** to change or edit panels and applets on them.

---

### Post by ProntoAnthony on 2011-10-20
Great suggestion!

Yes, I was in quite a pickle.  Alt-Gr+Print screen+K to kill the session worked well. However I had the same problem with Unity 2D, so I installed Gnome fallback and now at least I have a usable system. 


How do I get Unity back up and running on my laptop? Is there a way to do some sort of quick install or must I do a fresh install from the CD I just made on my desktop?

---

### Post by ProntoAnthony on 2011-10-20
I just went into software center , looked up unity, and saw that the add-on "Indicator for application menus" wasn't checked. Added that the Unity. Logged out on Gnome Recovery and into Unity only to come up against the same problem.

---

### Post by Frogs Hair on 2011-10-20
Have you tried to reset Unity ? ```
unity --reset
```

---

### Post by ProntoAnthony on 2011-10-20
Yes, tried it while in Gnome and compiz (core) warned that there was no exact match for ConfigureNotify and I should probably file a bug. Probably happened because Unity wasn't running at the time. S I went back to Unity 2D and tried the reset there. Got the same ConfigureNotify error.

Unity appears to be really busted. Gnome Classic is my best friend right now. At least it's working.

---

### Post by ProntoAnthony on 2011-10-21
Success!

I removed and reinstalled Unity. Now Unity 2D is working on my laptop.

---

