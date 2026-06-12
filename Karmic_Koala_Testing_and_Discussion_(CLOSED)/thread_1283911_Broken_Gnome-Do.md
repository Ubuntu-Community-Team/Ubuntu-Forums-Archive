---
title: "Broken Gnome-Do"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-10-06
Latest upgrade seems to have broken Gnome-Do, I'm getting this

> (Do:2072): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
when I run it from a terminal.

---

### Post by wilee-nilee on 2009-10-06
I have yet to get nothing but a black box with the ppa gnome-do, it will find stuff and open the preference window.

---

### Post by Peter09 on 2009-10-06
Have you set the view to Docky in the preferences?

---

### Post by wilee-nilee on 2009-10-06
> **Peter09 said:**
> Have you set the view to Docky in the preferences?

You know I am not sure I am on  the Xp partition right now but I will check it out. I have been using Gnome Do since it came out and I believe I have it set up as usual but that may be the problem, thanks for the suggestion. I am finding some graphic problems in general with Karmic but I have a barely workable ati radeon graphic card.

Edit: So I booted over to Karmic and Gnome Do is set up correctly I think it is the card, there are no loadable drivers it is 8 years old. Fortunately I have a new net-book I just use this oldy for daily use, and testing.

---

### Post by Sand &amp; Mercury on 2009-10-06
> **wilee-nilee said:**
> I have yet to get nothing but a black box with the ppa gnome-do, it will find stuff and open the preference window.
Running the Gnome-Do in the Karmic repositories, I got the same problem at first. However, I used xkill to stop it, and it hasn't done that again since. Sometimes it will appear black for a fraction of a second when I summon it, but that's the extent of it.

---

### Post by abhinavmodi on 2009-10-06
I am getting the following with the latest karmic upgrade :

```
abmodi@abhinav-lnx:~$ gnome-do

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 
```

Gnome-do version : 0.8.2

---

### Post by abhinavmodi on 2009-10-06
> **abhinavmodi said:**
> I am getting the following with the latest karmic upgrade :

```
abmodi@abhinav-lnx:~$ gnome-do

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 
```

Gnome-do version : 0.8.2

I removed ~/.local/share/gnome-do directory and gnome-do started working. HOWEVER, as expected all previous data/plugin settings/info seems to have been lost.

---

