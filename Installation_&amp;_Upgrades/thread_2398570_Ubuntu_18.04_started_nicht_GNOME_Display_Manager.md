---
title: "Ubuntu 18.04 started nicht GNOME Display Manager"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by gottfried21 on 2018-08-14
Hello,

have upgraded to 18:04. The boot process went to the Ubuntu site, then it was over. Then started in safemode and queried via terminal the graphics card with lspci. Nothing was displayed. Then I have the Nvidia driver installed on Synaptic. Now, the safe mode is no longer synonymous. I started then 18.04 from the CD and booted in the attempt. Have queried there with lspci and got the following message:

lspci -nkk | grep "VGA \ | 'Core' \ | 3D \ | Display" -A2

VGA compatible controller [0300]: Intel Cooperation 82G33 / G31 Express Integrated Graphics Controller [8086: 29c2] (rev 02)

If I start in normal mode now, "Started GNOME Display Manager" will appear and that's it.

Then started with ctrl + alt + F2 and tried to delete gnome-core, gnome-shell, gnome-session. Message: not instralled. I installed gnome-core, gnome-shell and gnome-session. Hatr unfortunately brought nothing.

Searched forum, without result.

Can someone help me?

Greetings, Gottfried

---

### Post by gottfried21 on 2018-08-14
Hello,

I have done a complete reinstallation of DVD. Everything seems to work

Problem solved!!

Gottfried

---

### Post by wildmanne39 on 2018-08-14
I am glad you got it fixed!

In the future please translate your post into English as you posted in an English only sub-forum or post in a sub-forum for your language, we have many available.

Thanks

---

