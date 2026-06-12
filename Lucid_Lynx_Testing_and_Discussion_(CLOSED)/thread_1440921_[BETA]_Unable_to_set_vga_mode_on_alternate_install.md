---
title: "[BETA] Unable to set vga mode on alternate install Lucid 10.04"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dougalb on 2010-03-28
I am not sure if this is the right forum for this but I am having problems trying to do a fresh install of Luicd 10.04 Beta amd64. Specifically I am unable to make it past the first menu with a working display.

I am installing on a HP Compaq 6710b and have in the past set vga=791 when installing 9.10 Karmic amd64. It appears that this is not longer supported on the Luicd install. I have found references to gfxmode= and gfxpayload= settings for grub2 but not solution to setting the correct graphics mode when installing.

Does anybody know of the method to change the vga/graphics mode at install time on the Lucid 10.04 alternate cd?

---

### Post by Mark Phelps on 2010-03-28
It's NOT the right forum.  Please post your beta-related questions to the Development & Programming, Lucid Lynx Testing forum.  Folks there will be able to help you a lot better.

Will be asking the Mods to move this thread to that forum.

---

### Post by cariboo on 2010-03-28
From the main menu screen you should be able to select nomodeset when you press F6, this should start the installation process.

---

### Post by dougalb on 2010-03-28
Have tried that and still no luck. Just a blank screen when I choose install.

Just to confirm steps, boot from alternate CD -> Choose English -> Press F6 - select nomodeset -> Press Esc to exit menu -> Press Enter to install

(I have come up with a workaround using desktop CD but would still like to solve issue on alternate CD as well.)

---

