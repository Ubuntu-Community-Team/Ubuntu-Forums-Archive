---
title: "Possible bugs in Update manager."
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2010-04-12
Hello everyone,

After downloading the new Ubuntu 10.04 Beta 2 (32Bit) i noticed some updates in update manager failed to install multiple times they are:

Cups-common
Firefox
Empathy

& their associated dependancies (Approx 15 files in total, all the other updates completed and ok) has anyone else experienced this problem?

PS: I know its a beta so I think it could be possible they are still "under construction"

---

### Post by 23meg on 2010-04-12
It's very likely that the packages or their some of dependencies are being held back (I'm guessing since you provided no details on how the packages fail to install, any error messages etc.) and that's normal in the development branch.

You may benefit from reading the [sticky]("http://ubuntuforums.org/showthread.php?t=1343434") [threads]("http://ubuntuforums.org/showthread.php?t=1343449") in this forum, if you haven't.

---

### Post by Nightstrike2009 on 2010-04-12
thay just failed to download and i had to cancel the installation and uncheck them to download the other updates, firefox always reached 90% then got stuck and i had to cancel manually. Same story for empathy and cups-common but at different percentages.

Thanks 23meg, for trying to help me I suspected they were maybe in an "unfinished stage" because of the beta status, but wanted confirmation of my suspicions by more experienced members.

UPDATE: Cancelled message reads: 
"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

Followed By:
"W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.3-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.3-1_all.deb)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.3-1_i386.deb"

---

### Post by dino99 on 2010-04-12
new update-manager has been released 1 hour ago, have to wait a little to see it into repo.

---

### Post by ranch hand on 2010-04-12
I would try using  a real tool for updating like apt, aptitude or synaptic if you want a gui.

Update Mangler is a bug.

---

### Post by dino99 on 2010-04-12
> **ranch hand said:**
> I would try using  a real tool for updating like apt, aptitude or synaptic if you want a gui.

Update Mangler is a bug.

bugs, that's all we love  :lolflag:

---

