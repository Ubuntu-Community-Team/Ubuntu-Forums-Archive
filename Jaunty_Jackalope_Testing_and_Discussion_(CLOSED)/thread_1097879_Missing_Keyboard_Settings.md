---
title: "Missing Keyboard Settings"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Minus0 on 2009-03-16
I just installed Jaunty (which is very nice) and realized that I downloaded Ubuntu Alpha 6 instead of Kubuntu Alpha 6.  I did the usual "sudo aptitude install kubuntu-desktop" and everything worked out just fine.  However when it came time to turn on the Numlock key, I noticed that there is no keyboard setting in "Keyboard & Mouse".  The only keyboard options that are present are "Standard Keyboard Shortcuts" and "Global Keyboard Shortcuts".  

So my question now is, how to I restore the missing Keyboard system setting so I can enable Numlock through the GUI?

---

### Post by Minus0 on 2009-03-16
Also, trying to launch the panel from the command line doesn't work.  I can launch other panels though like mouse.

To test:
kcmshell4 mouse
That should launch fine

kcmshell4 keyboard
Nothing happens, but no error message either.  It's finding keyboard.desktop as it should.  kcmshell4 unfortunately doesn't have a verbose option.

---

