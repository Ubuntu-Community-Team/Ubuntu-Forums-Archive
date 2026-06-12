---
title: "Powernowd hangs on install - how to disable?"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by mankypro on 2007-10-26
There is no article that tells you how to install w/o loading powernowd - do I need to edit the iso image and remove the package then reburn?  My BIOS Sager 9750 AMD FX60 has no option to turn off acpi.

Anyone?

---

### Post by amilak on 2008-07-23
I notice this thread is old, but I came across this when I was searching a solution for this exact problem. For my case later on I managed to solve it. If anyone else looking for a answer here is what I did...

My shuttle XPC system freeze when I tried to install mythbuntu I tested with Fedora also same, system freeze after loading powernowd.

This is what worked for me,

 1. I use the **Alternate CD ISO** & installed mythbuntu (ubuntu) using text installer. 

2. After install when system first starts up from hard disk (press 'esc') activate Grub menu & select "recovery mode"

3. After recovery menu pop up select "Drop to root shell prompt"

4. Once you are in root shell type "apt-get remove powernowd" to uninstall it.

5. Boot up system as usual now system will start without loading powernowd

But if you perform a auto system update powernowd maybe will install again, just go to recovery mode & uninstall it

Key thing is not to use the Live CD for installation.

---

