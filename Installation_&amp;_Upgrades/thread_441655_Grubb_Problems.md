---
title: "Grubb Problems"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Joel1943 on 2007-05-12
I attempted to install ubuntu server on my a second drive of my PC.  Windows XP Professonal was on the other drive.  Installation went without exception.  Upon reboot I am receiving a grub error 21.  I went into the rescue mode and looked at the menu.lst file and it seemed to be exactly what other posts on this site have said it should be.
Howeve, I am a very newbie and don't know how to edit this file from the shell given to me in the rescue mode.   I was able to look at it with CAT.

I would appreciate any suggestions.

---

### Post by phidia on 2007-05-12
[http://ubuntuforums.org/showthread.php?t=439603&highlight=grub+error+21](http://ubuntuforums.org/showthread.php?t=439603&highlight=grub+error+21)

Take a  look at that thread and see if it applies to your situation.

You can edit the file with > sudo gedit menu.lstor perhaps > sudo vim menu.lst since you have the server version I'm not sure if that has gedit, but it may. vim is a little harder to use at first.

---

### Post by Steven_B on 2007-05-12
If all you have is a terminal (which is normal for a server), you won't have Gedit.  Vim can be hard to use if you don't know how, so here is a micro-tutorial:

"vim filename" opens "filename".
Press "i" to allow insertion of text.
Edit text like most other text editors.
Press escape to quit insert mode.
Type ":save filename" to save the file to "filename"
Type ":q: to quit.

---

### Post by Joel1943 on 2007-05-12
Thanks for the help. I would have never thought that changing the bios was problem.  As soon as I changed the slave drive from off to auto the the load menu came right up.

Thanks again.

---

