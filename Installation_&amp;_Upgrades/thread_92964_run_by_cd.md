---
title: "run by cd?"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by sonihei on 2005-11-20
i have installed ubuntu on my newly formatted system... disc1 i believe is an installation cd for the operating system and disc2(live) is for the applications... my situation is like this: when i dont insert the disc2 it wont start in GUI just in command(DOS) mode... my question is, is this really run by cd? thanks for the help in advance...

---

### Post by yesplease on 2005-11-21
When you installed ubuntu  you do not need the CD Rom disks because the applications are on the hard disk. Change the boot options in the bios to make the hard disk boot first. 

Tell us more about your problem if this doesnt answer your question. 

Edit: Tell us **a lot** more about your problem if this doesnt answer your question.

---

### Post by sonihei on 2005-11-22
mu ubuntu is version 5.04... and it still runs by cd... is it different in v5.10? please help me out...

---

### Post by Tamlin on 2005-11-22
This may sound patronising so please forgive me, but is it possible that your installation of Ubuntu just doesn't automatically start the x server?
When you start your comupter without the CD and it just starts with a prompt type "startx" (I think, can anyone else help here?) and see if that starts the GUI. If it does then all you have to do is add this line to the appropriate startup file (sorry I don't know which one) and it will automatically start the GUI for you.

---

