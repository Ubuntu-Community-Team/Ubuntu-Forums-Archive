---
title: "Optiplex GX260 upgrade to 11.10 issues"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by grumpyoldgit on 2012-01-16
I usually leave upgrading a couple of months or so after each new release to allow it to bed down and any issues to become clear.

On attempting to upgrade from 11.04 to 11.10 today I get the message:-

[I]Your graphics hardware may not be fully supported in Ubuntu 11.10.
The support in Ubuntu 11.10 for your Intel graphics hardware is limited and you may encounter problems after the upgrade. Do you want to continue with the upgrade?[/I]

I've backed out and googled the boards. It certainly seems that people are having problems with the Intel graphics of the GX260 and despite plenty of suggestions have given up. Bearing in mind that the PC is nine years old, it may be an upgrade too far. I gather that Xubuntu is more suited to older computers. What I am unclear about is whether this extends to lower graphic demands and if so, whether there is a method of upgrading directly from Ubuntu to Xubuntu.

---

### Post by dino99 on 2012-01-16
no worry, this message is about the new Unity front-end that needs a 3D graphic card/chipset to run. As you dont have one, then unity 2D is the fallback choice.

But if you dont like/want unity at all, then install gnome-session-fallback to get a gnome-classic login

---

### Post by JoseeAntonioR on 2012-01-16
You will have some troubles with the video card. I had that PC, and I solved them easily following these steps:

1.- Search the values of HorizSync and VertRefresh of your monitor.
2.- Open a terminal and type "sudo X configure :1" without quotes. This will create a new xorg.conf file.
3.- In the same terminal, type "gksu gedit xorg.conf.new" without  quotes. This will open a text editor with the file that you have just  created in there.
4.- You will see that it is divided in sections. Search for the Monitor  section, and before the EndSection line of that section, add this two  lines, without quotes:
"HorizSync       30.0 - 81.0
VertRefresh     56.0 - 75.0"
 5.- Replace the values in there with the values found in step 1.
6.- Save and close the file. If you want to, you can put it into a  pastebin so I can check it before you move. If you do not want to, then  move on to the next step.
7.- In a terminal, type "sudo mv xorg.conf.new /etc/X11/xorg.conf"  without quotes. This will move the file to its correct position.
8.- Restart the PC.


 In case it does NOT works, copy this command into a paper: "sudo rm /etc/X11/xorg.conf", and boot into text mode, to enter this command without quotes and remove the file. If it works, please ignore this step.

---

