---
title: "Problems with Desktop Interface on a single user after Update"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by Artless01 on 2012-12-16
Hi,
after updating form 11.10 and 12.04, i have problems with my desktop interface on my main useraccount. I added a new user account and everything works fine.

As you can see in the attached pictures, i can open the data, but the background is black and i can not see the font. [ATTACH]228759[/ATTACH]

I tried to kill and restart compiz, but I justed switched back to the faulty screen. 
Using Gnome 2 leads instead of Unity leads to the same problem, but works fine in the new account.
 
Any ideas.

Thank you

---

### Post by ohnonot on 2012-12-17
it looks to me like your original account can't find the gtk theme anymore. 
i don't use unity, but you can try this:
open a terminal, type ```
gedit ~/.gtkrc-2.0 ~/.config/gtk-3.0/settings.ini
```
and in the files opening up, look for ```
gtk-theme-name="xxxx"
```
xxxx should be pointing to an existing folder in /usr/share/themes.
the folder should have subfolders called gtk-2.0 and gtk-3.0.
(if you need more help with that please ask)
log out and in -> any better?

---

### Post by Artless01 on 2012-12-17
The Console output leads to the following error 


(gedit:6361): Gtk-WARNING **: Theme parsing error: a11y.css:408:23: 'px' is not a valid color name

(gedit:6361): Gtk-WARNING **: Theme parsing error: a11y.css:465:23: 'px' is not a valid color name

Gedit opens up with two blank notes.

Could this broken stylesheet lead to an parsing error?

However, right now I managed to install the lubuntu desktop which works fine, so I can work with this account again, as it is not urgent I will mark this as solved and try to fix it over Xmas holidays.

Thank you for helping.


Edit: removing the config 
rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf -rf 

and resting unity

unity --reset 

solved the problem in the end

---

