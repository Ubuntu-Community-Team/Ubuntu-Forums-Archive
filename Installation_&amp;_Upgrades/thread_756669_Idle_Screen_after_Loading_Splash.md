---
title: "Idle Screen after Loading Splash"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by JoCoProductions on 2008-04-16
Hey guys just got a fresh install of Ubuntu here and everything was working great until I enabled my nVidia graphics driver and restarted. After that things seems ol, I selected my ubuntu partiotion to go into, and the splash and loading bar came up just fine. The problem is right when it finishes loading, when it should go to the GRUB login my screen goes idle (the LED on the monitor changes from green to orange) but the computer acts as if nothing is wrong. If I type in my username and password I can actually hear the login sounds, so it must be the graphics driver problem somewhere. also if I push the power button on my tower while the screen is idle the monitors LED goes green again and up pops the shutdown terminal fullscreen things happening.

Any fix to this?



And just for fun since it's my first post: :popcorn:

---

### Post by PmDematagoda on 2008-04-16
The fact that you hear the sound does not mean that the X-Server does not start since the GDM or any login screen for that matter requires a working X-Server(Except for the text one).

Now do this, when you reach the supposed login screen press Ctrl+Alt+F1 to move to a different tty, then do:-
```
sudo killall Xorg
```
and then do:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after that is done, start the X-Server with:-
```
sudo /etc/init.d/gdm start
```

See if that allows you to see something in the least:).

---

### Post by JoCoProductions on 2008-04-16
I think I broke it :X

After killing Xorg the terminal trips balls and goes black except for 1 or 2 lines of pixels at the top of the screen are random colors. I think this is becuase of the Gnome display manager but I have no clue.

When I push the power button on the case, it shuts down and I see terminal pop up again.

Any fixes?

---

### Post by JoCoProductions on 2008-04-16
SURELY somenone out there has had this problem? Is there any fix or way around it?

---

### Post by PmDematagoda on 2008-04-16
Ok, instead of killing Xorg that way, try doing:-
```
sudo /etc/init.d/gdm stop
```

> When I push the power button on the case, it shuts down and I see terminal pop up again.
What do you mean by saying that the terminal pops up again? Does the X-Server start at all or does it give an error?

---

### Post by JoCoProductions on 2008-05-02
Hey a follow up to this, I had to do a lot of things first in order to get back to this stage, but I am in ubuntu now with everything working fine except the restricted drivers. When I enable them it brings me back to an idle black screen right where the login should be. The only way to get back to Ubuntu is to boot into recovery mode edit the xorg.conf and add under "Device" "Drivers vesa".

Someone on the #ubuntu irc channel suggested it was a problem with my xorg and I would have to do some surgery with that in order to get it up and running. Any thoughts?

---

### Post by ecrivain5 on 2008-05-02
Hi,
I have the self same problem...well almost. When I start up ubuntu goes through loading until it gets to the end of the loading bar. From there I get a blank screen. It keeps doing this until I have run windows then it boots up as normal. (that may just be coincidence) Anyway if there is a fix to the problem I would be grateful. 
PS I also have the nvidia plug-in running.

---

