---
title: "Ubuntu 14.04(Trusty Tahr): Can't take screenshots all of a sudden."
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by SteveL1990 on 2014-04-24
Hello, folks.

So, today, I finally decided to upgrade from 13.10 Saucy to 14.04 after waiting a few months in anticipation. And it looks like everything went mostly smoothly with one significant exception.....I can't take screenshots using the Print Screen key anymore right now. This is probably some sort of bug, but regardless, does anyone have a solution for this problem? 

I can at least do it manually by going to the Screenshot utility or opening a certain command in the Terminal but I take a *lot* of screenshots and I don't want to have to do all that every single time. So if anyone can help, I'd appreciate that. :D

---

### Post by Double.J on 2014-04-24
Hi there!

Sounds like it's not using the correct keyboard map after the upgrade. Double check all the other keyboard oddities are working correctly. If nothing else, you can add a screenshot shortcut in system settings -> keyboard using your terminal command?

Jj

---

### Post by SteveL1990 on 2014-04-24
> **Double.J said:**
> Hi there!

Sounds like it's not using the correct keyboard map after the upgrade. Double check all the other keyboard oddities are working correctly. If nothing else, you can add a screenshot shortcut in system settings -> keyboard using your terminal command?

Jj

Thanks. I think most of the others work, with the exception of the Insert and right Delete keys. Can you tell me how to do that key shortcut thing, though?

---

### Post by Double.J on 2014-04-24
Of course,

if you type 'keyboard' into the dash, it should take you right to the keyboard settings. Then click on the shortcuts tab and select 'screenshots' from the list. If it isn't already configured, click 'take a screenshot' to highlight it, and then press the print screen key on your keyboard.

note that it *should* identify this key as 'Print' if it does not, then it's likely you're using the wrong key map after the update

---

### Post by Double.J on 2014-04-24
Just incase, you can add a screenshot command if it isn't present. Click on the '+' at the bottom, give it a name and then add in your terminal command. To assign it a key, again highlight the line and then press your key combo.

for example, say I wanted to be able to take a screenshot of the current window, with the mouse pointer in the picture, but without the window boarder for an online guide I was making, with a delay of three seconds so I can put the mouse cursor where I want it.

I'd click the us sign, call it window pointer no boarder, and add the command
```
gnome-screenshot -wpBd 3
``` click save, then click on the 'dissabled' line and press, say my windows key and my print screen key.

now whenever I press the windows key and print screen 3 seconds later I get my screenshot.

hope it helps!

Jj

---

