---
title: "Nautilus crashes on each login to Gnome after upgrade from 6.06 to 6.10"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by damgaard on 2007-03-19
When a user logs in to Gnome on my system, she gets this error message: ``The Application "nautilus" has quit unexpectedly. You can inform the developers of what happened to help them fix it. Or you can restart the application right now. [Restart app.] [close] [inform developers]''. 

I have another user on the same system. This user can log in to KDE without any errors. 

All this started happening after an upgrade from 6.06 to 6.10.

What can be the cause? 
How do I fix it? 

I have tried deleting all the nautilus session files from the user's .nautilus folder. This had no effect.

---

### Post by adam.tropics on 2007-03-19
It might be worth having a look at your session preferences. I had a problem with that upgrade. 

System-->Preferences-->Sessions...Current Session

Check gnome-settings-daemon is running. If not put it in startup programs. Also check that nautilus is starting before it. In Current session, it wants an order of 40. You can edit it there, apply, and restart the session.(logout)

---

