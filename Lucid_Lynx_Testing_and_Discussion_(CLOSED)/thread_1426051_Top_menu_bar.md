---
title: "Top menu bar"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-03-09
Okies ... I was helping s.o. out when they had managed to delete the top menu bar, and I saw what ??!! how did you do that ? --- Well, the instructions work. 

Now, having clicked the delete part, how does one get the top menu bar back?

I've scrabbled around and got a 'Top Menu Bar' back, with the notification, etc by right clicking on the bottom left and from there "Add To Panel" and even gotten it up to the top of the screen - But it is a 'mess' looks a lot like Win98 on the bottom bar....

 "There must be an easier way" ;-)

The O.P. has tried rebooting etc, but still no joy. I've tried restarting Gnome / 'X' etc ... but the settings seem to have gone ...

1st time that I've messed up my system helping some one,

((HELP!!))    :-)

Regards,

Phill.

---

### Post by caryb on 2010-03-09
No great loss KDE has survived for years without it:lolflag:


Cary

---

### Post by QwUo173Hy on 2010-03-09
A picture says a thousand words - show us what you mean!

---

### Post by phillw on 2010-03-09
> **jarlath said:**
> A picture says a thousand words - show us what you mean!

Right Click, New Panel.

Then click on the top panel and right click remove panel .... ::SIMPLES::

Looks really nice, and I'd like to keep it for when I'm coding etc. But... I'd lime to be able to turn it back on !!!!!
:D
 
Phill.

---

### Post by dcstar on 2010-03-09
> **phillw said:**
> Okies ... I was helping s.o. out when they had managed to delete the top menu bar, and I saw what ??!! how did you do that ? --- Well, the instructions work. 

Now, having clicked the delete part, how does one get the top menu bar back?

I've scrabbled around and got a 'Top Menu Bar' back, with the notification, etc by right clicking on the bottom left and from there "Add To Panel" and even gotten it up to the top of the screen - But it is a 'mess' looks a lot like Win98 on the bottom bar....

 "There must be an easier way" ;-)

The O.P. has tried rebooting etc, but still no joy. I've tried restarting Gnome / 'X' etc ... but the settings seem to have gone ...


Create a new user and the default top panel should be created, then you may be able to copy that definition file from the new profile to the existing user profile.

---

### Post by phillw on 2010-03-09
> **dcstar said:**
> Create a new user and the default top panel should be created, then you may be able to copy that definition file from the new profile to the existing user profile.

I have an additional user, (backups, backups .... - lol)  if the config is saved there, could you tell me where ?

Thanks,

Phill.

---

### Post by sigurnjak on 2010-03-09
No need to create new user . Put this in terminal

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and reboot. 

 Your desktop will be back to defaults  including panels .

When rebooting Gnome will create default configuration , i DID IT FEW TIMES .  .

---

### Post by jpeddicord on 2010-03-09
> **sigurnjak said:**
> No need to create new user . Put this in terminal

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and reboot. 

 Your desktop will be back to defaults  including panels .

When rebooting Gnome will create default configuration , i DID IT FEW TIMES .  .

That's pretty dangerous, you'd lose all of your settings for everything (applications included). I highly recommend you don't to that.

---

### Post by sisco311 on 2010-03-09
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```
should restore the default panels.

---

### Post by QwUo173Hy on 2010-03-09
> **phillw said:**
> Right Click, New Panel.

Then click on the top panel and right click remove panel .... ::SIMPLES::

Looks really nice, and I'd like to keep it for when I'm coding etc. But... I'd lime to be able to turn it back on !!!!!
:D
 
Phill.

Then I'd be in the same situation as you :)

---

### Post by phillw on 2010-03-10
> **sisco311 said:**
> ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```should restore the default panels.

And you, are a star of the first magnitude !!!!

Wow, what ever else can I say but thanks.

:popcorn:

You ever in the North West of UK, I owe you a beer / glass of wine :D

Thanks,

Phill.

---

### Post by phillw on 2010-03-10
> **jarlath said:**
> Then I'd be in the same situation as you :)

Well, now you can go play ;-)

Phill.

---

### Post by sisco311 on 2010-03-10
> **phillw said:**
> And you, are a star of the first magnitude !!!!

Wow, what ever else can I say but thanks.

:popcorn:



You're welcome!

> **phillw said:**
> 
You ever in the North West of UK, I owe you a beer / glass of wine :D

Thanks,

Phill.

mmmmm... beer...
[IMG]http://scrapetv.com/News/News%20Pages/Science/Images/drooling-homer-simpson.jpg[/IMG]

---

### Post by sigurnjak on 2010-03-10
> **jpeddicord said:**
> That's pretty dangerous, you'd lose all of your settings for everything (applications included). I highly recommend you don't to that.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing)

[http://ubuntuforums.org/showthread.php?t=419162](http://ubuntuforums.org/showthread.php?t=419162)


I never said do it as root .  And all your apps and data will stay , only your customized settings will be reset  to default as it was when you first installed it .

---

### Post by jpeddicord on 2010-03-10
> **sigurnjak said:**
> [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing)

[http://ubuntuforums.org/showthread.php?t=419162](http://ubuntuforums.org/showthread.php?t=419162)


I never said do it as root .  And all your apps and data will stay , only your customized settings will be reset  to default as it was when you first installed it .

First off you left out a key part: this must be done in a failsafe xterm session (from GDM), otherwise the gconf database will be left in an unstable state.

Second: phillw was trying to restore the panel layout, not start from scratch which is overkill. sisco311's post was the right command to do this.

---

