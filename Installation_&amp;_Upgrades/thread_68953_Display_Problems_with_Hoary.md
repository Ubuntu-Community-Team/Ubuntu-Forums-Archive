---
title: "Display Problems with Hoary"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by dakpowers on 2005-09-24
I've searched for this in the wiki and the forums, and found nothing, so I apologize if this is a repost or easy solution :)

I'm trying to install Hoary on my desktop. After everything installs from the CD, and it comes to the screen for me to put in my name and password, the monitor goes blank, as if it's receiving a resolution it cannot display. I hear the sounds, and I can blindly put in my name and password and hear the startup sound, I just cannot see anything. I have successfully installed both Warty and Hoary on my laptop with no issues. I cannot figure out how to change the resolution or any sort of settings during installation that will change this. I would post specs of my computer, but I'm not sure what's relevant or not. My video card is super old, though, for this is an old laptop I'm trying to revive.

I really appreciate any help I can get with this. I love Ubuntu, and am hoping to rid of Windows soon.

---

### Post by aysiu on 2005-09-24
Well, [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) are the general instructions for fixing the screen resolution. After you log in, press control-alt-F1 and see if it changes to a console without a graphical user interface.

If that happens, log in as yourself and then type ```
sudo nano /etc/X11/xorg.conf
``` and adjust things appropriately (see previous link).

If not... I'm not sure what to do.

---

### Post by dakpowers on 2005-09-24
Well, that's the thing... After all the drivers and what not load, the screen goes blank as soon. I hear all the noises, but the monitor goes to standby mode.

Because of this, I can't really do anything.

---

### Post by aysiu on 2005-09-24
[QUOTE=dakpowers]Well, that's the thing... After all the drivers and what not load, the screen goes blank as soon. I hear all the noises, but the monitor goes to standby mode.

Because of this, I can't really do anything.[/QUOTE] But you said you could type but couldn't see what you're typing. Can you, after you hear the log-in music press control-alt-F1 and see if that takes you out of the graphical environment? Please give it a try.

---

### Post by dakpowers on 2005-09-24
[QUOTE=aysiu]But you said you could type but couldn't see what you're typing. Can you, after you hear the log-in music press control-alt-F1 and see if that takes you out of the graphical environment? Please give it a try.[/QUOTE]
 Alright, I've got to that screen. I can open the xorg.conf file, but what do I do now? Pardon my newbishness, I've never done this before.

---

