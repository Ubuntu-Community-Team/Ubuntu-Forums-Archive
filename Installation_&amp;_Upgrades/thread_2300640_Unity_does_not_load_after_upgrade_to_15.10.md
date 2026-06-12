---
title: "Unity does not load after upgrade to 15.10"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2015-10-27
Hello everyone :-)

I just upgraded to 15.10 on my laptop (ASUS F554L).
The upgrade was "eventless" and smooth.

When I rebooted, I got my login screen and enter password.
From then on, what I can see is my desktop background image, my mouse pointer (which is responsive) and nothing else.

No other GUI component is loading.

Suggestions?

Thanks !

---

### Post by grahammechanical on 2015-10-27
Are you running on a proprietary video driver? Did you revert to the open source video driver before upgrading? There are two ways to try a solution.

a) At the boot menu select Advance Options for Ubuntu, Then select recovery mode. At the recovery menu select Resume. If that gets you to a working desktop go to Software & Updates>Additional Drivers tab and experiment with video drivers.

b) At the desktop without Unity right click the wallpaper and select Change Desktop Background. That will load System Settings at the Appearance page and from there we can get to the System Settings window and then the Software & Updates>Additonal drivers.

You will notice that right clicking the wallpaper also gives us the option to open a terminal. That can be useful when it comes to restarting Compiz and Unity. Which might or might or might not work in this situation.

For Compiz

```
dconf reset -f /org/compiz/
```

and for Unity

```
setsid unity
```

Regards.

---

### Post by Ifaistos on 2015-10-27
I tried step b).

Turns out it was using proprietary drivers.  I never asked for that.  (Maybe it was done during installation?)
I toggled that off.
Rebooted.

I am getting the same result.

Tried restarting Compiz and Unity.

Compiz command runs and nothing happens.
Unity command runs and get stuck at :
compiz (core) - Info: Starting plugin: switcher


btw.. How do I do step a) ?
How do I get access to the boot menu?

---

### Post by Ifaistos on 2015-10-28
I found this post :

[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

and followed the instructions.

It seems that for some reason the Unity Plugin was not "enabled".

When I "enabled" it there were a log of key conflicts which I had to go through...and had to reboot from the terminal.

After reboot though the unity plugin was back on!

I will leave this thread open for a little bit more, just in case I come across any related problems.

---

