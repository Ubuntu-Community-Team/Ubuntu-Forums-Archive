---
title: "Upgrade to 9.10 font problem"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by MrQuan on 2009-12-07
After upgrading my Ubuntu 9.04 to 9.10 the login screen shows no font character but squares instead. Kind of like this... [][][][][][][][][]
I believe this is an issue with the actual fonts being corrupted or broken somehow.

I managed to blindly log in and found my desktop was fine, but I have a customised theme with my own fonts specified different from default.  I created a new user as a test and logged in to that, everything was boxes: menus, labels, everything.

I went back to my normal login and scrolled through all the fonts to see which were broken by looking at the preview.  The ones that I found broken are:...

[LIST]
[*] Bitstream Vera Sans
[*] Bitstream Vera Sans Mono
[*] Bitstream Vera Serif
[*] Inconsolata
[*] Monospace
[*] Proggy Square TTSZ
[*] Sans
[*] Serif
[/LIST]
 
I'm assuming that some of these fonts are the default ubuntu fonts?  I've done an apt-get update, upgrade, and dist-upgrade without any luck.  I've noticed that by browsing the font directory I can see some of these fonts, but I cannot view them in the font viewer and the icon doesn't preview the font - so they may be corrupted??

Any help would be awesome~ thanks in advance.

---

### Post by MrQuan on 2009-12-07
Is there an easy way to overwrite/replace the effected font files?  Or is there some sort of repair operation that cold help?

I'll need this laptop up and running pretty soon for a work presentation. #-o A backup, reformat, and re-install with a fresh Ubuntu 9.10 ISO is looking to be an easier solution as the clock ticks on... :(

***Any ***suggestions are welcome.  Thanks!

---

### Post by MrQuan on 2009-12-07
Thread not resolved, but closed I suppose.

I'm going to reformat now.  I've seen one or two similar thread to this one but they seem to have also ended with a reformat.  Sorry if you're here looking for a solution. :roll:

---

### Post by TiloBunt on 2009-12-20
same here for a 9.10 install. No idea so far

---

### Post by TiloBunt on 2009-12-20
mine was because of a corrupt CD. use USB and all fine so far.

---

