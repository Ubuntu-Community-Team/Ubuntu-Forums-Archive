---
title: "i made a dumb mistake and need some help plez"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by sorrow413 on 2011-08-31
hi im a bit new to lucid  i just started useing it and made a bit of a mistake i seem to have deleted the  module for my integrated   graphics card and im on a recovery partion  i made  so i could fix dumb mistakes i make now and again  anyway ill get t5o the point  im not too sure how to get it back a friend told me a reinstall would fix it but  i really dont want to do that isnt their a way through partitioning to  fix this like a way to download the driver for it or module or what ever and than just to copy it over i mean  when i try to log into my main partition i get an error saying i am running in low graphics mode and or in xorg i think its called i thought about tryin to just copy and paste the one in this partition  to the main one but than i had a permission glitch so i use Adding a contextual menu item to open as root:

   1. Open a terminal and type sudo su
   2. Then type the following:

          gedit .gnome2/nautilus-scripts/Open\ as\ root

   3. Now add the following to the open document and save the file:

          for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do

          gksudo "gnome-open $uri" &

          done

   4. Back at the terminal, type:

          sudo chmod +x .gnome2/nautilus-scripts/Open\ as\ root

All set, now when you want to open a file as root, simply right click the file and select Scripts-> Open as root

Note: You may need to restart to see the changes!
 i fond that and tryed it and found its the best way to back things up but it doesnt seem to alwoe me to put anything into the folder i mean im sure im doing something very  stupid and that theirs some very easy command i can enter that will fix it lol but sadly im a moron can anyone take pity and help me i would really like to not have to  do a full reinstall  im running this on  emachines model w5243   with a gb of ram  i know i know im livin in the stone age  but can someone help me o and my distro is lucid linux

---

### Post by Hakunka-Matata on 2011-08-31
Welcome to the forum.

> gedit .gnome2/nautilus-scripts/Open\ as\ root```
sudo gedit .gnome2/nautilus-scripts
```, is a much safer way to edit a file as root.  Starting the line with 'sudo' makes you root (gives you superuser privileges) only temporarily, 'sudo su' makes you root until you close that Terminal session.

Check [B]System>Administration>Additional Drivers.

EDIT: [/B]in Lucid (10.04) [B]System>Administration>Hardware Drivers.
[/B]

---

