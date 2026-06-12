---
title: "gnome session flashback no panels after nvidia install ubuntu server 16.04"
date: 2019-10-07
forum: Installation &amp; Upgrades
---

### Post by rabicula on 2019-10-07
Hello everyone,

I have been hitting a wall for days now and I couldn't find any workaround digging my way through all the forum.
After installing ubuntu-desktop on top of an ubuntu-server 16.04, gnome-session-flashback was working fine and all the panels were displayed until I installed the nvidia driver. After nvidia proprietary driver install there's no way to log on the gnome flashback metacity session with top and bottom panels on, the desktop is here, there's a way to right click and get a terminal window at least on metacity mode ( no way with compiz but I don't really care ) but no panel is being displayed. I'm desperate, thank you for your help.

-H.

---

### Post by mörgæs on 2019-10-08
Maybe a good beginning is to take a look at the graphics processor. Please run ```
lshw -C video
``` and post the results in CODE tags.

---

### Post by Claus7 on 2019-10-08
Hello,

what happens if you issue the command: gnome-panel? Most probably is a graphics issue, yet, if you accidentally have erased the top and bottom panel with this command they should reappear.

Regards!

---

