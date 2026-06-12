---
title: "Feisty Fawn: power button ignored"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by lenorin on 2007-05-03
Hi,

I'm using an inspiron 6000, with a newely upgraded Feisty Fawn. Almost everything kept working after the upgrade, but for some reason the power button on my laptop is no longer registered as anything. I checked the power settings, and they still say to "Ask me" for a power button press. Which means that when I press the button the "quit" menu should pop up. I'm sure that some config file got edited and does not match what the power applet says.

Does anyone else have this problem? I would be curious if anyone knows where that conf file lies?

Thanks in advance,
Lenorin

---

### Post by MeduZa on 2007-05-06
Hi all, I have the same problem, I set up the power button to turn off the system.
I found that this problem only happened when you are logged in, if I press the button when the login screen is, the pc turn off normally

Any idea?

---

### Post by erny on 2007-11-04
Hi

I had the same problem.

For me 

```
sudo apt-get install --reinstall acpi-support 
```

did the trick.

---

