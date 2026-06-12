---
title: "Help with installation &amp; grub"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by mamak111 on 2012-10-18
Forgive my ignorance, I'm a complete newbie.
 
Over the years I've gotten tired of Windows's quirks and have been putting off learning about Linux. I've taken the plunge and am trying to get an Ubuntu server 12.04.1 up and running( no problem with the desktop version). 
 
The problem I have is as follows: I"ve been through the entire installation process and chose an SSH server instalation. Upto reboot everything runs fine, However on reboot the Grub 1.99 loader comes up (see attached) and when I select "Ubuntu, with Linux 3.2.0-29-Generic the startup entries load and then my screen goes blank.
My question is this: how do I get to a linux prompt(not Grub prompt) and how do I set it to automatically boot directly into the server and not the Grub prompt?

---

### Post by buckyaustin on 2012-10-18
I know on there are GUI programs on Ubuntu that will help, but since you probable don't have a GUI installed, I am sorry to say that I do not know how to do this through command line, but I have seen a tutorial about customising grub through command line.

Since you can't seem to boot try using [alt]+[f2] when the blank screen comes on this should allow you to use tty2. I hope thats the correct name. Also [alt] and the arrows keys sometimes work to allow you go into tty2-tty8.

---

### Post by bart.a on 2012-10-18
Did you do a total re-ïnstall? discarded all partitions and so on?..

I use the 12.04 server edition and I have not seen the grub menu.. I think the grub menu is 'turned off' when it's the GUI-free server edition..

In the image you provided, you see the grub menu.. activate the top one and press c, like it says at the bottom, does that do anything?

---

### Post by mamak111 on 2012-10-18
@buckyaustin
Thanks for the suggestions. I tried them but nothing happened.
 
@bart.a
I have tried several times, but they weren't clean installs.
I will format the disk and retry.

---

### Post by bart.a on 2012-10-18
A clean install is always best.. clutter from a previous install only messes up things..

---

