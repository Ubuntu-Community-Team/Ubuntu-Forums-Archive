---
title: "fast-user-switch-applet"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by spillz on 2010-04-14
Just dist-upgraded to the beta of Lucid. (Overall quite nice, though many apps don't fit in with the new theme and what's with the inch thick dark grey bar at the top of every window!?)

My problem:

```

~$ sudo apt-get install fast-user-switch-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  fast-user-switch-applet: Depends: gdm but it is not going to be installed
E: Broken packages

```

```

~$ sudo apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.

```

Is this known breakage that should be fixed soon? I've already had to put up with 6 months of Karmic without a fast-user-switch, not sure I can go another 6.

---

### Post by spillz on 2010-04-15
bug report here: [https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/563922](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/563922)

---

### Post by mcduck on 2010-04-15
Both Karmic and Lucid use indicator-applet for this purpose. As far as I know the old fast-user-switch applet doesn't have any features that wouldn't be there in the new applet...

The error about GDM is probably related to Karmic & Lucid using a new version of GDM, while that applet would most likely require the old one instead...

And, by the way, what "inch-thick grey bar"? Never seen such thing... Care to post a screenshot?

---

### Post by spillz on 2010-04-15
> **mcduck said:**
> Both Karmic and Lucid use indicator-applet for this purpose. As far as I know the old fast-user-switch applet doesn't have any features that wouldn't be there in the new applet...

how do i disable the need to enter a password when I switch between the active sessions of two users?

> 
And, by the way, what "inch-thick grey bar"? Never seen such thing... Care to post a screenshot?


top panel + title + menu bar
[http://images.sageek.co.za/images/lucidFF.png](http://images.sageek.co.za/images/lucidFF.png)
(taken from [http://blog.g33q.co.za/2010/04/07/review-ubuntu-1004-lucid-lynx-beta-1-with-screenshots/](http://blog.g33q.co.za/2010/04/07/review-ubuntu-1004-lucid-lynx-beta-1-with-screenshots/))

---

### Post by bapoumba on 2010-04-15
Moved to Lucid.

---

### Post by mcduck on 2010-04-15
> **spillz said:**
> how do i disable the need to enter a password when I switch between the active sessions of two users?



top panel + title + menu bar
[http://images.sageek.co.za/images/lucidFF.png](http://images.sageek.co.za/images/lucidFF.png)
(taken from [http://blog.g33q.co.za/2010/04/07/review-ubuntu-1004-lucid-lynx-beta-1-with-screenshots/](http://blog.g33q.co.za/2010/04/07/review-ubuntu-1004-lucid-lynx-beta-1-with-screenshots/))

Most likely tahts simply related to the gnome-power-manager locking the screen. Try with gconf-editor, the relevant keys are under apps/gnome-power-manager/lock/.

What comes to the combination of window decoration & toolbars, if you don't like it then just use some other theme. There are couple of alternatives installed by default, tens of themes more available in repositories and hundreds (or thousands) more in gnome-look.org... I guess it's simply impossible to create a theme that everybody would like. :)

---

### Post by spillz on 2010-04-15
> **mcduck said:**
> Most likely tahts simply related to the gnome-power-manager locking the screen. Try with gconf-editor, the relevant keys are under apps/gnome-power-manager/lock/.


Thanks. I'll try this when I can. Note that if I look at the gnome docs: [http://library.gnome.org/users/gnome-power-manager/2.29/gnome-power-manager.html#advanced-preferences-locking](http://library.gnome.org/users/gnome-power-manager/2.29/gnome-power-manager.html#advanced-preferences-locking)

I see:

    1. /apps/gnome-power-manager/lock/use_screensaver_settings
    2. /apps/gnome-power-manager/lock/blank_screen
    3. /apps/gnome-power-manager/lock/suspend
    4. /apps/gnome-power-manager/lock/hibernate 

are you suggesting that if I disable these (specifically 1 & 2) then the user switch should not ask for a password once that user has been logged in? If so, awesome :)

btw, Is there a way to customize what's on the Indicator Status Session menu? (gconf again?)

re theme, just one man's opinion of course, but first impressions matter, so I just gave mine. The problem with using anything other than the default is the effort of making sure everything plays nicely with whatever I choose (icons, custom widgets etc). Anyway, leave this for another thread...

---

### Post by spillz on 2010-04-15
> **mcduck said:**
> Most likely tahts simply related to the gnome-power-manager locking the screen. Try with gconf-editor, the relevant keys are under apps/gnome-power-manager/lock/.


Tried this and it didn't work. I'm assuming that I really do need fast user switcher

---

### Post by kurros on 2010-04-15
I don't think you have to mess with gconf-editor, just untick "Lock screen when screensaver is active" in the Screensaver preferences app for each of the users.

---

### Post by spillz on 2010-04-15
> **kurros said:**
> I don't think you have to mess with gconf-editor, just untick "Lock screen when screensaver is active" in the Screensaver preferences app for each of the users.

thanks, but tried that and it doesn't work. Can you confirm that you can switch between users without passwords?

---

### Post by mcduck on 2010-04-16
> **spillz said:**
> Tried this and it didn't work. I'm assuming that I really do need fast user switcher

Sorry, my mistake, that's how it's supposed to work, but I forgot that there's a bug in the indicator-applet that causes it to not respect those settings like it should.

There's already one "user-switcher" applet installed by default, have you tried that one?

Also, I actually never bother switching through any applets, I just press Ctrl-Alt-F7, Ctrl-Alt-F8 and so on to switch between the logged-in users...

---

### Post by spillz on 2010-04-16
> **mcduck said:**
> Sorry, my mistake, that's how it's supposed to work, but I forgot that there's a bug in the indicator-applet that causes it to not respect those settings like it should.

There's already one "user-switcher" applet installed by default, have you tried that one?

Also, I actually never bother switching through any applets, I just press Ctrl-Alt-F7, Ctrl-Alt-F8 and so on to switch between the logged-in users...

the user switcher doesn't even show a list of users, just the option to switch and requires passwords every time

otoh, CTRL+ALT+F7 and CTRL+ALT+F8 work :) Asks for the password first time, which I can live with, but hopefully password freedom doesn't time out.  

Can those keys be customized? Is this feature documented somewhere?

thanks for your help!

---

