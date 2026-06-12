---
title: "Ibex Down and Left Arrow Keys Not Repeating"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by brett6913 on 2008-10-31
I have a very strange issue.  Only the down and left arrow keys are not repeating.  Each time I push either one of these buttons, it moves the cursor one space, but will not move it more than one space when holding the button down.  My keyboard was working fine in Hardy, but ever since I have upgraded to Ibex, I started seeing this issue.  All the arrow keys on the keypad work just fine.  I have tried the keyboard on a WinXP machine and it works fine.  

Another odd thing I noticed.  In the Keyboard Preference -> Repeat Keys section.  It doesn't matter if I have the 'Key presses repeat when key is held down' option checked or not, it does not change the keyboard behavior.

I have a KB-0316 keyboard and selected the Keyboard model: 'Generic 105-key' in Keyboard Preferences.

Any ideas? I guess it's helping me improve my vi skillz... :tongue:

---

### Post by jessed on 2008-11-01
This is a known issue. The bug ID that I found while searching last night is 278078 ([https://bugs.launchpad.net/bugs/278078](https://bugs.launchpad.net/bugs/278078)). 

    It's extremely irritating. Some of the notes in the thread above point out that there are duplicate keyboard entries in the X log file. I don't know if it's related but I've noticed that I am only affected if I use synergy to control my Ubuntu box from a windows system. If I don't start synergy the bug doesn't manifest.



thanks,
--jesse

---

### Post by tkite on 2008-11-07
I have the problem when launching synergy too, but it goes away when I close synergy.  I did find a dumb fix, but it's unreliable:

[LIST=1]
[*]Start Synergy
[*]Go to the Ubuntu System menu and pick Preferences -> Keyboard
[*]Uncheck the "Key presses repeat when key is held down" box
[*]Close Keyboard Preferences
[*]Open Keyboard Preferences again
[*]Re-check the key repeat box
[*]Close Keyboard Preferences
[*]Your key repeats will now work while synergy is running...for this session
[/LIST]

Problem is, it doesn't always work, but it does MOST of the time.  It also will break if you try to do the "slow keypresses" trick described in an earlier post, but will work again after restarting X.  This is a very annoying bug, and ALMOST has me going back to 8.04.

---

### Post by Pelee on 2008-12-19
Same problem here, solution doesn't work though. Anoying, but good to know that its not me who botched his configuration up.

---

### Post by jessed on 2008-12-19
The solution I eventually settled on was switching which system is the synergy server, and which is the synergy client. This issue went away at that time. Synergy also became much more stable when I made the linux box the server and windows the client.

--jesse

---

