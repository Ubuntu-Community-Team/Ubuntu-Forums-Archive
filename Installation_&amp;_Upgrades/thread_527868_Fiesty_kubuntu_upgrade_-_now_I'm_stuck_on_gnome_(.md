---
title: "Fiesty kubuntu upgrade - now I'm stuck on gnome :("
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by TooRight on 2007-08-17
Hiya,

Well tonight I decided to finally upgrade to fiesty. things seemed to go well, until the reboot when I logged back into Kubuntu and realized my graphics were all all messed up. Everything was all squished down together and not in the proper colour bit (reminded me of the old 'safe mode' in windows, lol), and instead of seeing text and buttons, all I saw was zigzaggedygrey and black streaks. it was impossible to do much at all. I must say though, the nongraphical stuff was fine, like the text in the terminal, etc. Thinking it was my ati card and the drivers again, i went through what worked when i first upgraded to edgy... didn't work. 

Upon rebooting, I decided to check into the gnome session and everything is just perfect in here! :D

I think part of the problem might be the way i had kbuntu set up, all veryyy customized, my own icons, beryl, karambas, everything changed and not looking like kubuntu even.

Does anyone have any experience with this? Any suggestions?


** Just wanted to add... I did the upgrade through the updater, if that helps

---

### Post by dabl on 2007-08-17
If Gnome works and KDE doesn't, then the difference is that gdm runs the Gnome desktop, and kdm runs the K desktop.  So, it sounds like your problem is isolated to kdm.  Unfortunately, I have not clue #1 to how one would go about removing and reinstalling kdm.  But I'm pretty sure you'll be doing it from a true console!  :)

---

### Post by mikewhatever on 2007-08-17
> now I'm stuck on gnome :(
It seems like nothing to complain about.

---

### Post by TooRight on 2007-08-17
lol, but mike, I reallyyy loveeeeee KDE!


Found my solution in my xorg.conf file... at the end where it says:

```

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

I had to change it to say:

```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

and now... Woo hoooooooo, I can use my KDE!!! :D:D:D:D

Now... to straighten out beryl, lol

---

