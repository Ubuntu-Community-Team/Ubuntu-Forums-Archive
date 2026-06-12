---
title: "Ubuntu 7.04 and windows xp using virtualbox"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by benzfuf on 2007-04-26
Hey guys !

I recently installed ubuntu on my pc... i installed virtualbox too so i could have windows xp working on it... everything went fine, but then, during windows installation, i have to press F8 to confirm the installation, BUT I CAN'T... when i press it i have ubuntu's windows appearing on the monitor? anyone with a clue??

Is it possible to change the F8 HOTKEY in ubuntu?

---

### Post by Lord de le Warr on 2007-04-30
All you have to do is click on the windows installation window and then click F8. Thats what i did and it worked

---

### Post by St. Coin on 2007-05-01
I'm having the exact same problem. The install reads my "Enter" key so that I get to the accept terms page, but it will not read my pressing of the F8 key. I have a hunch that there is some Ubuntu hotkey assigned to F8 which is stealing the keypress away from the program or something....

---

### Post by St. Coin on 2007-05-01
I just found a work around!

Hit "Shift+F8"

:)

---

### Post by tiddy on 2007-05-08
Using beryl by any chance? F8 "initiates the window picker for all workspaces"

---

### Post by hyperair on 2007-05-13
I use Beryl and that happens too. I haven't tried it without Beryl though, the Shift+F8 workaround seems to work.

By the way, when you make Virtulabox lock onto the keyboard, even alt+tab in Beryl doesn't work, so why should F8 be captured by Beryl?

---

### Post by straxus on 2007-05-18
I can confirm the same behavior here.  I didn't know about the shift-F8 workaround, but switching to Metacity allowed me to press F8 and continue the installation.

Oddly, when the input is captured by VirtualBox, F8 doesn't have the same effect on Beryl as it normally does.  Rather than initiating the window picker it merely 'restores' all minimized windows to the desktop.   Odd.

---

### Post by david412 on 2008-04-05
If your keyboard has a function lock "F Lock" key, try turning it off. This worked for me when I was having the exact same issue with F8 not working.

---

