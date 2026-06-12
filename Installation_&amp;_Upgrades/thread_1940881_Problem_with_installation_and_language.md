---
title: "Problem with installation and language"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by Luikkari on 2012-03-14
Hello

I really need help with Ubuntu. I'm so NOOB with this and I'm about to throw my computer out of my window. I have problems and questions:

1. I cannot install some apps from Software Center, because I tried to install Teamviewer and now I can't install app from Software center because I tried to install Teamviewer and it said I got too many errors in installation so it didn't install whole Teamviewer and now it's bugging or something.. (teamviewer7:i386:) How I can delete that? I have tried tutorials but I have no clue where is System folder... I'm so frustrated atm. Ubuntu is great better than Vista but still..

2. How I can set my language back to English? Oh nevermind I just noticed that my Ubuntu is so messed up. It says I can't install or uninstall any languages. This is my poor translate of error:
"You can't install or uninstall any programs. Fix the problem using Synaptic (something) or with command "Sudo apt-get install -f". Title is something like "Program database is broken" idk.

I'm also getting spammed in software center. It says something like this: "Programs can't be installed or uninstalled before packetlist (or something) is fixed. Do you want to fix it now? when I click Fix it asks me password and then goes away and that error pops up. This is all Teamviewer's fault. Should I just uninstall ubuntu and go back to vista? I'm dissapointed because I want to have Ubuntu but this makes me to uninstall it. Everything is made so hard. :mad:

If someone can help me to uninstall teamviewer I would appreciate it.

Edit: I'm also having sometimes problems that my Pidgin etc window goes darker (Freezes) for a while..

---

### Post by cortman on 2012-03-14
OK, for all your problems I have one solution: Reinstall. If you have any data in Ubuntu you want to save, back it up and do a clean reinstallation. If you have problems after that, let us know and we'll be glad to help. But for your current situation, a reinstallation is probably the best thing you can do.
Good luck!

---

### Post by oldos2er on 2012-03-14
Open a terminal (Ctrl-Alt-t) and run ```
sudo apt-get install -f
``` If there are errors please copy and paste the terminal output here.

---

### Post by QIII on 2012-03-14
Reinstalling ("Nuke 'em from orbit") is not a solution and should not be the first consideration.

Could you copy the errors as requested?  There might be clues there.

---

### Post by Linux_junkie on 2012-03-14
How did you install Teamviewer? I just searched synaptic package manager and teamviewer was not listed.

I have just searched online for Teamviewer for Ubuntu and it looks like it installs like any other debian/ubuntu package.  In that case, if you open up the terminal type the following:

```
sudo apt-get purge teamviewer
```

---

### Post by Luikkari on 2012-03-14
Why is everything made so hard? I uninstalled Ubuntu and I will try ONE MORE TIME. IF I follow tutorial "How to play RSPS with ubuntu" I still get error. IF I read tutorial how to uninstall something I CANT UNDERSTAND IT. THANK YOU Teamviewer. Well atleast I changed my language with tutorial.

---

### Post by cortman on 2012-03-14
> **QIII said:**
> Reinstalling ("Nuke 'em from orbit") is not a solution and should not be the first consideration.

Could you copy the errors as requested?  There might be clues there.

My advice was based on the OP's high frustration level with the current system- if they are willing and able to keep plugging away at issues, I agree it would be better to try to sort things out.

---

