---
title: "[SOLVED] Uninstalled system configuration tools by mistake!"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by yan4 on 2014-05-01
Hi,

I was 'cleaning up' my system by removing everything that I won't use to save disk space. When uninstalling the 'universal access' stuff at certain point it showed me up a message (that I didn't read right) and I clicked the 'Remove Anyway' button. Well, after that several system configuration tools (such as screen monitor, mouse, sound volume, etc) just disappeared.

:redface:

I would like to know how can I install them back!

Thanks!

---

### Post by grahammechanical on 2014-05-01
I cannot say for sure and it also depends upon which version or flavour of Ubuntu you are using but Ubuntu+Unity 14.04 has something called unity-control-center which Synaptic Package Manager describes in this way: 

> This package contains configuration applets for the GNOME desktop, allowing to set accessibility configuration, desktop fonts, keyboard and mouse properties, sound setup, desktop theme and background, user interface properties, screen resolution, and other GNOME parameters.


It also contains a front end to these applets, which can also be accessed with the GNOME panel or the Nautilus file manager. 


Do you still have unity-control-center installed?

Regards.

---

### Post by yan4 on 2014-05-01
Yes, it is already there, but mostly of configuration icons disappeared. Under 'hardware', for instances, I only have 'printers'.

PS: My Ubuntu version is is 14.04.

---

### Post by yan4 on 2014-05-01
I think I figured it out and you helped a LOT! Thank you!

I entered terminal and typed:

*sudo apt-get install unity-control-center*

After to run this the icons came back to the Unity Control Center.

:)

---

