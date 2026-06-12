---
title: "more desktops"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2013-04-27
I see from other threads that the new Ubuntu 13.04 is a bit dodgy. Things keep crashing, Astrill VPN won't work. Hope it gets better soon! I can't seem to enable more desktops. I only have four. I want more! In 12.04 I used Unity to increase the number. But I can't find anything in System Settings to get more desktops.

---

### Post by Frogs Hair on 2013-04-27
13.04 beta and final have been very solid here . System settings doesn't have an option to install different desktop environments so maybe you could explain what are referring to.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by deadflowr on 2013-04-27
I think the OP means workspaces.
Precise doesn't have that ability by default, You had to have installed something like myunity or ubuntu tweak.

Since neither of those is yet available for raring, you need something else.

It just so happens there is, at least one simple program you can install.
unity-tweak-tool.
```
sudo apt-get install unity-tweak-tool
```

Of course there are other programs like ccsm, or dconf editor, but those are crazy dangerous if you don't know what you're doing.

---

### Post by Pedroski55 on 2013-04-27
Yeah, that's what I meant 'workspaces' I like to have a lot of them! I downloaded the tweaks and now have more 'workspaces'

Another problem: I want compiz style wobbly windows! I love them! Can I get that in 13.04???

---

### Post by dandroid13 on 2013-04-27
Install CompizConfig Settings Manager and Compiz plugins. It will disable snapping windows.

---

### Post by Pedroski55 on 2013-04-27
Buhu! Wobbly windows is gone!! I got CompizConfig Settings Manager, but it does not have 'wobbly windows' any more!! Buhu!

---

### Post by dandroid13 on 2013-04-28
Install Compiz plugins extra.

---

### Post by Pedroski55 on 2013-04-28
There is no such package in Software Installer

---

### Post by dandroid13 on 2013-04-28
Here, should be this one```
compiz-plugins-extra
```

---

### Post by MAFoElffen on 2013-04-28
In 13.04... Okay, I'm a Gnome3 buf so, patience... In Unity, system settings > appearance > behavior tab > enabled desktops... In Gnome, right-click on the lower right of the taskbar > preferences > Workspace Selection Manager > enable workspaces... then how many workspaces is a slider type widget. I usually go with 5-6 workspaces.

---

### Post by fantab on 2013-04-28
> **Pedroski55 said:**
> There is no such package in Software Installer

Perhaps you need to enable "Independent" and "Partner" Repositories. You can do it from Software Center-> EDIT.

"Synaptic Package Manager" has more advanced features than Software Center. Install it you won't regret.

---

### Post by Frogs Hair on 2013-04-28
The compiz plugins package in 13.04 is now :```
 compiz-plugins
```

---

### Post by Pedroski55 on 2013-04-28
Thanks very much! 

sudo apt-get install compiz-plugins-extra

did the trick, I have my beloved wobbly windows again!!

---

