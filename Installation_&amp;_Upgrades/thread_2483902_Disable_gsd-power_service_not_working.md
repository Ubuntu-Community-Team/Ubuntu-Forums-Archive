---
title: "Disable gsd-power service not working"
date: 2023-02-12
forum: Installation &amp; Upgrades
---

### Post by vendax on 2023-02-12
Some instructions i found on the web to **disable a gsettings plugin** no longer work.

```
sudo gsettings set org.gnome.settings-daemon.plugins.power.active false
usage: [redacted]

sudo gsettings set org.gnome.settings-daemon.plugins.power active false
No such key "active"

sudo gsettings set org.gnome.settings-daemon.plugins.power enabled false
No such key "enabled"
```
How does this work? I tried with dconf-editor but i simply see no option like 'active' or 'enabled' i see some whitelist variable.

I want to disable gsd-power because it is segfaulting and restarting every x seconds. Seems like this unresolved bug:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=786425](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=786425)

This is inside QEMU however, i do not know if the bug exists on real hardware. Custom kernel might have something to do with it. For now, i just want to disable it so it doesn't try to spawn every x seconds and clog my dmesg with segfaults.

---

### Post by MAFoElffen on 2023-02-13
For Ubuntu 20.04 and 22.04, for my laptop...
```

mafoelffen@Mikes-ThinkPad-T520:~$ gsettings list-recursively org.gnome.settings-daemon.plugins.power
org.gnome.settings-daemon.plugins.power ambient-enabled true
org.gnome.settings-daemon.plugins.power idle-brightness 30
org.gnome.settings-daemon.plugins.power idle-dim false
org.gnome.settings-daemon.plugins.power lid-close-ac-action 'suspend'
org.gnome.settings-daemon.plugins.power lid-close-battery-action 'suspend'
org.gnome.settings-daemon.plugins.power lid-close-suspend-with-external-monitor false
org.gnome.settings-daemon.plugins.power power-button-action 'interactive'
org.gnome.settings-daemon.plugins.power power-saver-profile-on-low-battery true
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 3600
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 1200
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'suspend'

```
The unnamed fix you "found on the web":
```

gsettings set org.gnome.settings-daemon.plugins.power active false

```
was for Ubuntu 11.10: [https://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management](https://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management)

And has since been deprecated (You should have read further down the page...):
> 
For anyone that still trying to use this solution, this thing already deprecated as it's further description This key is deprecated and ignored. Set org.gnome.desktop.session idle-delay to 0 if you do not want to active the screensaver., try using the org.gnome.desktop.session idle-delay then. Just saying, hope can help. &#8211; 
ksugiarto
Apr 30, 2015 at 8:45

What I found was to use these together:
```

gsettings set org.gnome.desktop.session idle-delay 0
gsettings set org.gnome.settings-daemon.plugins.power idle-dim false

```

---

### Post by vendax on 2023-02-13
Right, but as stated in his quote, those are for his problem with screensaver, not for disabling a gsettings plugin. I don't have a problem with the screensaver or screen dimming - it works well. Besides the url you linked to i searched for other pages as well, but none presented me with a modern equivalent of the deprecated-and-removed feature that page talks about.

I tried to browse the gsettings manually with dconf-editor, a GUI browser like RegEdit for Windows i guess. But i cannot find any option to disable a plugin - there is no 'enabled' or 'active' item - just various others. I went as far as to remove the configuration file **/etc/xdg/autostart/org.gnome.SettingsDaemon.Power.desktop** but if i do that gnome desktop crashes. Lucky this is inside qemu so i can experiment at will.

But there has to be a way to turn that power plugin off - it causes continuous respawns and segfaults. Interesting how much issues a pristine debootstrap installation of the latest LTS release would present. And because it is running inside qemu virtual machine, hardware cannot be blamed.

So my question remains: what equivalent command should i use on modern Ubuntu versions to achieve the desired effect: disable the 'power' plugin which is causing me issues.

---

### Post by MAFoElffen on 2023-02-13
Try
```

gsettings set com.canonical.unity.settings-daemon.plugins.power active false

```

---

### Post by vendax on 2023-02-13
Unfortunately that key does not seem to exist:
```
$ gsettings set com.canonical.unity.settings-daemon.plugins.power active false
No such schema ?com.canonical.unity.settings-daemon.plugins.power?
```
With the command **gsettings list-recursively | grep canonical** i can see only items like com.canonical.Unity.Lenses and com.canonical.unity.desktop.

I tried editing the **/etc/xdg/autostart/org.gnome.SettingsDaemon.Power.desktop** file, but to no avail. Commenting out the restart stuff there will still keep it spawning over and over. Replacing **/usr/libexec/gsd-power** with **/bin/true** also does not solve the issue - the desktop keeps hanging.

So as i understand they deprecated the option to disable a specific plugin, without offering something comparable to be used instead, and now if one plugin is causing problems it is virtually impossible to turn it off without causing the entire gnome desktop to crash or stall or become unusable. I keep wondering why this is happening in the first place inside a QEMU vm and after a pristine debootstrap install with some scripts that do apt install and place some configfiles. I think the custom Linux kernel configuration might be causing this issue. I might try with a stock kernel. I would have preferred to just disable the power plugin and use that for now, but that option seem to have been 'deprecated'.

---

### Post by MAFoElffen on 2023-02-13
That is strange. Here is what I get on my Laptop on Ubuntu 22.04.1 LTS...
```

mafoelffen@Mikes-ThinkPad-T520:~$ gsettings list-recursively com.canonical.unity.settings-daemon.plugins.power
[COLOR=#ff0000]com.canonical.unity.settings-daemon.plugins.power active true
[/COLOR]com.canonical.unity.settings-daemon.plugins.power ambient-enabled true
com.canonical.unity.settings-daemon.plugins.power button-hibernate 'hibernate'
com.canonical.unity.settings-daemon.plugins.power button-power 'interactive'
com.canonical.unity.settings-daemon.plugins.power button-sleep 'suspend'
com.canonical.unity.settings-daemon.plugins.power button-suspend 'suspend'
com.canonical.unity.settings-daemon.plugins.power critical-battery-action 'suspend'
com.canonical.unity.settings-daemon.plugins.power idle-brightness 30
com.canonical.unity.settings-daemon.plugins.power idle-dim true
com.canonical.unity.settings-daemon.plugins.power lid-close-ac-action 'suspend'
com.canonical.unity.settings-daemon.plugins.power lid-close-battery-action 'suspend'
com.canonical.unity.settings-daemon.plugins.power lid-close-suspend-with-external-monitor false
com.canonical.unity.settings-daemon.plugins.power notify-perhaps-recall true
com.canonical.unity.settings-daemon.plugins.power percentage-action 2
com.canonical.unity.settings-daemon.plugins.power percentage-critical 3
com.canonical.unity.settings-daemon.plugins.power percentage-low 10
com.canonical.unity.settings-daemon.plugins.power power-button-action 'suspend'
com.canonical.unity.settings-daemon.plugins.power priority 0
com.canonical.unity.settings-daemon.plugins.power sleep-inactive-ac-timeout 1200
com.canonical.unity.settings-daemon.plugins.power sleep-inactive-ac-type 'suspend'
com.canonical.unity.settings-daemon.plugins.power sleep-inactive-battery-timeout 1200
com.canonical.unity.settings-daemon.plugins.power sleep-inactive-battery-type 'suspend'
com.canonical.unity.settings-daemon.plugins.power time-action 120
com.canonical.unity.settings-daemon.plugins.power time-critical 300
com.canonical.unity.settings-daemon.plugins.power time-low 1200
com.canonical.unity.settings-daemon.plugins.power use-time-for-policy true

```

---

