---
title: "Important, need help about error in the startup screen"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by Green on 2004-12-02
Hi, Guys
   I have some errors after installation. It says,"cannot insert picehp, cannot insert hw_random".
   What does it mean?

p.s I have another wierd thing happen that everytime i **minimize the window** it goes away, it does not happen before i rearrange the panel.

---

### Post by mr_ed on 2004-12-03
With respect to the pciehp error, that's a benign message.  It's trying to add that module to your system, and doesn't find it.  It shows up on my computer, too.
If you want it to go away, type this command:

sudo gedit /etc/hotplug/blacklist
and add pciehp to the bottom.

Alternatively, you could type this
sudo echo pciehp >> /etc/hotplug/blacklist
instead, I think.  It's safer to do it the first way though (since I'm not 100% sure about this method).

About the minimising the window, I have no idea.  :(
What do you mean by "rearrange the panel?"

---

### Post by Green on 2004-12-03
To mr_ed,
     Thank you very much for replying me. I used to only have one error while startup which is pciehp. The second error "cannot insert hw_random ..." begins after i have done the following work which is weird to me. 
      I add some apps on the top panel, like realplay which succeed. Then i rearrange some app icon's position on the panel. After that, i download mozzila 1.72 and install in /usr/local/mozilla, and try to use the same method add mozzilla icon to the top panel which not succeed. Finally i realize all the minimized apps which used to be in the bottom panel all disappear, and i am sure they are all running. Then i open firefox 1.0 browser, everything works fine. After i minimize the browser, it disappear into the very right bottom corner like other apps did.

I was confused about this behavior, do you have any idea?
Thx [-o<

---

### Post by taygan on 2004-12-10
Right Click on the lower panel and "add to panel" the "window-list" applet.. the window selector boxes should come back for you.

---

