---
title: "Change Shutdown/Restart countdown timer?"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-14
When you go to shutdown/restart now a popup appears with "are you sure? it will shutdown in 60 seconds" and it counts down, and I can click cancel or shutdown.

There should be an option to change the countdown timer. I would like to change it to 5 seconds. That way if I do realize I made a mistake I can change it. But since I rarely do make the mistake of choosing wrong option, I would prefer to let it shutdown faster without needing to click shutdown again. Or an option to get rid of the popup.

---

### Post by tgpraveen on 2009-03-14
> **andrewabc said:**
> When you go to shutdown/restart now a popup appears with "are you sure? it will shutdown in 60 seconds" and it counts down, and I can click cancel or shutdown.

There should be an option to change the countdown timer. I would like to change it to 5 seconds. That way if I do realize I made a mistake I can change it. But since I rarely do make the mistake of choosing wrong option, I would prefer to let it shutdown faster without needing to click shutdown again. Or an option to get rid of the popup.

completely agree with u . i too find this highly irritating.

---

### Post by xtoudi on 2009-03-14
Yes, I would like to have an option to change this counter too!

---

### Post by olskar on 2009-03-14
Indeed, or perhaps change it to 2 hours before going to sleep and watching a movie or something, would have been great.

Perhaps a new option in the shutdown menu?

Shut Down Timer

---

### Post by GSMX on 2009-03-14
I also agree, I rarely mistake when i want to shutdown, so a dialog box that waits a minute becomes *very* annoying. I do actually like the idea of some sort of timer (sudo shutdown -P 12:00), but it should be totally optional imho.

---

### Post by hyl4me on 2009-04-03
> **andrewabc said:**
> When you go to shutdown/restart now a popup appears with "are you sure? it will shutdown in 60 seconds" and it counts down, and I can click cancel or shutdown.

There should be an option to change the countdown timer. I would like to change it to 5 seconds. That way if I do realize I made a mistake I can change it. But since I rarely do make the mistake of choosing wrong option, I would prefer to let it shutdown faster without needing to click shutdown again. Or an option to get rid of the popup.

With the lastest update.  You can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

---

### Post by philinux on 2009-04-03
> **hyl4me said:**
> With the lastest update.  You can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

Excellent. Thats was so windows like. Really annoying.

---

### Post by andrewabc on 2009-04-03
> **hyl4me said:**
> With the lastest update.  You can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

THANK YOU!
I will hopefully remember that when I install Jaunty.

---

### Post by Basiic on 2009-04-03
After updating today I also noticed your programs you had open before you click on restart are saved, and re-opened when you boot back up from restart.

Is this a new feature?  I have not seen this yet on jaunty before today.

---

### Post by hyl4me on 2009-04-03
> **Basiic said:**
> After updating today I also noticed your programs you had open before you click on restart are saved, and re-opened when you boot back up from restart.

Is this a new feature?  I have not seen this yet on jaunty before today.

Actually the "feature" has been there at least since Hardy.  I don't know somehow you got it enable.  

If you want to enable/disable it (save session)
System > Preferences > Startup Application (or Session for 8.10 or earlier) > Options > Check/Uncheck "Automatically remember running applications when logging out"

P.S.: Before you disable this feature, you should restart with all windows closed for gnome to remember your "default" session.  Or else, a certain program before you disable save session will start automatically.

---

### Post by phenest on 2009-04-04
> **hyl4me said:**
> With the lastest update.  You can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

Great! But what if, like me, you have uninstalled gnome-panels. I use AWN instead. Is there another way to change that?

Also, I have debated this timer in another thread, as 60 seconds is too long. If you're going to invoke the dialogue and walk away, any thing could happen in 60 seconds. In an office environment, someone could click Cancel and use your account. 5 seconds is better, and still gives YOU time to cancel.

---

### Post by Mempho on 2009-04-04
Aha! Thanks hyl4me. I disabled "Remember automatically running apps" but Ubuntu kept reopening the same apps in spite of that. Now it makes sense, it remembers the last state, so you have to first teach it to remember a blank desktop, then disable "Remember automatically..."

---

### Post by rburkartjo on 2009-04-04
hyl, tks for the info

---

### Post by rburkartjo on 2009-04-04
hyl, i also see you can disable the lock screen option when switching users. i hated that option

---

### Post by Basiic on 2009-04-04
> **hyl4me said:**
> Actually the "feature" has been there at least since Hardy.  I don't know somehow you got it enable.  

If you want to enable/disable it (save session)
System > Preferences > Startup Application (or Session for 8.10 or earlier) > Options > Check/Uncheck "Automatically remember running applications when logging out"

P.S.: Before you disable this feature, you should restart with all windows closed for gnome to remember your "default" session.  Or else, a certain program before you disable save session will start automatically.

Yeah, before I read your post I disabled it. In which it remembered my session and would start up programs as startup, really annoying.

I deleted the saved session so those programs wont start up though, it was located under Home/.config/gnome-session/saved-session

---

### Post by olskar on 2009-04-04
> **hyl4me said:**
> with the lastest update.  You can right-click on the shutdown button at the corner > preferences > uncheck "show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

yay! :d

---

### Post by hyl4me on 2009-04-04
> **phenest said:**
> Great! But what if, like me, you have uninstalled gnome-panels. I use AWN instead. Is there another way to change that?

Also, I have debated this timer in another thread, as 60 seconds is too long. If you're going to invoke the dialogue and walk away, any thing could happen in 60 seconds. In an office environment, someone could click Cancel and use your account. 5 seconds is better, and still gives YOU time to cancel.

Another way to do this is

open GNOME configuration 
```
gconf-editor
```

apps > panel > applets > fast_user_switch_screen0 > prefs > Checked "suppress_logout_restart_shutdown"

---

### Post by phenest on 2009-04-05
> **hyl4me said:**
> Another way to do this is

open GNOME configuration 
```
gconf-editor
```

apps > panel > applets > fast_user_switch_screen0 > prefs > Checked "suppress_logout_restart_shutdown"

That won't work. I don't have gnome-panel installed therefore I cannot configure the applet because it doesn't exist.

---

### Post by powel212 on 2009-04-13
> With the lastest update. You can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown". Then, you won't see annoying dialog. 

Awesome! Thank you.

P

---

