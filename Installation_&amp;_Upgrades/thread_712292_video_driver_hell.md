---
title: "video driver hell"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Randy Matheson on 2008-03-01
i have just installed gutsy gibbon and have accepted the option for a restricted driver for my ATI Radeon 1600 pro. when i rebooted to finish the install, my computer screen goes black just after the ubuntu screen.  i have rebooted a couple of times but no luck!

is there anything that i can do to get my video back?

Thanks for the help!

RandyM

---

### Post by taurus on 2008-03-01
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When it's done, press <Alt>F7 to get back to the GUI login screen and restart X again with <Ctrl><Alt>Backspace.

---

### Post by Randy Matheson on 2008-03-01
thanks!  i'll give that a try!

randym

---

### Post by Randy Matheson on 2008-03-01
I followed instructions, i've got my desktop back, however by best resolution is 800 x 600.  just before the desktop, a warning came up saying that ubuntu couldn't identify my video card.  is there anything I can do to get better resolution?

Thanks!

randym

---

### Post by taurus on 2008-03-01
Perhaps you need to do the longer version, picking things from the list.

```
sudo dpkg-reconfigure xserver-xorg
```
Don't forget to either reboot or restart X server again when you are done with it.

---

### Post by zeleny on 2008-03-01
I am going through my little personal hell with this installation as well. I had a working version of 6.10. But then I had to add a pci-e nvidia 8600gt (had on-board nvidia 6100 before) and decided to upgrade to 7.10. ...  3d desktops and all. 

I never even got to the desktop screen as it always goes blank (no signal). I downloaded (and checked) both the regular and the alternate cds. the alternate cd installed it, but when i try to reboot all i get is the blank screen. i can boot into the recovery mode, but that is as far as i can get. all the advice i found so far did not get me anywhere. i realize this could be the "id10T" error, but due to my advanced age i don't want to spend weeks over this.

---

### Post by Randy Matheson on 2008-03-01
i'll give the new info a try ... at least i can get to my terminal to try out the commands ...

thanks for the help

randym

---

