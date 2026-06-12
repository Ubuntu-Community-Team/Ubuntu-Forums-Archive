---
title: "keyboard not responding; can't log in"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by mikeciance on 2007-04-03
i have ubuntu successfully installed, but i cannot log in because it does not recognize my keyboard input.  during installation, i was about to get the keyboard to respond by changing the device input, but this option is not available at login.  any ideas?

---

### Post by amohanty on 2007-04-03
I am sorry I dont understand. DO you mean that when you type, nothing happens?
Also what did you do to change the device input during installation??

AM

---

### Post by mikeciance on 2007-04-03
that's correct - when i type, nothing happens.  i can still use the on-screen keyboard, but not to log in

during installation, i was able to use the context menu to switch the input to "SCID Input" i believe

---

### Post by amohanty on 2007-04-03
Did your keyboard work prreviously?
Do you have a special keyboard? 
Are you sure it was SCID and not SCIM?? SCIM is the set of modules related to accessibilty.

In your bios there should be an option that says something about boot errors, select the option that says something like, halt on all errors and see if the bios complains about a keyboard not being present. Actually you should not even be able to get into the bios, but try it nevertheless.

AM

---

### Post by mikeciance on 2007-04-03
i have a dual-boot setup and the keyboard works fine in windows.  in fact, i'm using it right now.

i think it might be SCIM, but i'll have to go through the whole Live CD process again to check

i have an HP Multimedia Keyboard.  i tried changing the layout to HP Multimedia during the installation, but it didn't affect anything

is there any way that, upon installation, i can set an automatic login?  i know i can do that once i am in ubuntu, but can i have it install that way?

---

### Post by amohanty on 2007-04-03
Here's something to try:
1. Download and burn the alternate insall cd
2. Install in 'text' mode or the default in the install menu (its the same thing)
3. Do _not_ autodetect keyboard just use pc104 or pc105 
4. Install as usual.

See if that works.

AM

---

### Post by mikeciance on 2007-04-04
i'm still having some trouble

my keyboard does work in the first menu, and if i hit esc is starts the text install.  what should i be typing in to change those settings about the keyboard?

---

### Post by amohanty on 2007-04-04
> **mikeciance said:**
> i'm still having some trouble

my keyboard does work in the first menu, and if i hit esc is starts the text install.  what should i be typing in to change those settings about the keyboard?

I am not sure I understand the problem here. When did you type ESC. Basically just insert the alternate install cd, let it boot up and then press enter for the text install to start. It will install the regular default desktop version with the GUI.

Simply that in the middle of the text install you will be prompted to detect the keyboard type. Select No there and just click through. That should work.

HTH
AM

---

