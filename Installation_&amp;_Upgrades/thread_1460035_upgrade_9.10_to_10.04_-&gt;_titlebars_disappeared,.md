---
title: "upgrade 9.10 to 10.04 -&gt; titlebars disappeared, compiz problem?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by AMTQ on 2010-04-22
Hi all

I tried to update from 9.10 to 10.04beta2. It didn't work out very well, all titlebars (upper frame with the three buttons minimize/maximize/close) of all windows are missing. What is more, all compiz-features do not work anymore, which led me to the conclusion that the problem is with compiz.
I tried reinstalling compiz and metacity but none of this helped. Do you have an idea how to get my titlebars back? If not I'll wait for the final release and reinstall the whole system, but this is somewhat annoying...

I'm not shure wether you get what I mean, because I'm not a native speaker, I have therefore added a screenshot.

Thanks!
AMTQ

---

### Post by psycho5 on 2010-04-22
Hey man, I had the same problem, you can fix it by going to software center, and search for 'compiz fusion icon'. Install it, then run it, right click the icon on the upper right once you run it, and then go to "Select Window Decorater" and change it to GTK. See if that works, if not, then just select "Reload Window manager".

---

### Post by AMTQ on 2010-04-22
> **psycho5 said:**
> Hey man, I had the same problem, you can fix it by going to software center, and search for 'compiz fusion icon'. Install it, then run it, right click the icon on the upper right once you run it, and then go to "Select Window Decorater" and change it to GTK. See if that works, if not, then just select "Reload Window manager".

Hi! Thanks, this worked almost:
Compiz-features such as multiple desktops etc. work again, but there is still no titlebar. Also, it shows only the KDE4 Window Decorator.
If I switch the window manager to Metacity it all looks nice and there are even titlebars, but I'd prefer to use compiz...

any more ideas?

---

### Post by AMTQ on 2010-04-22
hm ok, I reinstalled the compiz window-manager, now it appears also in the list. It is now almost well, but after each reboot I have to manually reload compiz for the titlebars to appear.

---

