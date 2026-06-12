---
title: "I can't beleive it's still borked :("
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by BorgCymru on 2007-06-05
OK I have just done a clean re install after the .16 update messed everything up. I ran the updater once it popped up after the first start up and after a re boot it all went tits up AGAIN.

Have they mot removed or fixed the problems ?

They wouldn't be that stupid would they.

Also got this error message after using Envy

API mismatch NVIDIA kernel module has the version 1.0.9755 but this X  module has version 1.0.9631

---

### Post by PilotJLR on 2007-06-05
My -16 kernel works just fine on a couple computers.

What exactly is the error / problem??

---

### Post by BorgCymru on 2007-06-05
mostly with the NVidia drivers again it seems. not sure weather to update them use Envy or use Envy and then update.

---

### Post by rumli on 2007-06-06
I think this means that you need the "nvidia-glx-new" package instead of "nvidia-glx".

---

### Post by BorgCymru on 2007-06-06
But do I download the updates then run this command or run this command and then download the updates ?

---

### Post by dabl on 2007-06-06
If you install nvidia-glx-new with Synaptic, kernel upgrades will not bork your Nvidia driver.  If you use Envy, then kernel updgrades WILL bork your driver.  However, if you use Envy, the only thing you have to do upon rebooting after a kernel upgrade and finding yourself at a text prompt is (a) log in, and (b) type ```
sudo envy -t
```, and it will reinstall the driver.

If you don't have a GUI at the moment, due to borked Nvidia driver, then you might just as well do ```
sudo apt-get update
``` and ```
sudo apt-get install
``` then re-install your Nvidia driver. :)

---

