---
title: "How Do I Remove Invest Applet?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by mgaskell on 2007-01-20
Hello All,

I'm running Edgy 6.1.

I loaded the invest applet into the upper panel. It doesn't work. When I click on it, nothing happens. When I right click on it to remove it, nothing happens. I would rather not delete the entire applet package and reinstall.

Any ideas?

Thanks,
Mike

---

### Post by gavintlgold on 2007-01-20
Did you try restarting the panel (or did you already restart the computer?)

sudo killall gnome-panel

I don't know much, but maybe..?

---

### Post by mgaskell on 2007-01-21
I don't know much either but I think your suggestion will kill everything in the panel for this session only. I want to get invest off the panel permanently without affecting the other aplets.

What do you think?

---

### Post by gavintlgold on 2007-01-21
Did you click to the right of the button? It seems the invest applet only works that way. If you click directly ON the button, nothing happens, but to the side, it gives you an option to remove.

I tried it too, and it doesn't do anything unless you right-click to the right of the button and do the preferences, or right-click and do remove.

Is this your problem?

---

### Post by mozkill on 2007-12-07
my problem with this applet is that no click of any kind, in any location will get any sort of activity from the applet.  it is dead in the water and i cant remove it because the Panel itself doesn't have a master "panel editor".   i also cant find the .config directory where the panel itself might actually be sitting.

---

### Post by valmalio on 2008-02-04
You dont have to click ON the applet!
Just click outside the icon on the right side :)

Edit: Now I mention that this solution told 2 posts before by gavintlgold. I am sorry....

---

### Post by zasf on 2008-05-02
Can you guys try invest-applet from svn? Invest-applet UI has been renovated, the problem you mention should be fixed.

---

