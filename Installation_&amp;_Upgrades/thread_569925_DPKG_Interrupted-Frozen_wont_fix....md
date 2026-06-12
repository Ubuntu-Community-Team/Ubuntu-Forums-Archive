---
title: "DPKG Interrupted-Frozen wont fix..."
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by poopingfish on 2007-10-07
Was installing Moblock and it went to updating blocklists and such, and then it just stayed there, basically froze. I guess their update servers ar down or im not sure.
But sudo dpkg --configure -a just restarts that, and sits there. Wont stop or do anything.
I cant update now, cant install programs or anything. VERY annoying!

Wotn let me remove the program either because its still running..How can i just CANCEL or force stop the moblock update stuff?

Thankyou!
           -Evan

---

### Post by overdrank on 2007-10-09
> **poopingfish said:**
> Was installing Moblock and it went to updating blocklists and such, and then it just stayed there, basically froze. I guess their update servers ar down or im not sure.
But sudo dpkg --configure -a just restarts that, and sits there. Wont stop or do anything.
I cant update now, cant install programs or anything. VERY annoying!

Wotn let me remove the program either because its still running..How can i just CANCEL or force stop the moblock update stuff?

Thankyou!
           -Evan

Hi and welocme, you may try the command in the terminal ```
sudo apt-get install -f
```. Hope this helps and please post back.

---

### Post by bigken on 2007-10-09
also look in synaptic for broken packages

---

### Post by poopingfish on 2007-10-10
Synaptic wouldnt open due to dpkg, and the -f install didnt do anything.
Although it is fixed now, someone gave me a force-remove package command on another forum.
Thanks guys!

---

### Post by ephman on 2007-11-02
> sudo dpkg -r --force-depends filename

just incase anybody needs this command.

thanks for your bandwidth,

ephman

---

