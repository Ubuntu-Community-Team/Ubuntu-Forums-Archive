---
title: "strange installation of 12.10"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by tafnyc on 2012-10-24
[SIZE="2"][/SIZE] I upgraded from 12.04 and did get 12.10 installed; however the login alternative for Gnome or Ubuntu does not work; I have tried numerous things and it will only put on Gnome Classic with no effects. What is going on?! 12.04 worked perfectly; what can I do to correct this?

---

### Post by Pilot6 on 2012-10-24
It means that you either did not install video driver, or it does not support your videocard.

---

### Post by memristor on 2012-10-24
Are you using lightdm as your display manager? I am guessing you are only seeing Gnome Classic as a login option and there is not option for Gnome or Ubuntu Unity listed, correct?

I had similar issue on a previous upgrade. Uninstalling and then reinstalling lightdm fixed it for me. Give it a try.

---

### Post by tafnyc on 2012-10-24
> **memristor said:**
> Are you using lightdm as your display manager? I am guessing you are only seeing Gnome Classic as a login option and there is not option for Gnome or Ubuntu Unity listed, correct?

I had similar issue on a previous upgrade. Uninstalling and then reinstalling lightdm fixed it for me. Give it a try.

All options are there listed at Login, but not allowing me to go to any I choose; it goes into Gnome Classic, period.

---

### Post by Pilot6 on 2012-10-24
What is you video card? Did you install proprietary drivers?

---

### Post by funicorn on 2012-10-24
Actually it's not exactly as you've seen. The alternative session(s) can be selected and started. It's just there's something wrong with the login window so that somehow the alternative button doesn't take mouse click. You can try like this: first click on an effective session button, then move the active spot with up/down arrow to the target, press Enter and you are in.

Just note that the switching of focus using up/down arrow is not circular.

---

### Post by tafnyc on 2012-10-25
Tried what you suggested; did not work. The list is there; it does not move from Classic no effects.

---

### Post by memristor on 2012-10-25
Do you see .desktop files for your sessions in /usr/share/xsessions ?
for example ubuntu.desktop, gnome-shell.desktop etc.

My wild guess is that lightdm is unable to see the .desktop files and resorting to the default.

---

