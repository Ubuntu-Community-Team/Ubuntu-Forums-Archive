---
title: "XMMS problems"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by astronerd on 2005-05-17
Hi, I am trying to play mp3s on XMMS and I downloaded it using synaptic, but when I add the files to XMMS, it just freezes and then I have to force it closed.  I cant reopen another xmms after that either.  I thought that I had gotten all the nec. files that came with it, but I dont know.  The same thing happens when I try to play something via streamtuner and XMMS.  Is there a way to uninstall XMMS and try again?  Should I be looking for a particular file in synaptic?  (OT: When I do start synaptic, it gives me an error warning that it cant find a long list of http:// sites, but for some reason it still has a good number of packages to choose from.  I am very very new to this so I dont know if this is normal or if something is messed up....  I have all the repos uncommented too. )  
Charles

---

### Post by AMCDeathKnight on 2005-05-17
Im not sure about this problem, as I am new to Ubuntu, but maybe this could help you:

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

---

### Post by bruizer on 2005-05-17
This is a konwn issue with ALSA. If you go into XMMS properties and change your output plug-in to eSound instead of ALSA, it ahould light up nice. I had the same issues initially when I upgraded from Warty to Hoary...

Let me know if this works ;-)

---

### Post by astronerd on 2005-05-17
[QUOTE=bruizer]This is a konwn issue with ALSA. If you go into XMMS properties and change your output plug-in to eSound instead of ALSA, it ahould light up nice. I had the same issues initially when I upgraded from Warty to Hoary...

Let me know if this works ;-)[/QUOTE]
 Got it! Thanks, thats what it was.

---

### Post by bruizer on 2005-05-17
Anytime! Glad you are hearing things again!

---

