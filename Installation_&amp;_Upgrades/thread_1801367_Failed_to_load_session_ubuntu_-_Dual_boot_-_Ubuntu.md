---
title: "Failed to load session ubuntu - Dual boot - Ubuntu-11.04 with winxp sp3"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by HorseHero on 2011-07-10
Hello! anybody to help me to resolve the problem? I am a new user to Ubuntu 11.04 natty,
 
I am using Pentium 4 2.4 mhz pc with G845GVSR Mother board.Broand band network available. I have the winxp sp3 installed originally in my PC, Today I have installed Ubuntu-11.04 Desktop i386 in my pc and completely installed and updated well.everthing was worked perfectly, I have played audio and movie also. nice.
 
but I wanted to upgrade the gnome3 desktop, in the terminal I have typed the follwing;-
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-session
 
during installation of gnome-session, I got the power failure, Installations distruped due to power failure. after half an hour, I have again rebooted the pc,
grub boot loader Ok
in the graphical user login and password given ( gdm option-ubuntu, user defined session & terminal ) there is no option for gnome, in the gdm-ubuntu option login the following error message shown;-
window shown 
failed to load session ubuntu - log out 
if pressing logout button again come to user login.
I couldn't see the desktop screen.
I tried to reinstall gnome3 repository in the terminal, its telling everythin updated.
even I couldn't purge the gnome3 also!
 
please help me, what will be the next step.
 
Grub booting ok, from there I can got to the winxp booting well and its working fine.
only I couldn't get the ubuntu desktop.
Horse Hero

---

### Post by Bucky Ball on 2011-07-10
Just a question, not a fix. Why did you issue, 'sudo apt-get dist-upgrade'? 'sudo apt-get upgrade' I would have thought to be the command. The former command upgrades your *entire release*. The latter command only upgrades packages (if you have any installed that need to be upgraded).

---

### Post by HorseHero on 2011-07-10
both cases, It doesn't work. but command terminal working well. I couldn't go to the ubuntu window session.?

---

### Post by Bucky Ball on 2011-07-10
If you can get to a terminal you can issue:

startx

... and see if that gets you to a desktop. If so, we're getting somewhere.

---

