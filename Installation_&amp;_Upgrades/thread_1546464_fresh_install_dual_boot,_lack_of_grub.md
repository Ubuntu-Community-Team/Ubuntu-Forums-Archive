---
title: "fresh install dual boot, lack of grub?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by skawars on 2010-08-05
After formatting and doing a fresh install of Ubuntu 10.04, I done some partitioning and installed windows 7 on a 50gb partition I made.

This as usual overrode the bootloader, but after some work in the terminal from the live CD I have managed to get my laptop to boot back into ubuntu as default, but have yet to see a successful grub menu. Any ideas please?

---

### Post by corrytonapple on 2010-08-05
Hit shift as you start up.

---

### Post by oldfred on 2010-08-05
Since you installed windows after Ubuntu grub does not know about the windows install.

run 
sudo update-grub

That should add windows to the menu and with 2 different system entries it should then show menu as default.

---

### Post by skawars on 2010-08-05
> **oldfred said:**
> Since you installed windows after Ubuntu grub does not know about the windows install.

run 
sudo update-grub

That should add windows to the menu and with 2 different system entries it should then show menu as default.

after taking the above advice of holding shift on boot i was presented with the problem you have described here, and running that command has it working perfectly.

thanks!

---

### Post by corrytonapple on 2010-08-05
Glad to here you found a solution. I am learning more every day.

---

