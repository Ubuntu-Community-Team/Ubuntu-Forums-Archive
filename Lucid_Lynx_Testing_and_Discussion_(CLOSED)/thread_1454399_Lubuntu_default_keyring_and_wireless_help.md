---
title: "Lubuntu default keyring and wireless help"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BigSilly on 2010-04-14
Hiya guys, my first time in the testing forum!

I've recently been asked to speed up an old laptop for someone, and after trying out a few distros I was really impressed with Lubuntu, in spite of the fact that it's still in beta. The laptop in question is an old Toshiba Equium A60 with only 192Mb RAM and a P4 processor. I'm also using a Netgear WG511v2 (China) with ndiswrapper. Lubuntu really is tremendous on this hardware, and a massive step up from the Windows XP it came with.

Anyway, the problem I'm having is with regards the wireless network and the keyring manager. Every time I log in to the laptop, it prompts me to enter the password for the default keyring. After that, I then have to select the network I want from the list in network manager, otherwise it won't connect. 

Is there any way to get Lubuntu to automatically connect to my wireless network without having to go through this keyring app and manual network selection? I've tried deleting the keyrings from .gnome2 (solution found on Google), then setting a blank password but this doesn't work. It seemed to work at first, but then I still had to select my network manually. I should add that I have the system bang up to date from the Lubuntu PPA.

Many thanks. :)

---

### Post by kerry_s on 2010-04-14
edit the connection(right click the icon) & select "available to all users" that should bring it up before log in.

---

### Post by BigSilly on 2010-04-14
Excellent. That seems to have fixed it just great. Many thanks! Such a simple solution. D'oh!

---

### Post by BigSilly on 2010-04-15
Just wanted to add that I had to install wicd so that it would log onto my network automatically after this change, as it still wouldn't stick after several reboots. Still, it's fine now. :)

---

