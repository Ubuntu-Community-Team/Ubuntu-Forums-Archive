---
title: "Ubuntu 17.10 but no Gnome"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by leddith on 2017-10-19
I updated to 17.10 today but everything looks the same. It still looks like Unity. It says 17.10 is installed, I see the new software icon in the side bar, but no gnome. Please help.

---

### Post by wildmanne39 on 2017-10-19
Go to  top left of the screen above the launcher and click on activities does that make all the open windows small if so you should see a search function at the top center of the screen as well? can you see the day and time a the center of the top panel? if so then it is gnome. You just have to learn to use it which is very easy.

---

### Post by leddith on 2017-10-19
It's not Gnome. I'm sure of that. It is still Unity.Even the close, minimize and maximize are still on the left side, and it doesn't say "activities" anywhere.

---

### Post by dino99 on 2017-10-20
clean the system, using gtkorphan & bleachbit (as root), then reboot

---

### Post by leddith on 2017-10-20
How do I do that?

---

### Post by leddith on 2017-10-20
I rebooted and I got an internal error "/usr/lib/unity-settings-daemon/unity-settings-daemon" I don't know if that has anything to do with it

---

### Post by deadflowr on 2017-10-20
Most likely since it's an upgrade you still have unity.
(They weren't going to remove it)
So chances are you are simply logging into the unity session.

Do you have new sessions to try at login for (Ubuntu and Ubuntu on xorg)?
Those now are gnome.(Ubuntu is gnome on wayland)
unity should now be listed as unity

---

### Post by leddith on 2017-10-20
Just got another internal error "/usr/lib/i386-linux-gnu/hud/hud-service"

---

### Post by leddith on 2017-10-20
Is there any way to do a clean install without using a disc? Maybe via the terminal or something.

---

