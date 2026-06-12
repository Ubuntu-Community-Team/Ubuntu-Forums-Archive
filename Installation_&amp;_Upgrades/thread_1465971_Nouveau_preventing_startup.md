---
title: "Nouveau preventing startup"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Rahu on 2010-04-29
I'm attempting to get the latest ubuntu installed on a fairly old laptop. The problem I'm running into is that a few seconds after the install CD starts up, before i have the opportunity to do anything, the system completely locks up and the screen fades to green/purple in a strange pattern and then back to black.

I found that the server install disc works and I was just going to install the desktop package over that, but on the first reboot after the install completes I get the same problem.

With the server install, I can see a message appear right before it fades so I'm assuming this is responsible:


nouveau: pointer to LVDS manufacturer table invalid


Any ideas on how i might get past this?

The laptop in question in a Dell Inspiron 8100 that I believe has a GeForce 2 GO video card

---

### Post by rochefort on 2010-05-12
I had this same problem with my inspiron 8100.  It has indeed an geforce 2 go.

Startup of the live cd was problematic until I modified the startup:
 - after initial loading of the live cd and choosing the language choose to edit the bootline
 - look for the line that starts with "linux " and add the text " nomodeset" to the end (this line will be wrapped so you'll be adding this text at the end of the wrapped line)
 - continue booting (press ctrl-x if I recall correctly)

Install works now and finishes.  
Reboot and hold the shift so you enter grub.  Edit the line the same way as described above.  Startup will work.
Update the system and install the nvidia driver.  After that you will have a proper booting system again.

---

