---
title: "Ubuntu alternate install black screen @ 60%"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by whereami on 2006-09-23
i have an unusual problem, im trying to install ubuntu onto an external hard drive, so after trying and failing with the desktop cd, i realized i needed the alternate install cd and that seemed to be working fine at first.
I was using advanced mode or whatever its called, so i could controll it step by step, and everything seemed to be working fine untill "select and install software". at 60% through this stage, my entire screen went black except for 2 small rectagles of grey, (looked like those block cursors) about halfway down the screen. and it just sat like that untill i manually turned off my computer.

i have no idea what happened. i dontk now why you would have an idea, but if you do, your a genius. ANY comment or suggestion would be apreciated.

---

### Post by dlehman on 2006-09-24
I have this exact problem, except I'm not installed to an external drive and the live cd boots but I have not tried installing that way yet.
at 60% the last package I see is configuring xorg-server if that helps 

Thanks

---

### Post by whereami on 2006-09-24
well, now theres 2 of us with no answer. hmm. ill keep messing around with the installer i guess. 
i tried just skipping the 'select and install software' step and it installed fine and i could boot to it perfectly, cept i didnt have any software, like GNOME or anything. so it was just a console and that was rather boring. :rolleyes:

---

### Post by dlehman on 2006-09-24
I got it figured out today, whoo hoo:D what I did was before you select to install at the bottom of your screen is several options one of them being vga I think it is F4.  my monitor will only handle 640x480 so I chose that and when I got to 60% It asked me to select display modes I unchecked 1024x768, and 800x600 and leave 640x480 checked then every thing worked for me.:o 

If you can boot to an console and login but have no graphics install the ubuntu desktop package 

first update sources
```
aptitude update
```

then install ubuntu desktop
```
aptitude install ubuntu-desktop
```

---

### Post by whereami on 2006-09-26
hmmmm, wow, i never would have guessed it had anything to do with that. ill try it! thanks alot.

---

