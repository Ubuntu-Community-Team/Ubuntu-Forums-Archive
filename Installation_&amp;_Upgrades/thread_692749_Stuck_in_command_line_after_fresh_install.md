---
title: "Stuck in command line after fresh install"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by Sveet on 2008-02-10
i got a laptop that was being thrown away, its battery doesnt work (so i have to keep it plugged in) and its screen is busted (so its hooked up to a monitor). it had win2k on it, with a password and the only way around it was to reinstall the OS. since i had no win2k CD i thought of linux and decided to mess around. that started about a week ago and after playing around a lot with bad CDs and finally got a working live CD and alternate CD. the live CD tended to lag up a lot with the installer and then freeze at random times, and then i read soemthing about the alternate cd installing in a command line. well i finished installing it and all i have is a command line. it said it set up the net, but whenever i try to sudo apt-get install ubuntu-desktop it looks for a CD, but it wouldnt accept the CDs i have. basically, im just looking for how to get to GUI.

---

### Post by solar george on 2008-02-10
```
sudo nano /etc/apt/sources.lst
```

Remove all lines which relate to cds - I can't remember exactly which but if you post the file then I can work out which.

---

### Post by Sveet on 2008-02-10
how do i remove lines in command line? i know how to read lines with the more command but i dont know how to edit.

---

### Post by PmDematagoda on 2008-02-10
Could you please post the specifications of your PC.

---

### Post by Sveet on 2008-02-10
dell latitude C510/C610

1ghz intel (i think celeron)
256 RAM
20GB harddrive

as far as i know its stock hardware. probably integrated graphics. i dont get any errors really, im just stuck in the command line.

edit:: ive looked at some other problems like mine, and things like startx dont work, they return an "unknown command"

---

### Post by PmDematagoda on 2008-02-10
One thing, did you get the Server edition or the Desktop edition of Ubuntu?

Also considering your RAM, you would be better off using Xubuntu since the minimum amount of RAM required by Ubuntu is 384Mb of RAM whereas that required by Xubuntu is much less.

---

### Post by Sveet on 2008-02-11
uhh no it was the CD. i remade the CD (apparently i didnt do a cd check on that one, i went thru so many i lost track) and it worked fine and im typing this from ubuntu desktop. btw minimum is 128 for live and like 194 or something like that for install, iirc

---

