---
title: "Lubuntu + touchpad ; disable tap-to-click??"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sefianix on 2010-04-18
I have a laptop with a touchpad.  I want to switch to lubuntu since it's an old laptop.  But I can't use the HAL fdi hack to disable tap-to-click.  I've tried many things but nothing has worked.  

I've tried reading  [Configuring Input Devices on Ubuntu Wiki]("https://wiki.ubuntu.com/X/Config/Input") but that made no sense to me.  However, I gave it a try and wrote a udev rule, named it touchpad.rules, and placed it in /etc/udev/rules.d
```

ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.MaxTapTime}="0"
LABEL="touchpad_end"

```
This didn't work.  But, hey, I gave it a shot.

There are several users on this laptop so I'm looking for a global solution similar to the old fdi hack.  Any ideas?

Thanks

---

### Post by kerry_s on 2010-04-18
install "gpointing-device-settings".

---

### Post by Sefianix on 2010-04-18
Thanks for informing me of gpointing-device-settings.  I installed it.  ran it.  settings don't hold after reboot.  I also executed with sudo; settings still don't hold.  Maybe settings not holding is a bug??

---

### Post by kerry_s on 2010-04-18
> **Sefianix said:**
> Thanks for informing me of gpointing-device-settings.  I installed it.  ran it.  settings don't hold after reboot.  I also executed with sudo; settings still don't hold.  Maybe settings not holding is a bug??

forgot about that, theres a command you need to put in the startup to load the settings at start.
you'll have to read the man page, i can't remember the command.
```
man gpointing-device-settings
or
gpointing-device-settings --help
```

once you find the command add it to $HOME/.config/lxsession/Lubuntu/autostart
you might have to create the file if it doesn't exist.

---

### Post by Sefianix on 2010-04-18
> **kerry_s said:**
> forgot about that, theres a command you need to put in the startup to load the settings at start.
you'll have to read the man page, i can't remember the command.
```
man gpointing-device-settings
or
gpointing-device-settings --help
```

once you find the command add it to $HOME/.config/lxsession/Lubuntu/autostart
you might have to create the file if it doesn't exist.

Thanks kerry_s.  I read the man page but there isn't much there--mostly just a url to the [project website]("http://live.gnome.org/GPointingDeviceSettings").  But I didn't find the command you mention.  Also, oddly enough, nothing is output when using the --help option.  So I tried putting just the gpointing-device-settings command into the autostart file but it just brings up the control panel at startup; it doesn't commit any changes unless I select something and click 'ok'.   

While trying to figure this out, I kept looking around and found stuff on xinput and synclient.  xinput didn't work for me.  I tried ```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Time" "0"
``` (and variations) but it didn't work for me.  I later tried ```
synclient MaxTapTime=0
``` and that did work!  I'd like to put it somewhere at startup that's safe and won't hose my system.   I think this would be the global solution I'm looking for--something that'll work for all accounts on the system.  Can you recommend a place to put that command that's safe??

Thanks for all the help

---

### Post by kerry_s on 2010-04-18
press> **alt+f2**
type> **gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart**

add your " **@synclient MaxTapTime=0** "

thats the global for lubuntu session.

---

### Post by Sefianix on 2010-04-19
:) Thanks!  That works!  I appreciate all the help and I hope this helps others too.  Lubuntu is fast; I like it.

---

