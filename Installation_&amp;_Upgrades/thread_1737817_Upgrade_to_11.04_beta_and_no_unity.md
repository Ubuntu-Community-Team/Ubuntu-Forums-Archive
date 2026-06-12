---
title: "Upgrade to 11.04 beta and no unity?"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by mw007 on 2011-04-23
Hi all, I upgraded to 11.04 beta today and unity didn't appear to be installed. So, I ran sudo apt-get install unity and everything looked good.

The problem now is that I can't select unity in the login manager (I use kdm). Is there a way to make unity selectable? I'd like to try it out.

Thanks!

---

### Post by mikewhatever on 2011-04-23
Are there options for Ubuntu in kdm? The Ubuntu option in 11.04 should load the Unity interface, but I am not sure if installing only unity is enough. You might need the whole of ubuntu-desktop.

---

### Post by mw007 on 2011-04-23
Thanks for the quick reply! Yes, I have the following options in my login window.

[LIST]
[*]Default
[*]KDE Plasma Workspace
[*]Ubuntu
[*]Ubuntu Classic
[*]Ubuntu GNOME Shell Desktop
[*]Failsafe
[/LIST]
The Ubuntu and Ubuntu Classic both give me the error: "Cannot load session".

The Ubuntu GNOME Shell Desktop works, sort of. I installed it today as well hoping to get it working, and it doesn't look anything like what was on the livecd test disc. I just assumed the packaging wasn't 100% ready yet.

---

### Post by ishaangt on 2011-09-09
U need to install the Ubuntu desktop for those sessions to work
```
$sudo apt-get install ubuntu-desktop
```

---

