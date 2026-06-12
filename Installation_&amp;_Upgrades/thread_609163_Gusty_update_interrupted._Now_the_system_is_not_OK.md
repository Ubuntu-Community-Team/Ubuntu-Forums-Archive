---
title: "Gusty update interrupted. Now the system is not OK."
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by PabloCamino on 2007-11-10
I was updating through the update-manager. It was downloading the necesary packages. Since it took long, the screensaver started. When I got back and moved the mouse to quit the screen saver, it got frozen. The machine became unresponsive. I was forced to press the reset button on the chasis.

Now, I can start up and also log-in, but it trows me a bunch of error messages. Some features are not working, and, most of all, update-manager doesn't work anymore. I tried some console commands that found arround the web but none of theme worked (like apt-get install -f)

What can I do? It is recoverable or I should consider reinstalling feisty?
And, if I have to reinstall, which is the best way?

Thanks in advance,
Pablo Alberto Camino

---

### Post by Pumalite on 2007-11-10
Reinstall on top of the other one.(point to the right partition)

---

### Post by PabloCamino on 2007-11-11
OK. Will reinstall Feisty on top of actual partition.
I would like to not reinstall GRUB, because I've had a bad time dual-booting and I prefer to just load GRUB from a floppy.
How can I prevent the installation wizard from installing GRUB?

---

### Post by Pumalite on 2007-11-11
Bad idea. But, if you insist:

[http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)

---

### Post by unebaguettesvp on 2007-11-11
i ran into the same problem! check this out:

[http://ubuntuforums.org/showthread.php?t=586957]("http://ubuntuforums.org/showthread.php?t=586957")

see if that helps!

---

### Post by PabloCamino on 2007-11-12
I finally did a clean reinstall from the Gutsy Alternate CD.
I had to reformat the partition so I lost everything I had (That wasn't quite much), but now I have Gutsy working fine and since I used the alternate CD I was able to install the GRUB into a Floppy disk. So it doesn't mess up with the Windows XP MBR.

Thanks for the help. This forum has lots of info end experienced users.

---

