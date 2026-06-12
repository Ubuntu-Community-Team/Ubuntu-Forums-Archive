---
title: "Display Issues"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by lamogo on 2012-05-01
Hello,

I just upgraded to 12.04 LTS and am having an issue with my dual display. I am using an nVidia triple head graphics card, I am using the VGA and DVI heads. The other is for TV which I am not using. 

After I installed, as typical, only one screen was working. I opened the display settings and it reported one screen as a "Laptop" which it isn't. I then opened nvidia X server program and it is seeing both displays correctly. I marked the other screen as enabled chose the "twin view" mode saved the config file and rebooted.

Now the display settings show that it is a laptop display still but is the width of both my monitors. Also there is a unity launcher on both screens. (I am actually not sire what it is called, forgive me, but it has the shortcuts to the programs and trash bin on it.) Also my mouse hangs between both screens unless I scroll quickly.

Did I do something wrong when I installed and how can I fix it?

---

### Post by lamogo on 2012-05-01
Looks like I solved it on my own.

I removed the nvidia driver, reconfigured X, rebooted and then when I went to the Ubuntu display manage both screens were correctly detected. I think the issue is the nvidia driver.

---

