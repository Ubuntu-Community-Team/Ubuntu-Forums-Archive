---
title: "Install issues (screen goes blank)"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by lamapuppy on 2008-01-14
I'm using a PC with 2 Nvidia GeForce 8500 GT cards.  I'm having an issue were after I'm at the initial boot screen (where you have the options to install, change resolution etc) where if I choose "install" or "install in safe graphics mode" it just goes blank and even my backlight of my monitor goes off.

I'd love to get this PC switched from Vista to Ubuntu, but this is obviously a hinderance.  Any ideas?  I'm willing to try near anything to get off Windows Vista!

---

### Post by JR Tyner on 2008-01-15
I have the same problem. I left it at the black screen and went out to eat. I figured I'd mess with it when i got back but it was working when I walked in. 

Nice going Janet ](*,)

---

### Post by Partyboi2 on 2008-01-15
See what happens when you add some boot options. At the main menu press F6 at the end of the line try changing ```
splash
``` to ```
nosplash
``` and adding ```
vga=791
```

---

### Post by lamapuppy on 2008-01-16
I did as directed.  Changing the VGA didn't work but when I just did the "nospash" change it showed me what was being processed.  I believe it was after it said it was loading the startup script (or something to that effect) that the screen would go blank (with backlight this time) and not continue.

I do find upon pressing the power button on my PC that it states that it is cancelling connecting to ports on my pc and is initializing shutdown.  I'm not at the PC at the moment so I can't give a word for word description of the error.  Seems like I'm making progress but I'm not sure if I should just let it sit and wait or if I need to modify things more.

I installed 7.10 just fine on another PC that my girlfriend uses, so I'm not sure what is up with mine (which is a newer PC and is an AMD 64).

Any other suggestions?

---

### Post by dannyboy20 on 2008-01-16
i hav the same problem...my screen goes blank right after the splash screen...and im forced to shut it down and start it up again....i hav a amd64 turion with and nvidia video card....

---

### Post by rappin05 on 2008-01-16
I fixed the problem by taking out the video card but encountered a different problem later
8600 gt geforce
intel core 2 duo 6600 64bit

---

### Post by lamapuppy on 2008-01-17
This is my only video card (I have 2 of them, for duel screen) and no onboard to use as a backup.  I wouldn't be able to remove the card and continue as then I'd have no video.

---

### Post by redcrayon on 2008-03-23
I just got around this problem...  i have an amd64 3200+ and a 8600gt.

After the screen went blank (and went to standby) i left the machine running... a few minutes later the cd cranked up and the screen turned on once it reached the desk top...

I also read in another forum post that when the screen turns off you can press "enter" to kick start live cd (havent tested that myself.)

I am now running the install from the live cd session, will let you know how that goes :)

Peace.

---

### Post by IanW on 2008-03-23
From the LiveCD start menu press F6 and delete the words "quiet splash" from the end of the line shown.

Once installed remove the same words from GRUB by using
```
sudo gedit /boot/grub/menu.lst
```

---

