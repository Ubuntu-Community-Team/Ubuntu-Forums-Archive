---
title: "i broke synaptic..."
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by lecter255 on 2007-11-10
ok so I am really noob, and I tried to add the universe repository but i think i typed the url in wrong or something and now i can't even open synaptic. if i open it it give me the following error

E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

how can I just set the repositories of synaptic back to default? also, after I set it back to default, how do I add the universe repository?

I try undoing what I did but that didn't work.. obviously

---

### Post by jasmuz on 2007-11-10
Open a terminal (alt+f2 and type gksu gnome-terminal)
now type at the prompt: nano /etc/apt/sources.list

Look for the malformated text or anything that dosent fit.
Hit Ctrl+X then S to Save.
type at the prompt aptitude update

That should be it! 

Hit me back if you need.

---

### Post by lecter255 on 2007-11-10
wait nvm i figured it out... but how do i add the universe repository though? and having that repository means i can install everything installable on linux through synaptic right?

---

### Post by lecter255 on 2007-11-10
btw thx jazmus

---

### Post by jasmuz on 2007-11-10
Your /etc/apt/sources.list must contain the following to be completely enabled:

deb [http://do.archive.ubuntu.com/ubuntu](http://do.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://do.archive.ubuntu.com/ubuntu](http://do.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse
deb [http://do.archive.ubuntu.com/ubuntu](http://do.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

After you save your list... the type aptitude update, to update your available lists.

---

### Post by lecter255 on 2007-11-10
thanks again jasmuz. i did it and I try to install skype via synaptic, but it still can't find skype. is it possible to install skype through synaptic? i know i can just download it and install but synatpic keeps everything neat and stuff. just wondering, not a big deal.

---

### Post by weblordpepe on 2007-11-10
In Synaptic, go to 'Settings' at the top, then 'Repositories'.
From there you can tick the boxes for universe & multiverse repositories.

---

