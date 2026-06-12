---
title: "Session not being saved after Edgy install"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by pawarrp on 2006-10-27
I just installed Edgy. I used to have Dapper before. Now this was a clean install.
But once I installed Edgy, every time I click System -> Preferences -> Sessions and I try to add a new session as a startup program, after a restart, the added program is no longer there. I do not see any apply button either.
Am I doing some thing wrong or is it a glitch with Edgy?
I am using Kernel 686 SMP, Nvidia GeForce PCI, and Intel pentium processor.
I am so lost. I even tried reinstalling gnome-session but even that failed.
Please help.

Ubuntu rocks!  :cool:

---

### Post by Tails on 2006-10-29
> **pawarrp said:**
> I just installed Edgy. I used to have Dapper before. Now this was a clean install.
But once I installed Edgy, every time I click System -> Preferences -> Sessions and I try to add a new session as a startup program, after a restart, the added program is no longer there. I do not see any apply button either.
Am I doing some thing wrong or is it a glitch with Edgy?
I am using Kernel 686 SMP, Nvidia GeForce PCI, and Intel pentium processor.
I am so lost. I even tried reinstalling gnome-session but even that failed.
Please help.

Ubuntu rocks!  :cool:

hehe, I have the same problem, but i just find a solution........ seems for some odd reason the .config/autostart doesnt have the write permission, so it cant save the settings...

that what u have to do in terminal..

```

sudo chmod a+w /home/[USERNAME]/.config/autostart/

```

replaces [USERNAME] with your one.. :D

and it should be working fine again.. :D

---

### Post by pawarrp on 2006-10-31
Works! 
This is simply brilliant. 
BTW I dunno if you noticed, but I also seem to be having issues saving my alacarte menus. I cannot change the menus. I cannot even check or uncheck. 
I been checking the forum for a solid answer but haven't found one, mebbe its just me trying to do a wrong search.
Any clue?
Again, thank you so much for this brilliant solution.

Ubuntu Rocks! :cool:

---

### Post by amanita on 2006-11-01
Thanks man! sudo chmod a+w /home/[USERNAME]/.config/autostart/  also works for me :cool:

---

### Post by groggyboy on 2006-11-13
it worked!  thanks

---

