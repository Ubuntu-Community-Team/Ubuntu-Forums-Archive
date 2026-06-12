---
title: "Ubuntu 10.10 to 11.04 Unity Start error"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by fubuloubu on 2011-04-29
Just upgraded from 10.10 this morning. Unable to start Unity when I log in under normal Ubuntu operating mode (from the dropdown box in the login menu)

Able to boot into "Ubuntu Classic" with no problems. Was curious if anyone had any suggestions to try and get unity to work. I was sort of excited to try it out today.

thanks.

---

### Post by sikander3786 on 2011-04-29
What happens when you login to Unity? Fuzzy screen, blank screen or something else?

Which graphics card is there and any proprietary drivers are installed?

---

### Post by fubuloubu on 2011-04-29
> **sikander3786 said:**
> What happens when you login to Unity? Fuzzy screen, blank screen or something else?

Which graphics card is there and any proprietary drivers are installed?

missing top and bottom taskbars, no access to terminal. everything else looks like a normal experience of "Classic Mode" (i.e. my three startup programs start normally and look the same as they did in 10.10)

I have an XFX/ATI HD 5770 graphics card and I did have the proprietary drivers installed under 10.10

two things I noticed while upgrading is that some of my graphics card packages didnt update or install correctly.

the second is that I kept my old compiz settings files when it asked if I wanted to overwrite

What are the minimum requirements to run Unity?

---

### Post by sikander3786 on 2011-04-29
Your graphics card is capable of running Unity I belive. The compiz settings have to do something with your problems.

Install ccsm in the classic mode.

```
sudo apt-get install compizconfig-settings-manager
```

Drag the shortcut to desktop. Logout and select Unity or 'Ubuntu' session. Login, run ccsm from the desktop shortcut. Enable the 'Ubuntu Unity Plugin'. It might require a reboot.

Please let us know how that goes.

---

### Post by fubuloubu on 2011-04-29
> **sikander3786 said:**
> Your graphics card is capable of running Unity I belive. The compiz settings have to do something with your problems.

Install ccsm in the classic mode.

```
sudo apt-get install compizconfig-settings-manager
```

Drag the shortcut to desktop. Logout and select Unity or 'Ubuntu' session. Login, run ccsm from the desktop shortcut. Enable the 'Ubuntu Unity Plugin'. It might require a reboot.

Please let us know how that goes.

Been trying this. I am able to enable the Unity plugin, but it asks me to 'resolve conflicts with other plugins'

I have the option to Resolve or Ignore the conflicts

first conflict is 'Reveal Mode' in Unity vs. 'Flip Left' in 'Desktop Wall' plugin

three options on this are 'Set reveal anyways', 'Don't set reveal', and 'Disable Flip Left'

second conflict is 'key to put keyboard-focus on launcher' in Unity vs. 'show main menu' of 'Gnome compatability plugin'

similar three options 'set keyboard focus anyways', 'dont set keyboard focus', 'disable show main menu'

last conflict is 'key to execute a command' vs. 'run dialog' of 'Gnome compatibility plugin'

same three options 'Set command key', 'dont set command key', 'disable run dialog'

---

### Post by sikander3786 on 2011-04-29
Did you try 'Resolve conflicts'?

---

### Post by fubuloubu on 2011-04-29
> **sikander3786 said:**
> Did you try 'Resolve conflicts'?

Yep. Tried it checking all three cases. No changes. I tried disabling the 'Gnome compatability plugin' and I was able to Enable and Disable the Unity plugin without any conflicts.

However, this seemed not to be the issue since I was able to restart the computer and it still wouldnt launch into unity.

I'm beginning to think its a graphics card driver issue thats messing with the ability to start unity. When I log into normal Ubuntu, I notice the taskbar blip on for a second, then its gone again.

It seems like alot of people having these kinds of issues.

---

### Post by sikander3786 on 2011-04-29
Yes many people are having these issues but mostly those with an upgraded 10.10. If possible, consider doing a clean install.

Before that, you might want to try by removing the old compiz settings so it can revert to default Unity settings.

Open your home folder, press Ctrl + H to see the hidden files. There should be a folder name .compiz, rename it to something else and reboot your PC.

Let us know how that goes...

---

### Post by sikander3786 on 2011-04-29
Or try this command.

```
unity --reset
```

---

### Post by fubuloubu on 2011-04-29
> **sikander3786 said:**
> Or try this command.

```
unity --reset
```

got a procedural error from running the reset command:

```
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_Profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
```

---

### Post by fubuloubu on 2011-04-29
> **sikander3786 said:**
> Yes many people are having these issues but mostly those with an upgraded 10.10. If possible, consider doing a clean install.

Before that, you might want to try by removing the old compiz settings so it can revert to default Unity settings.

Open your home folder, press Ctrl + H to see the hidden files. There should be a folder name .compiz, rename it to something else and reboot your PC.

Let us know how that goes...


my folder was named '.compiz-1' instead... and no luck with either of those two commands

---

### Post by jjaremczuk on 2011-05-05
> **fubuloubu said:**
> my folder was named '.compiz-1' instead... and no luck with either of those two commands

try to use 

gconftool-2 --recursive-unset /apps/compiz

command

it will reset compiz to defaults

---

