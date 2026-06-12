---
title: "No keyboard/mouse at login screen"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Muffe on 2008-10-10
I use Intrepid Ibex, and updated my system a few hours ago. After a reboot, there was no keyboard and mouse at the login screen. A bit unpractical not to be able to enter the username and password.

Am I the only one, or does more have this experience? I am surfing with links in a terminal, so browsing the web to find out is not a joy.

I have tried to boot with an old, but working, kernel, and the problem is still there.

Best regards.

---

### Post by wgrant on 2008-10-10
> **Muffe said:**
> I use Intrepid Ibex, and updated my system a few hours ago. After a reboot, there was no keyboard and mouse at the login screen. A bit unpractical not to be able to enter the username and password.

Am I the only one, or does more have this experience? I am surfing with links in a terminal, so browsing the web to find out is not a joy.

I have tried to boot with an old, but working, kernel, and the problem is still there.

Best regards.

You probably let xserver-xorg-input-evdev be removed - there was a window of a few hours where apt would have tried to. Make sure that xserver-xorg-input-all is installed.

---

### Post by Muffe on 2008-10-11
Thanks for the tip. Works like a charm, but I also had to install gnome-panel to log in...

Lesson learned: do not remove everything Synaptics tells you to remove, especially not when you are running a pre-release distro...

---

### Post by fritz276 on 2008-10-11
Thanks, that saved my day. I had the same problem and hat to reinstall ...-synaptics to also get my touchpad working again.

---

### Post by ubulette on 2008-10-11
> **wgrant said:**
> You probably let xserver-xorg-input-evdev be removed - there was a window of a few hours where apt would have tried to. Make sure that xserver-xorg-input-all is installed.

I've been experiencing that for several weeks now.
See [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/265029](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/265029)

After a reboot, either gdm or the whole desktop (when using autologin) are stuck without keyboard and mouse. The mouse is stuck in the center of the screen, and the keyboard is almost dead (leds are fine, and i can switch to the consoles).

The workaround is to go to a console and kill Xorg, then it's all fine. 

xserver-xorg-input-evdev is installed.
Could it be a race condition?

---

### Post by wgrant on 2008-10-11
> **ubulette said:**
> I've been experiencing that for several weeks now.
See [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/265029](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/265029)

After a reboot, either gdm or the whole desktop (when using autologin) are stuck without keyboard and mouse. The mouse is stuck in the center of the screen, and the keyboard is almost dead (leds are fine, and i can switch to the consoles).

The workaround is to go to a console and kill Xorg, then it's all fine. 

xserver-xorg-input-evdev is installed.
Could it be a race condition?

X asks hal for input devices now, so it could well be a race with hal.

---

### Post by jonger on 2008-10-11
Thanks wgrant. i don't have gnome as an option now though on GDM.

for newbies here is what i did to fix the keyboard/mouse problem

at the login screen hit CTRL+ALT+F2

then login and type 

```
sudo apt-get install xserver-xorg-inut-all
```

then restart. Thanks again guys

---

### Post by Amael on 2008-10-27
Hello, 

I have the same problem but without using autologin. No keyboard & no mouse at gdm login screen. But a "ps-ef | grep gdm" showed my that I have two instances of GDM running ! So I tried to restart gdm using "/etc/init.d/gdm restart" and this worked, I now have keyboard and mouse support.
But I have to do this manipulation at each reboot, so it's a little bit painful.
Btw, I have the xserver-xorg-inut-all package installed.
Haven't found a solution for now, but I have put the same comment on the bugreport on launchpad.

---

### Post by Amael on 2008-10-28
Found the solution in another thread here : during my update the /etc/rc*.d/S20gdm file hasn't been moved to /etc/rc*.d/S30gdm. I did it manually and now everything works.
More infos : [http://ubuntuforums.org/showthread.php?t=901300](http://ubuntuforums.org/showthread.php?t=901300)

---

