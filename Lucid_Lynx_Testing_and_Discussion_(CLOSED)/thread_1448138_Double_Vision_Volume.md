---
title: "Double Vision Volume"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2010-04-06
About a month ago, after testing various sound options and determining everything to be in working order, I set my sound preference to "No Sounds", muted the alert volume, and called it all good. 

Just recently, I decided I should test to ensure everything is still functional with the sound prefs and have discovered some interesting behavior. Now, if I select the only other available sound theme, "Ubuntu", a second volume icon appears in my panel.

I use the indicator-sound component of indicator-applet to access Sound Preferences. This spawns gnome-volume-control. When I select "Ubuntu" from the dropdown, gnome-volume-control-applet is started and the icon is displayed in the notification-area-applet. See screenie:

[IMG]http://img338.imageshack.us/img338/4416/doublevolume.png[/IMG]

Is this happening for anyone else?

---

### Post by tekstr1der on 2010-04-06
Well, I created a new user profile. I observe the correct expected behavior there, indicating something screwy with my user settings.

I completely purged and reinstalled pulseaudio, canberra, and gnome-media. The problem is still present for my user. Any ideas?

---

### Post by Gourgi on 2010-04-07
check your "startup applications" if there is sound/volume application loading twice. if so then disable gnome-volume-control-applet from there.

---

### Post by tekstr1der on 2010-04-10
> **tekstr1der said:**
> I use the indicator-sound component of indicator-applet to access Sound Preferences. This spawns gnome-volume-control. When I select "Ubuntu" from the dropdown, gnome-volume-control-applet is started and the icon is displayed in the notification-area-applet. See screenie:

[IMG]http://img338.imageshack.us/img338/4416/doublevolume.png[/IMG]

Is this happening for anyone else?

Does anyone have any idea how I could prevent gnome-volume-control from spawning gnome-volume-control-applet when I select the sound theme rather than simply playing the login sound via libcanberra-gtk-play which is the default behavior?

---

### Post by psyke83 on 2010-04-10
> **tekstr1der said:**
> Well, I created a new user profile. I observe the correct expected behavior there, indicating something screwy with my user settings.

I completely purged and reinstalled pulseaudio, canberra, and gnome-media. The problem is still present for my user. Any ideas?

Purging/reinstalling packages won't fix corrupted user settings. You need to delete the user settings located somewhere within ~/.local/ or similar.

---

### Post by tekstr1der on 2010-04-10
Thanks. I should have added that while the packages were uninstalled, I also removed any user settings related to pulse as well as compared diffs between known working profile for ~/.gconf/desktop/gnome/sound/%gconf.xml. I just can't seem to find any user setting difference that could be responsible.

In addition, it confuses me how this seems to be a programmatic problem as the behavior of the drop-down list changed and is at fault here. Perhaps I should examine the source code for insight as to the logic which could cause this behavior change. Very strange.

---

### Post by tekstr1der on 2010-04-12
Just to be sure it was not a gconf issue, I deleted .gconf and .gconfd directories. Logging in with defaults, I am still experiencing this issue.

Also, after taking a look at gvc-sound-theme-chooser.c, all that's happening in code is essentially reading and writing gconf values as well as reading from the sound theme directories. I had hoped to glean more from the source.

With gconf and pulse user settings ruled out, I can't think of any other user setting that would have any bearing, yet it clearly must be something under ~/ causing the issue as all works as expected when logged in under a new user profile.

Any ideas?

---

### Post by linuxman94 on 2010-04-19
Remove the startup application 'Gnome volume control' and then kill the gnome-volume-control-applet process by using:

```
killall gnome-volume-control-applet
```

---

