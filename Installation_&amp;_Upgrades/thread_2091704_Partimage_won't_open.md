---
title: "Partimage won't open?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-12-05
Was told Partimage is a good utility to use when attempting to clone/save a HDD partition. Installed Partimage with Synaptic but when looking in apps, Partimage can't be found.

Where is it and how do you open Partimage?

---

### Post by steeldriver on 2012-12-05
it's a terminal based (ncurses) application afaik - you just run it from the terminal using the command 'partimage'

---

### Post by cybrsaylr on 2012-12-05
Tried that:
For Ubuntu Users

sudo partimage

Put: sudo partimage
In terminal, along with password and get a 'command not found' message.

---

### Post by steeldriver on 2012-12-05
well idk then - I just installed it as a test on my 12.04 laptop (using apt-get instead of synaptic - shouldn't matter afaik) and it opens fine

---

### Post by Mark Phelps on 2012-12-06
Last time I checked, Partimage did not work with Ext4 filesystems -- and there were no plans to update it.

To clone such filesystems, a better choice (which does work) is Clonezilla.

---

### Post by cybrsaylr on 2012-12-06
Mark Phelps, thanks. Got a message similar to that when attempting to install partimage with terminal. 

Thanks for the Clonezilla tip.

However the failing drive I planned to clone has totally failed and I guess to option to clone it is gone.

---

