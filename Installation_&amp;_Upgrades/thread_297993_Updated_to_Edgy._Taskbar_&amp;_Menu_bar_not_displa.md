---
title: "Updated to Edgy. Taskbar &amp; Menu bar not displaying"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Eddy Dean on 2006-11-12
Hello everyone,

I have used Dapper Drake for a while, and thought it would be nice to update to edgy, in order to have more functionality and eye-candy ;). I updated Dapper the way I should, typing "gksu "update-manager -c -d"". A while later (actually, a long while later) the update was finished, and I was asked to reboot. I did this, logged on and then noticed that the taskbar at the bottom of the screen and the menu bar at top of the screen were missing. All applications I'm using now are totally full-screen (that's actually pretty nice, but I still want my menubar and taskbar back..).

Although I don't think it matters, I'll post my configuration below:

AMD Athlon XP 2800+
AsRock motherboard (don't know the exact type, if it's important I'll look it up)
nVidia MX 420 graphics card, I had drivers for this installed on Dapper, and noticed Edgy renewed the drivers. The splash screen at boot still shows.

I'm looking forward to your replies,
Arno

---

### Post by bulldog on 2006-11-12
You can try```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

Or a simple logout and login again can help too.

---

### Post by Eddy Dean on 2006-11-12
Thanks for your reply, but unfortunately it did not work. I already tried rebooting, but that did not help.

Is it possible to "downgrade" to Dapper without ruining all settings and programs installed?

Thanks again,
Eddy

---

### Post by bulldog on 2006-11-12
Don't think you can.

Is ```
sudo aptitude dist-upgrade
```doing any good?

Or maybe select another theme its possible you used an unsupported theme.

Otherwise I'm stuck.

---

### Post by Eddy Dean on 2006-11-12
Thanks a million for your help. After some googling (variation is the key, even with google), I found out that running the command "gnome-panel" did the trick. I executed that comment by right-clicking the desktop, clicking "new starter" and giving it the command I was looking for :P

Thanks for your help, I really appreciate it.

Greetz,
Eddy

---

