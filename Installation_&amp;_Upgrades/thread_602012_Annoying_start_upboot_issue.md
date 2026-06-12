---
title: "Annoying start up/boot issue"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Urinemachine on 2007-11-03
I am not sure what the deal is - I installed 7.04 after a few months of Vista, and now when it boots I get the "Grub loading press ESC to access menu" and it counts from like 3 2 1, if I don't touch anything, it says "Starting up...." with a cursor blinking.  Nothing happens.  If I instead hit ESC to enter the Grub menu, I can choose the installation via the menu and it boots up.

I want to use this machine as a router, so this isn't going to work as is.  Can anyone give some advice?

---

### Post by Jose Catre-Vandis on 2007-11-03
Don't know why this is happening but.....

Try making GRUB do what you are having to do manually. once you have booted up "your" way, open a terminal
```
sudo gedit /boot/grub/menu.lst
```
Scroll down to find "hiddenmenu" and put a # infront of it
Scroll to timeout and change the number to 5
save and reboot

---

### Post by PilotJLR on 2007-11-03
Is there a "default" line in menu.lst?
Can you post your menu.lst?

---

### Post by Jose Catre-Vandis on 2007-11-03
> **PilotJLR said:**
> Is there a "default" line in menu.lst?
Can you post your menu.lst?

You want to set your default OS to boot yes?

Open up your menu.lst file for editing

In the stanza for the OS you want to boot, ensure there is the line:

savedefault

and remove this line from the other stanzas

then

scroll up to find the line "default"

replace the number after "default" with "saved"

so from this:  default    0
to this:           default    saved

save out and reboot, and your new default OS should be selected

---

