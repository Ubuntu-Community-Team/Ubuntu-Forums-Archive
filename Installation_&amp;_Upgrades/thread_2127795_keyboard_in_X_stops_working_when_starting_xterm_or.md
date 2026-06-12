---
title: "keyboard in X stops working when starting xterm or LXTerminal"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by 7hs on 2013-03-21
Dear ubuntucomunity,

 I have just made some suggested updates in Lubuntu 12.10. After the restart I can not use xterminal anymore. If I starte them, the keyboard in the entire X seassion stops working. I can still use the mouse to logout and login again, then the keyboard works again. The computer is a lenovo X1 carbon.

What other information would one need to diagnose the problem? dmesg does not revile anything.

I don't even know which of the updated/installed packages did cause the problem (how could one get a list of recently updated packages?)


many thanks in advance!

---

### Post by 7hs on 2013-03-23
OK I'am sorry. I found the problem. Quite embarrassing. I permanently turned of the touchpad in the X1 carbon, because I always touch it accidentally (and thus selecting and unwantedly deleting text while typing). I did that in the bashrc with
[FONT=courier new]xinput set-prop 11 "Device Enable" 0[/FONT]

somehow this is not a reliable solution, because after the lubuntu update somehow the device ID 11 which used to point to the touchpad now is for the keyboard. So either you always check the device ID
with [FONT=courier new]xinput list[/FONT] or
the better solution seems to be to use the command

[FONT=courier new]synclient ToucpadOff=1[/FONT]

---

