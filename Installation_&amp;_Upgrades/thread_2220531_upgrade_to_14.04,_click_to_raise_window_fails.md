---
title: "upgrade to 14.04, click to raise window fails"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by kfstephensii2 on 2014-04-28
Upgraded two, single-boot machines from 13.10 to 14.04. The problem: Windows do not come to foreground when left-clicked, except for Chromium (Kile, file manager, tweak tool, okular, and evince are some that do not come to front). 

I use "sloppy focus" and the focus does follow the mouse. 
Other than minimizing windows in front, I use Alt-TAB to bring windows to front. Problem exists using sloppy, mouse, and click to focus.

I did a fresh install on two new machines and they don't have this issue. Only the upgraded machines are afflicted.

---

### Post by jbaerboc on 2014-04-28
Sounds to me like there's a package somewhere that is not getting upgrade or being upgraded incorrectly. Have you compared relevant package versions on you upgraded versus clean install machines?

---

### Post by kfstephensii2 on 2014-05-01
I was able to extract a list of installed packages using 'dpkg' but it does not contain version info. Any suggestions?

Also, my skills are limited to using 'diff' to compare files. Is there something better since that seems like the files would have enough minor differences to confuse it.

I don't know if it's related, but when I log in after the screen locks, each window has a black border around it. It obscures other windows and the background. I changed my theme (Window, GTK+) to Adwaita and the black border disappeared. The black border did not return after resetting the theme back to Ambiance.

---

### Post by beetcom on 2014-05-03
i have the same problem after upgrade to 14.04, i "solved" with unity tweak tool changing "focus mode" in windows administrator, "click" to "mouse", but i prefer click in a windows to be focused and not automatically focused when mouse is above.
Another way... i use tint2 (a smallest taskbar that not demand cpu) for change beetwen opened windows (sudo apt-get install tint2) and after comand tint2 or place it in aplication at launch, this way is easy to minimice and maximice the windows to be focused but is not the ideal way.

---

### Post by beetcom on 2014-05-11
SOLVED 

I do not know why but this has worked, from unity tweak tool autoraise not work, from a terminal type this if it works

gsettings set org.gnome.desktop.wm.preferences auto-raise true

---

### Post by Allen.McIntosh on 2014-05-16
You may need to try various combinations of gsettings and gnome-tweak-tool.  Be patient.  I like focus-follows-mouse with no autoraise.  It never seems to be the default, and it always takes some fiddling to get it right.

---

### Post by kfstephensii2 on 2014-05-16
But I don't want auto-raise --- I like interacting with a window even if I can't see all of it. I don't want it to come to the front. If I did, I'd click on it.

A.M, "focus follows mouse" is all I've ever used on all my linux machines. It works great right now. No matter which focus type I used, clicking on the window does not bring it to the front. It already has focus (b/c of focus follow mouse).

A hint could be that if I click in the document part of Chromium, it will come to the front. Clicking on the menu or window frame of Chromium does not bring it to the front. It is the only app for which this happens.

I agree with jbaerboc that it is an upgrade vs. a clean install issue. But I can't track down what package is the culprit. Suggestions on how to compare between the two machines would be useful.

---

