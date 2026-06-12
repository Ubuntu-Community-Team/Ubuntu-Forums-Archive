---
title: "Problem and questions"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by J V on 2010-04-21
Problems:

[LIST]
[*]Window manager won't start
I don't know why, but it just won't start, I've had to resort to putting compiz --replace into my startup applications.
[/LIST]


Questions:

[LIST]
[*]Are keyboard shortcuts being saved somewhere else now?
I had a script that automatically set them up but although they appeared in the shortcuts window, they wouldn't work until I double-clicked them and clicked OK.
[*]Is the shortcut for setting ctrl alt backspace changed too?
At the bottom of the script I had a line that re-enabled it but when I looked at keyboard layout settings it was still disabled.
[/LIST]


My aforementioned script:
```
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/action "xkill"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/binding "<Control><Alt>X"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom0/name "Kill Application"
echo "Kill app is ctrl + x"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/action "gnome-system-monitor"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/binding "<Shift><Control>Escape"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom1/name "System monitor"
echo "System monitor is ctrl + shift + esc"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/action "nautilus /"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/binding "<Control>space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom2/name "Filesystem"
echo "Filesystem is ctrl + space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/action "gksudo nautilus /"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/binding "<Shift><Control>space"
gconftool-2 --type string --set /desktop/gnome/keybindings/custom3/name "Administrator filesystem"
echo "Admin filesystem is ctrl + shift + space"
setxkbmap -option terminate:ctrl_alt_bksp
echo "Restart X is ctrl + alt + backspace"
```

---

### Post by P4man on 2010-04-21
> **J V said:**
> Problems:

[LIST]
[*]Window manager won't start
I don't know why, but it just won't start, I've had to resort to putting compiz --replace into my startup applications.
[/LIST]

You mean windows decorator? IOW, you had no window borders? If you have compiz config setting manager installed, open it, make sure the "window decoration" plugin is active.

If thats not it, open gconf-editor, navigate to apps/metacity/general and make sure "compositing manager" is unselected.

As for control alt backspace, go to system > preferences > keyboard > layout > options > keys to kill the X server and enable control+alt+backspace.

---

### Post by J V on 2010-04-21
No, window manager... Alt click/drag, alt tab etc don't work, the window manager is non-existant.

That setting is already unchecked.

The question is, how do you set <ctrl><alt>Bakcspace on the command line...

Edit: Window manager required deletion of ~/.config/gnome-session/saved-session

---

