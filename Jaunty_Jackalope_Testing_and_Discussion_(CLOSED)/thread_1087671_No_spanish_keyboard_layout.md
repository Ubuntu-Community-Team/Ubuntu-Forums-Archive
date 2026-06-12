---
title: "No spanish keyboard layout?"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dalonso on 2009-03-05
I just opened a bug about not being able to select an spanish keyboard layout:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/337016](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/337016)

Actually, it seems even impossible to select any "latin" keyboard: nor spanish, nor portuguese, not catalan, ... so I am stuck to an english layout.

But I have not seen any comment in this forum about anyone with the same problem. Am I alone? Or is it so simple to fix that anyone has managed to fix it but me?

Best regards.

---

### Post by Darkshade on 2009-03-05
I'm using Spanish as my main layout and I never had problems with it :???:

---

### Post by nyarnon on 2009-03-05
PT on 64 and 32 bit, no problem whatsoever.

---

### Post by dalonso on 2009-03-05
Bump!!!

@nyarnon, darkside: Please, did you get to Jaunty updating from Intrepid or through a fresh install?

---

### Post by nyarnon on 2009-03-05
> **dalonso said:**
> Bump!!!

@nyarnon, darkside: Please, did you get to Jaunty updating from Intrepid or through a fresh install?

Both, have several machines, one was a fresh install the other upgrade. Have two more intrepids and one xubuntu.

---

### Post by Darkshade on 2009-03-05
Updated from a fresh Intrepid install, although my /home is on another partition so most of my settings remained after the reinstall, including the keyboard layouts.

---

### Post by nyarnon on 2009-03-05
> **Darkshade said:**
> Updated from a fresh Intrepid install, although my /home is on another partition so most of my settings remained after the reinstall, including the keyboard layouts.

Keyboard layouts in the homedir?

---

### Post by Darkshade on 2009-03-05
> **nyarnon said:**
> Keyboard layouts in the homedir?

There must be some configuration file in there because after the reinstall I had my keyboard layouts set up the same way as I had them before (layouts, shortcuts and the rest of the settings). Just spent 15min looking for the settings file but couldn't find anything, any ideas?

---

### Post by dalonso on 2009-03-05
~/.Xmodmap ,maybe???

---

### Post by nyarnon on 2009-03-05
Modification, normal install at least here doesn't have them.

---

### Post by nyarnon on 2009-03-05
> **Darkshade said:**
> There must be some configuration file in there because after the reinstall I had my keyboard layouts set up the same way as I had them before (layouts, shortcuts and the rest of the settings). Just spent 15min looking for the settings file but couldn't find anything, any ideas?

Sure your configuration files pointing to the keymaps but the keymaps themself are stored in /usr/share/consolefonts and /usr/share/X11/xkb/keymap if I'm not mistaken.

---

