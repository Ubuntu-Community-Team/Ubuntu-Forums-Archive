---
title: "i need some beryl assistance"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by b0rderline99 on 2007-08-22
so i really got turned onto ubuntu after seeing a video featuring the cool eye candy which beryl has to offer
the only problem is that i cannot for the life of me get beryl to work
i am totally new to linux, been a windows user all my life, and though i am fairly adept with computers, linux is taking some getting used to.
but back to the problem, i have linux installed and working well, and i have beryl and beryl-manager installed, but when i go to run beryl (alone without the manager) everything just dissappears except for the desktop background and icons on the desktop (i have like one so it isnt very useful)
When i try to run it with the manager, the screen just flashes once or twice and it crashes back to the default

any suggestions would be greatly appreciated!! :)

(and as a side note, i am on windows right now, as my wireless doesnt work with linux, so i cant really copy paste any files :()

---

### Post by Pumalite on 2007-08-22
You would do better in Sub-Forum Desktop Effects & Customization.

---

### Post by b0rderline99 on 2007-08-22
alright ill try there

---

### Post by ThrobbingBrain66 on 2007-08-22
> **b0rderline99 said:**
> so i really got turned onto ubuntu after seeing a video featuring the cool eye candy which beryl has to offer
the only problem is that i cannot for the life of me get beryl to work
i am totally new to linux, been a windows user all my life, and though i am fairly adept with computers, linux is taking some getting used to.
but back to the problem, i have linux installed and working well, and i have beryl and beryl-manager installed, but when i go to run beryl (alone without the manager) everything just dissappears except for the desktop background and icons on the desktop (i have like one so it isnt very useful)
When i try to run it with the manager, the screen just flashes once or twice and it crashes back to the default

any suggestions would be greatly appreciated!! :)

(and as a side note, i am on windows right now, as my wireless doesnt work with linux, so i cant really copy paste any files :()

First, I'll need you to open a terminal and type 'beryl --replace'

Then, copy and paste any and all output here.  This will show us any errors that are occurring when launching Beryl.

---

### Post by b0rderline99 on 2007-08-22
> **ThrobbingBrain66 said:**
> First, I'll need you to open a terminal and type 'beryl --replace'

Then, copy and paste any and all output here.  This will show us any errors that are occurring when launching Beryl.

well do you mind if i kind of paraphrase? because i can only get my wireless internet to work on XP, i dont have a ground line for this computer

idk ill do my best :)

---

### Post by b0rderline99 on 2007-08-22
ok so i used a flashdrive to copy it over
and here is what i got (the format got messed up some in the transfer)

> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
beryl: glXCreateContext failed
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by runemaste644 on 2007-08-25
im having problems with compiz fusion and i want beryl to work so i have some eyecandy.
I get:```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: pixmap 0x2400066 can't be bound to texture
beryl: pixmap 0x2400168 can't be bound to texture
beryl: pixmap 0x2400215 can't be bound to texture
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
Initiating splash
Segmentation fault (core dumped)

```

Please help me too!

---

