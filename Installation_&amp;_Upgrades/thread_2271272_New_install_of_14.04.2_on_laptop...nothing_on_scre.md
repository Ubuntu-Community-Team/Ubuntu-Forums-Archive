---
title: "New install of 14.04.2 on laptop...nothing on screen but background"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by sillyboy on 2015-03-28
Hello all,

I just installed Ubuntu 14.04.2 on my old Presario CQ-60-215DX.  I ticked the boxes for the latest updates on the install.  Seems all went well till I rebooted (like it said to), and nothing came up on the screen but the background.

Thinking that I have a video driver problem, I downloaded the correct drivers (gulp) for my graphics card (256MB Nvidia GeForce 8200M) on my 12.04 computer.  Question:  How do I install them on the laptop?

Any help would be great!
Thanks

Getting old ain't for sissy’s...
SB

---

### Post by kerry_s on 2015-03-29
sounds like that opengl bug, you just need to reset unity.
press ctrl+alt+f1 to get to a terminal, type:
dconf reset -f /org/compiz/
sudo reboot

ps: if it keeps happening you might want to try ubuntu 15, i didn't see that issue there yet.

---

### Post by sillyboy on 2015-03-29
Hi kerry_s,

I got the terminal up, but it's asking for a "login:"  I entered my PW, now it's asking for a PW.  Nothing happens.  Am I supposed to have a login: phrase, etc???

Thanks

SB

---

### Post by sillyboy on 2015-03-29
OK I entered my name at the "login:" and it worked.  Entered PW, and it worked.  Will try -dconf reset -f /org/compiz/ 
sudo reboot

Thanks

---

### Post by sillyboy on 2015-03-29
I got into the terminal, and will try the

dconf reset -f /org/compiz/
sudo reboot

I will get back soon

Thanks

---

### Post by sillyboy on 2015-03-29
I entered |conf reset -f /org/compiz/| and received "bad command.  I tried |unity --reset| and got "compiz (core) - Info: Starting plugin: opengl".  I thought something was going to happen, but,
The curser then started blinking on the left edge of screen, and has been blinking for over a half hour.

Any other sugestions?

Thanks

---

### Post by kerry_s on 2015-03-29
did you reboot/restart ?

---

### Post by sillyboy on 2015-03-29
Solved!!!  I reinstalled Ubuntu 14.04.2 and it worked.

Thanks for the help

SB

---

### Post by sillyboy on 2015-03-29
Solved!!!  I reinstalled Ubuntu 14.04.2 and it worked.

Thanks for the help...

SB

---

### Post by kerry_s on 2015-03-29
like i said if it go's out again try ubuntu 15. the real issue is unity is not compatible so it uses software(slow) rendering which causes opengl to crash. in 15 there switching from compiz to mir.
also any de not using compiz will work just fine, so you can use gnome, mate, xubuntu, lubuntu, etc...

---

