---
title: "Lost System Tray in 12.04LTS"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2012-04-12
Shut down my desktop computer last night, started up this afternoon and now my OS does not have a "System Tray".  That means I can not access the Operating System. I am doing this by using a live CD OS.

How do I repair, and where did it go?

This is on my desktop computer.  Laptop still using 10.10 and netbook using 11.10 until after the 26th of April when I will upgrade both to 12.04LTS (if I get this problem repaired).

---

### Post by Frogs Hair on 2012-04-12
After well over 100 updates for 12.04 yesterday I lost Ubuntu 3D after reboot. I logged into Ubuntu 2D and used ```
unity --reset
``` The command started the 3D panel over the 2D panel . I then logged out and into Ubuntu 3D and it was restored. In my case only the Ubuntu 3D DE was affected.

---

### Post by joshuapurcell on 2012-04-12
I'm not finding the unity command. I've just run into what seems like a similar situation after accepting a rather large update, but I'm able to log in and get a normal desktop by selection the 2D option at login. I see no unity executable either as my user or root.

---

### Post by joshuapurcell on 2012-04-12
Looks like logging in after selecting the 2D option from the login and then rebooting helped correct the issue for me. I didn't need to change any configuration.

---

### Post by uRock on 2012-04-12
The command listed in the above post was to be copied and pasted into a terminal, but if you have it working, then all is good.:p

---

### Post by jlh68 on 2012-04-13
How do I get to the Unity 2D screen.  I have no idea if I was in the 3D or 2D screens, before this problem.  I can not get a terminal to use the unity --reset command.  In essence I can not do much at all.  I can get Writer, Calc, & Impress on some programmed F-keys, but no ALT-F2 for the terminal.

Some more suggestions will be helpful.

---

### Post by jlh68 on 2012-04-13
Another item, I do not get the choice of which Ubuntu I get to log into, such as the safe mode or memtest.

---

### Post by otherethe on 2012-04-13
> **jlh68 said:**
> Another item, I do not get the choice of which Ubuntu I get to log into, such as the safe mode or memtest.
thats you're grub but as far as everything else goes do crlt alt f2 or any of the f keys f7 is your gui once you log, type in sudo apt-get remove unity then type in sudo apt-get install unity you can also install other gui shells as well such as gnome 3 sudo apt-get install gnome-core i think is the command now type in sudo stop lightdm, sudo start lightdm it should load up your gui fine you can then logout and select what desktop type you wanna use such as unity 2d, 3d, gnome or any other shell you installed this way it's simple fast and easy theres also no need to edit your conf I've had this same problem lots of times with 12.04 but now after a few updates my 12.04 is stable about as stable as 11.04 if I do say so my self

---

