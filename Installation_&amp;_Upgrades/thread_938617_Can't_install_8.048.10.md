---
title: "Can't install 8.04/8.10"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by doctorwho? on 2008-10-05
I've hit a speed bump here... no matter what i do whenever i upgrade i either get the black screen of death or i can't get passed the grub load screen and it asks me to go to the "help" command... some answers would help... Here's my Xorg.logX

---

### Post by doctorwho? on 2008-10-06
thats a little disconcerting....

---

### Post by norgur on 2008-10-06
disconcerting indeed...
can you give more detailed information about your system? which ubuntu version are you running at the moment, some details about your hardware, etc?
*/&#8364;: Xorg seems to start up correctly

---

### Post by uidb4056 on 2008-10-06
When you boot the grub menu appears? or a message saying ' press ESC to get the menu' ?
If yes you can try to edit pressing 'e' to get the lines of the first option, move the cursor to the kernel line and press 'e' again, go to the end of the line and remove 'quiet splash' press intro and then 'b' to boot with these temporary workaround, if it boots OK you can edit the menu.lst to make the changes permanent.

---

### Post by doctorwho? on 2008-10-06
Well i'm currently running 7.10, AMD64 3200+ Operton, SB audigy, Asus A8V deluxe mobo board, Gforce4 Ti4800.

After that certain point of the grub loading it just refuses to beyond the loading screen, the install goes just fine though which is the mysterious part.

---

### Post by doctorwho? on 2008-10-08
i've got both ATA and SATA running,would that have something to do with it ?

---

### Post by timcredible on 2008-10-08
have you tried installing using the 'safe graphics mode'?

---

### Post by Kevbert on 2008-10-08
It may be best if you perform a fresh install of 8.04 from CD. Don't forget to backup all your data first. You can get a list of all installed packages with
```
sudo dpkg --get-selections > filename
```
Save the file to a floppy for safekeeping
Next you can then re-install these packages on 8.04 by copying the file to your home directory and run
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < filename
sudo aptitude install dselect-upgrade

```

---

### Post by doctorwho? on 2008-10-09
haven't tried installing in safe graphics mode, i'll have to try that floppy drive thing though

---

### Post by doctorwho? on 2008-10-11
okay update: removed my old IDE, particianed off my newer 500G sata drive, 8.04 is working perfectly. Its booting up in under 2 minutes... this is seriously impressive ! 
Thanks for the help !

---

