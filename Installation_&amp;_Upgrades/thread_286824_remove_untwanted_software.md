---
title: "remove untwanted software?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by janhenderson on 2006-10-28
Is there a tool to help me remove unwanted software? Stuff that I installed long ago but no longer use that I don't feel I want any more? Other than synaptic, I want something that'd say "this software hasn't been used for so and so, perhaps you no longer need it, do you wish to remove it?". Thanks

---

### Post by exir on 2006-10-28
i don't know if that feature is in ubuntu

with 'dpkg -l' you can see what software is installed on your pc. If you know that you dont use an program you can remove it by the synaptic package manager or by typing 'apt-get remove %name_of_package%'

good luck!

---

### Post by madmetal on 2006-10-28
as exir said remove all the software you dont need from synaptic or apt-get...
after this i use 
deborphan (install it via synaptic and run it at a terminal-shows you the orphaned deb packages)
and sudo apt-get autoclean

---

