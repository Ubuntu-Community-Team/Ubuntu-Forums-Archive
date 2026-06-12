---
title: "Cant load Ubuntu 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by davincidgenius on 2010-10-14
Hi,

I am currently using an Acer Extensa machine with Windows 7 and Ubuntu 10.04 dual boot. I tried to upgrade 10.04 to 10.10 , everything was fine until I am asked to restart. After restart I selected Ubuntu from dual boot menu. It cant load Ubuntu and machine keeps rebooting. Can anybody tell me what to do next ??

---

### Post by TBABill on 2010-10-14
Do you get an error message of any kind right before the machine reboots? It sounds like you are making it to the grub menu and selecting Ubuntu, but then something fails and it forces a restart. It may be something in your grub configuration or it could be an issue with the install itself. If you can capture the error code and post it here, the cause may be found within that information.

---

### Post by crienoloog on 2010-10-14
Same here...
Error: file not found
Error: file not found


twice real fast then back to first screen. 
Machine is HP Probook 4510s with Windows 7. Updated a Wubi installed 10.04 to 10.10.
I can start Windows 7.

---

### Post by TBABill on 2010-10-15
Ahhh....a Wubi install. I always install to a separate partition so unfortunately I can't be of much assistance on this one.
 
Edit: re-read your posts a couple times and I am confused. First post you said it's a dual boot and you upgraded, but the next post of yours says it was a Wubi install that you updated. Is Ubuntu installed via Wubi or is it a separate partition with its own install? 
 
If you installed in Wubi then you have to start Ubuntu within Wubi. You can't select Ubuntu from a Grub2 or other boot loader menu and have it start if your install of Ubuntu is within your Windows partition.

---

