---
title: "Run Program in other than the native Launguage."
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by *PTR on 2008-08-20
I want to run an x app (in this case Glade-3) in english 
But - my native system language is Swedish.

It works when i run 
qt-language-selector --mode install to change native language
and then reboots, but then i need to run  
qt-language-selector --mode install  and then reboot again to restore my original language.

What i want is to run a program with mulitiple languages supporet and trick it to run in another than the native language.

I have tried to save the English_Us settigns with set > AllSettings_Eng
And then after rebooting in my native language i source the file from an kterm and after that run glade-3 from the kterm, but with no success.

My reason for doing this is that i am following the glade-tutorial and i need to have the program running in english so i can follow the tutorial as clearly as possibly.


*PTR

---

### Post by *PTR on 2008-08-21
bump

---

### Post by *PTR on 2008-08-23
Ok - Obvisualy it didnt work when i sourced the file which containing the variables i need.

I thought it was some more - or some deeper settings that i had to figure out, i was so sure about that so i didn't even check that i after that i sourced the file actually had the variables in my system. BIG SHAME ON ME ](*,)

Today i did that.
Still my settings was containing 

GDM_LANG=sv_SE.UTF-8
LANG=sv_SE.UTF-8
LANGUAGE=sv_SE:se

even though i sourced the file AllSettings_Eng
So i tried to manually..

export GDM_LANG=en_US.UTF-8
export LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8

After that i startad glade-3 from the same teerm that i have run the previous commands.

suiccess -now i run glade-3 in english even though the rest of my system is in swedish.

Now i just need to learn how to adept the settings from a file so i don't need to set the language settings manually.

---

