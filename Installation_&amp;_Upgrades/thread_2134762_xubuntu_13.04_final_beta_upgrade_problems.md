---
title: "xubuntu 13.04 final beta upgrade problems"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by fintry on 2013-04-12
I have just upgraded my laptop to the 13.04 final beta release and have a couple of problems I don’t know how to fix.
 

[LIST=1]
[*]Right click menu on the desktop does not work at all.
[*]None of the file manager programs can find both of my hard discs
[*]Not urgent, but the background wallpaper doesn’t work either.
[/LIST]
 
Any guidance for a newbie much appreciated.
Thanks.

---

### Post by Toz on 2013-04-12
Both #1 and #3 sound like xfdesktop isn't running. Try starting it up again by Alt-F2 and running:
```
xfdesktop
```

As for #2, what do you mean be "none of the file manager programs"? Xubuntu only comes with one by default, Thunar. Have you installed others? BTW, if you've installed Nautilus, it may be taking over management of the desktop, which may explain why #1 and #3 may not be working.

---

### Post by fintry on 2013-04-12
Nice one Toz.  xfdesktop got it going again.
As for the file managers, I also installed Krusader.
Will that be causing a problem ?

---

### Post by Toz on 2013-04-12
> **fintry said:**
> Nice one Toz.  xfdesktop got it going again.
As for the file managers, I also installed Krusader.
Will that be causing a problem ?

I'm not that familiar with Krusader, but I don't think it would. It might just be that your cached sessions got corrupted (it happens). If running xfdesktop solved your problem, then good. If you find that on every login, xfdesktop isn't working and needs to be restarted, then you may need to delete your sessions cache (~/.cache/sessions).

---

### Post by fintry on 2013-04-13
I do have to run xfdesktop everytime I boot the laptop, and that is after your tip of clearing the sessions cache.
I still have Windoze 7 installed on this laptop, will that be causing any interference ?
I installed Ubuntu through the Wubi program.

---

### Post by Toz on 2013-04-13
> I do have to run xfdesktop everytime I boot the laptop
Before you logon, press Ctrl+Alt+F1 to go to the text login console and login there (text mode).
Once logged in, enter the following commands:
```
cd $HOME/.cache
rm -rf sessions
logout
```

Then, go back to the graphical login - press Ctrl+Alt+F7 - and log in again.

Does xfdesktop start automatically now?

---

