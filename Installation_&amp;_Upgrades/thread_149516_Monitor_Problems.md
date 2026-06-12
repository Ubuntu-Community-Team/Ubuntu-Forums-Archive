---
title: "Monitor Problems"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by zugu on 2006-03-24
Hello, guys and girls.

Last night I made a historical move: I switched to Ubuntu. I installed the 5.04 version on an old PC (Athlon 750, 256 RAM, RIVA TNT2, 3 GB HD, no network, no net connection).

First I used the Live CD. Everything went smooth, until the graphical interface appeared. That moment, my monitor enterd in standby. I've had this problem in XP too - the 15" monitor can't handle screen resolutions greater than 1024x768@60Hz. So in XP, after I ran the first boot with the "Enable VGA" option, everithing worked smoothly.

I decided to "live-expert", as there was nothing to lose. I was prompted for a lot of opions, and finally, there was something about the monitor. I chose 800x600@24 bit@60Hz and I was then able to see the Ubuntu desktop.

Because I've liked what I've seen, I decided to install it on the 3 GB HDD. The default installation, of course. It ran with no problems, untill entering the graphical interface. Then, my monitor again entered standby, and I had no possibility to interact with the OS. I pushed my shutdown button.

And now I'm asking the Ubuntu community to help me with this problem.
What can I do? Are there any command line parameters on booting, that can help me solve this? Is there any line that added to the default GRUB booting sequence that could help?

Any help provided here will have a tremendous influence on my future Ubuntu career, so take it easy on a n00b like me :mrgreen:

---

### Post by aysiu on 2006-03-24
Try [this link](http://ubuntuforums.org/showpost.php?p=129379&postcount=21).

---

### Post by zugu on 2006-03-24
Thank you for the link. I see that the solutions provided there involve command line editing of some files.

How do I start Ubuntu without starting GNOME, so that I get the command line only?

---

### Post by aysiu on 2006-03-24
Well, you actually don't have to be in command-line mode. You can use the command-line from within the system.

In Ubuntu: Applications > System Tools > Terminal
In Kubuntu: KMenu > System > Konsole

*Or*, you can just press Control-Alt-F1 to get into command-line mode. When you're done changing the settings, press Control-Alt-F7

Either way, after reconfiguring for your monitor, press Control-Alt-Backspace for the changes to take effect.

Both ways, you do *not* need to reboot.

---

