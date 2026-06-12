---
title: "Fresh Ubuntu 12.10 won't boot on first try"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by floebig on 2012-11-19
Hey,

I am really pleased with the new Ubuntu 12.10 64 bit which seems to run a lot smoother on my desktop machine, so first I want so say thank you for the good job developing Ubuntu!

However, I'm having a problem booting the machine up: When I switch on the machine or reboot the system, it get's to where the Ubuntu splash-screen should appear, but then the screen shuts of and the computer gets stuck. After I switch of the machine and switch it on again, all works fine. I need to say, that after the reboot the Grub loading screen appears and when I select the normal "Ubuntu"-option, it asks me for the decryption password I entered while installing. After I enter and confirm this, all works fine. So basically, the 1st try always fails, but when I select Ubuntu from the Grub loader at the 2nd attempt, all works fine. 

Once up and running really everything is working perfectly. But the boot-reboot-procedure really is annoying.

Does anyone know about this problem or do you need more information?

Thanks in advance, I hope this is the right place to ask ;)

Cheers,
Freddy

---

### Post by dgharmon on 2012-11-19
> **floebig said:**
> the 1st try always fails, but when I select Ubuntu from the Grub loader at the 2nd attempt, all works fine.

I had to tweak the BIOS settings else it won't boot ...

---

### Post by floebig on 2012-11-19
okay. I will see what I can find anything there. Do you remember what you did in particular?

---

### Post by dgharmon on 2012-11-20
> **floebig said:**
> okay. I will see what I can find anything there. Do you remember what you did in particular?

I selected the default settings, which switched off over-clocking and something related to dual core, and memory speed ???

---

### Post by wildmanne39 on 2012-11-20
*Thread moved to **Installation & Upgrades**.*

---

### Post by floebig on 2012-11-20
Okay, thanks for the info. I found out that installing the correct NVidia driver for my Geforce 8800GT made the difference. I came to this solution as I tried to enter the password while the screen was black and tadaa, the system continued booting. 

As a hint: Installing the driver via sudo apt-get install nvidia made the system unusable because unity did not load. I purged it to return to the default driver and activated the nvidia-current via Software Sources -> Additional Drivers. 

All works fine now.

Cheers

---

