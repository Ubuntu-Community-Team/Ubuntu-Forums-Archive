---
title: "Ubuntu install hangs at cursor"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by alejandroD on 2006-08-29
I've tried installing Dapper Drake with both the live CD and the alternate CD (text install), and I'm getting the same issue. After completing the install process (partitioning, file install, etc), the screen goes black except for a blinking cursor. With the live CD install, the CD spins for a while as the cursor blinks, but then my screen turns off (as if there's no input) and the CD eventually stops spinning. The screen goes blank after a blinking cursor sits for a while in the alt. install as well (no CD spinning though). Has anyone encountered this? Here's my specs:

CRT Monitor
512 RAM
IDE HD
AGP GeforceFX 5200
AMD Athlon

Thanks for the help.

---

### Post by zxee on 2006-08-29
When the situation you've described happens you can also open another console using the Alt+Ctrl+F1 (or other function keys) see if there is any output at other consoles.
How does ubuntu behave on your system from the desktop/live cd?
You could also use the live cd to check the install see what's there, and maybe look at /var/log/install messages if they exsist. Hope that helps.

---

### Post by alejandroD on 2006-08-29
On the live CD installation, it runs through all the different parts of the install, saying, 'ok' after each one. After it's completed the install, it goes to the black screen with a blinking cursor, and then eventually the screen turns off as if there's no input.

I don't get as far as a desktop so that I can type the 'Alt+Ctrl+F1' command. However, after completing the text install, I can get to a command line 'safe mode' (or whatever it's called in linux).

I will also try looking for an install log - thanks for the suggestion.

---

### Post by alejandroD on 2006-08-29
Solved!

This was an nvidia driver issue. I used the ubuntuguide wiki to find installation instructions for my geforce card.

---

### Post by zxee on 2006-08-30
That's good to hear. Congrats on getting it working. BTW the Alt+Ctrl+F1 can be done without there being a gui desktop. The Alt+Ctrl+function keys pressed together will open a new console as long as the system isn't frozen or hung.

---

### Post by Peter The Plumber on 2006-11-22
> **alejandroD said:**
> I've tried installing Dapper Drake with both the live CD and the alternate CD (text install), and I'm getting the same issue. After completing the install process (partitioning, file install, etc), the screen goes black except for a blinking cursor. With the live CD install, the CD spins for a while as the cursor blinks, but then my screen turns off (as if there's no input) and the CD eventually stops spinning. The screen goes blank after a blinking cursor sits for a while in the alt. install as well (no CD spinning though). Has anyone encountered this? Here's my specs:

CRT Monitor
512 RAM
IDE HD
AGP GeforceFX 5200
AMD Athlon

Thanks for the help.

  I had the exact same thing with an almost bone stock Thinkpad T22 except for 512M ram and a CD RW/DVD ROM. I'm using the live install cd to boot 6.06 LTS. The trick for me was to boot the 'graphics safe mode'. Currently installing permanently after quickly checking out the live version. 
  Hope this helps someone.

Regards,

Peter

---

