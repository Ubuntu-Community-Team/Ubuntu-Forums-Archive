---
title: "black screen installing Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by gian on 2009-11-14
hello All,

I would like to install Karmic on an old Travelmate 290.

The live cd boots into a black screen.

After some googling, I added linux vga=711 noapic nolapic to the kernel parameters, and was able to complete the install.

However, at the first reboot, I'm back to square one: a black screen, and nowhere to go.

What can I do now?

thanks for reading,
-gian

---

### Post by RodGer GR on 2009-11-14
I'm a newbee but I'll try to give an idea which may be a hint until you have a real answer from someone more experienced.

I think that we should find a way to add the parameter 'vga=711 noapic nolapic'
to the installed kernel. Which way you added it during the installation? Maybe you should just use a live cd to change the installed kernel adding the required parameter.

good luck.

---

### Post by gian on 2009-11-15
thanks RodGer,

I guess you're right, but I do not know how to add those parameters now that Karmic is installed.

When I booted the live, I pressed F6 at the first screen to add the parameters, and I expected that the install would have taken the entries to build the kernel.

-Gian

---

### Post by TheBlackjack on 2009-11-22
gian, its simple. When OS is started:
if you have grub2:
open your terminal [Application --> Accessories]
digit "sudo gedit /etc/default/grub"

look for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line or similar
add your parameterS "vga=711 noapic nolapic"
to obtain something like GRUB_CMDLINE_LINUX_DEFAULT="vga=711 noapic nolapic quiet splash"
save

run "sudo update-grub" and the game is done: next time your parameters will be in the right place ;)

if you are using 'old' grub let me know, steps are quiet different and you have to modify a 'menu.lst' file in /boot/grub, if my memory is till working.

---

### Post by TheBlackjack on 2009-11-22
gian, maybe I miss a step...
when grub is loading and if the grub menu wont display, press ESC while booting till grub menu appear
now you can manually add your parameter pressing 'e' (there are instruction lines below the grub menu)
pressing 'e' a mini editor will appear
find the line with "ro  quiet splash" parameters and manually digit your parameters after the 'ro' parameter and than CTRL-X to boot
to move you must use the arrow keys :)

after your os is started... complete the commands in the previous step

good luck

---

### Post by gian on 2009-11-22
BlackJack,

thanks for your support.

I wasn't able to interrupt the boot process, and my friend, on whose part I was installing Karmic, preferred to switch to Open Suse.

Anyway, I take a note of your suggestions for the future.

ciao,
-Gian

---

