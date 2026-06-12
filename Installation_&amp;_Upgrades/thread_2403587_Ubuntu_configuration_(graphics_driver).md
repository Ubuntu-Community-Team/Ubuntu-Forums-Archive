---
title: "Ubuntu configuration (graphics driver)"
date: 2018-10-13
forum: Installation &amp; Upgrades
---

### Post by titant3k on 2018-10-13
Hello. I have to install Ubuntu 18.04 on my laptop, which is an *HP Envy 13* (ad102nl) as a second os. No problems in managing dualboot.

But, this time, I want to set up Ubuntu to work *properly* with Intel HD620 and Nvidia MX150, so **can you please tell me what drivers** (and how) **I have to install?** Ubuntu does a good work in configuring the system, but I always stuck somewhere in managing graphics drivers... For example sometimes Ubuntu doesn't open Nvidia configuration panel, or says that the driver isn't running. This time i'm performing a clean install, so that I can understand how to set it up in the right way from the beginning.

PS:
I also need to set a 150% scaling, because Ubuntu UI would be small to be used in 1920x1080 on a 13" device.

---

### Post by Bashing-om on 2018-10-13
titant3k; Hello -

> 
 so can you please tell me what drivers (and how) I have to install?

Allow the system to do the heavy lifting :)
In terminal run:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot the system to see the effect ... -> nvidia-settings in the GUI to tweak.

[INDENT][INDENT]ain't a thing to it - in ubuntu
[/INDENT][/INDENT]

---

