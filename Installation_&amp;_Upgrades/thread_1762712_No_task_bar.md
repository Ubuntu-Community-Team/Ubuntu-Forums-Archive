---
title: "No task bar"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by thenovelist on 2011-05-19
Just updated this afternoon to v 11 from 10.10.  Took a few hours, it seemed to go well, but I am always skeptical that it will fail somewhere.  I rebooted and I was right, no task bar.  I do have desktop icons though.  But that is not much good when you can't access your applications.  Anyone know how I can get back my task bar and access to the applications?

---

### Post by thenovelist on 2011-05-21
I thought I had better make this back to the top again as its now buried deep into all the other threads.   I have no way of access any application to setup the taskbar and access to applications.  Anyone have any idea on how to resolve this PLEASE as I can't get to work without my office programs etc:-(

---

### Post by thenovelist on 2011-05-21
I have found this command
[LEFT][FONT=Verdana]Once the Terminal window opens, enter the following command at the prompt:[/FONT][/LEFT]
 [LEFT]***[COLOR=#ff0000][FONT=Verdana]gconftool-2 – -shutdown[/FONT][/COLOR]***[/LEFT]
 [LEFT][FONT=Verdana](**Note:** T*here should be no spaces between the two dashes before shutdown.*)[/FONT][/LEFT]
 [LEFT]**EDIT – Reader  nickrud has suggested a better method instead of shutting down gconfd.  Instead use the following command (thanks nickrud!)**[/LEFT]
 [LEFT][COLOR=#ff0000]***gconftool – -recursive-unset  /apps/panel ***[/COLOR][/LEFT]
 [LEFT][FONT=Verdana](**Remember:** T*here should be no spaces between the two dashes before shutdown.*)[/FONT][/LEFT]
 [LEFT][COLOR=#000000][FONT=Verdana]Then enter the next command:[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#ff0000]***[FONT=Verdana]rm -rf ~/.gconf/apps/panel[/FONT]***[/COLOR][/LEFT]
 [LEFT][FONT=Verdana]And enter one more command:[/FONT][/LEFT]
 [LEFT][COLOR=#ff0000]***[FONT=Verdana]pkill gnome-panel[/FONT]***[/COLOR][/LEFT]
 [COLOR=#FF0000][FONT=Verdana][COLOR=#000000]That's it! 
[/COLOR][/FONT][/COLOR]
[COLOR=#FF0000][FONT=Verdana][COLOR=#000000]ANd guess what !!![/COLOR][/FONT][/COLOR]

[COLOR=#FF0000][FONT=Verdana][COLOR=#000000][/COLOR][/FONT][/COLOR]
[COLOR=#ff0000][FONT=Verdana][COLOR=#000000]NOTHING!!
[/COLOR][/FONT][/COLOR]

---

### Post by ivanovnegro on 2011-05-21
Dont understand what happened exactly?
Maybe try this:

```
unity --reset
```

That will set your environment to the default settings.
And yes, to be capable to do this, just use ALT + F2 and run this command in terminal if you cannot access it from your GUI.

---

### Post by thenovelist on 2011-05-21
OKAy, I believe my terminology is incorrect and it seems I am talking to myself on this forum.  I believe the correct terminology is panels not taskbar!

---

### Post by thenovelist on 2011-05-21
Well I did it and for those who are struggling like me here is the answer if you can access your terminal - type in or copy this 

> nohup gnome-panel

Works like a dream

---

