---
title: "MSTTCOREFONTS not working in firefox"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by praveenmarkandu on 2009-04-19
i was using intrepid until a day ago. i did an upgrade to jaunty via update-manager -d
everything went fine. 

when when i launched firefox i realized the fonts on the pages i visit frequently had changed.
**on the irc channel people say firefox chooses its own fonts. but why isnt it using the microsoft fonts?**
allow pages to choose thier own fonts, instead of my selections above is checked. thats what it should be and didnt change when i did the upgrade.

i still have MSTTCOREFONTS installed and i have reinstalled it for safe measure.

---

### Post by Reiger on 2009-04-19
There are settings, at least in Opera, you can use to override website CSS/Fonts/JavaScript/Cookies/Etc. A reason why you would want to do that is when your browser is themed to such an extent that the fonts `must match'.

Anyways, digging through the settings you can probably find something like "Allow websites to determine fonts" or something similar. Checked yes there is: Edit -> Preferences, from the panel that appears select Content -> Advanced (next to default Font setting) -> Allow websites to determined fonts (or whatever it was called).

---

### Post by praveenmarkandu on 2009-04-19
as i have said before in my first post, i have checked "allow pages to choose thier own fonts, instead of my selections above"

---

### Post by philinux on 2009-04-19
Might be worth trying a new FF profile.

---

### Post by praveenmarkandu on 2009-04-19
> **philinux said:**
> Might be worth trying a new FF profile.

tried that. also uninstalled an reinstalled firefox.

---

### Post by smbm on 2009-04-19
Have you tried creating another user and trying Firefox as the new user? Something may have gone awry in one of your font config files.

---

### Post by praveenmarkandu on 2009-04-19
> **smbm said:**
> Have you tried creating another user and trying Firefox as the new user? Something may have gone awry in one of your font config files.

just tried that. didnt work :(

---

### Post by praveenmarkandu on 2009-04-20
i've even tried to do 
```
sudo fc-cache -rv
```
and
```
sudo defoma-reconfigure -f
```
but no luck

---

### Post by ivanhelguera on 2009-04-22
I've had a similar problem. 
I've installed Ms fonts manually to /usr/share/fonts/MS, and then ```
sudo fc-cache -f -v
```.
From that moment on, FF stopped dispaying any font when a windows font was appealed - there were noe letters whatsoever on the screen.

---

