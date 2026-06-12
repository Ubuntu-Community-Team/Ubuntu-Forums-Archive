---
title: "Keyboard layout problem after upgrade"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by walterBE on 2008-07-01
Hi, 

I have upgraded from 7.10 to 8.04 and since then have I problems with the keyboard layout.

I use a Belgian keyboard (AZERTY). It has happend several times that "azertyuiop" produced the symbols "æâ€êþÿûîœô" on the screen.

When I go to the configuration interfase in gnome to slected a layout the correct one is selected (Belgie). When I add it again or remove and re-add it again it works normaly again as a Belgian azerty. 

But when I reboot it is gone again. Mostly it changes back to a french azerty layout. That is close to a Belgian azerty but not the same.

It seems to revert always to the default settings. When I press in the keyboard configuration window on the button "go back to default setings" it picks "French alternative" for resons me unknown. I do not know why it would use that layout or how to change it.

Does anyone has suggestions?

Greetins,
Walter

---

### Post by chmod 777 on 2008-07-06
I have the same problem with my Russian layout.
I've posted a topic on 7th of May and nobody responded.
I didn't find how to solve this problem, so I re-add my layout every working session:(
If you install Ubuntu 8.04 instead of upgrading, there is no such problem.:guitar:

---

### Post by chmod 777 on 2008-07-06
Found solution here: [http://ubuntuforums.org/showthread.php?t=772511&page=2]("http://ubuntuforums.org/showthread.php?t=772511&page=2")

---

### Post by walterBE on 2008-07-09
Thanks. I have fixed it by including in the session startup the instruction to run;

setxkbmap

(for other people who have this problem)
system -> prefferences -> sessions 

add program

and make sure the correct layout is in the keyboard settings GUI. I have removed all except the correct one.

Editing the xorg.conf did not worked for me because I do not know the code for a Belgian keyboard (it is not be). In anycase it works now. 

Now only trying to find out why gnome locks up when I press the red logout button ....

---

