---
title: "Give up soon with ubuntu =("
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by winzhangout on 2007-01-06
When i come to start or install i choose it have tested that cd works and burned it many times. I get to the after screen then i hear sound and get black screen. Everything works exept i dont see anything =(. If i try Ctrl+Alt+Backspace i hear sound again all the time i do it. If i Press Ctrl+Alt+F1 i come to command and if i write sudo dpkg-reconfigure xserver+xorg i manually configure it. but after that startx dont work. if i write sudo reboot now i get the prob that my comp reboot and then it stand i have to take out cd and press Enter, if i take out it stand the same take out cd and press Enter even that there is no cd in. And if i reboot with the computers start button all the thing i have changed with ctrl alt f1 dissapear.

I have a new Amd X64 laptop with ATi X700 graphic card.

Please help me with this need to see the screen.

---

### Post by jvc26 on 2007-01-06
Did you mean:
```

sudo dpkg-reconfigure xserver-xorg
startx

```
Rather than:
```

sudo dpkg-reconfigure xserver+xorg

```

Il

---

### Post by teaker1s on 2007-01-06
ati driver issue,search forums with ati model number and you will find how to resolve it

---

### Post by jvc26 on 2007-01-06
Heres an X700 post:
[http://www.ubuntuforums.org/showthread.php?t=332622&highlight=reconfigure+xorg](http://www.ubuntuforums.org/showthread.php?t=332622&highlight=reconfigure+xorg)
Il

---

### Post by winzhangout on 2007-01-06
After i have write 

sudo dpkg-reconfigure xserver-xorg

and changed to VESA instead of ati 
startx Dont work it stand something Server is allready running Display 0 or something please help i think if i can startx here it will work. When i reboot my changes is erased otherwise thats why i need help how to make startx work.

Btw tested Linux Mint with exact same problem. =(

---

### Post by confused57 on 2007-01-06
> **winzhangout said:**
> After i have write 

sudo dpkg-reconfigure xserver-xorg

and changed to VESA instead of ati 
startx Dont work it stand something Server is allready running Display 0 or something please help i think if i can startx here it will work. When i reboot my changes is erased otherwise thats why i need help how to make startx work.

Btw tested Linux Mint with exact same problem. =(

You could try:  ctrl-alt-F7
or
```
sudo /etc/init.d/gdm restart
```

or maybe
```
sudo /etc/init.d/gdm start
```

---

### Post by teaker1s on 2007-01-06
sudo gdm restart

---

### Post by firetux on 2007-01-06
I had that problem too. Fixed it with this: [http://www.ubuntuforums.org/showthread.php?t=238033&highlight=monitorlayout+x700](http://www.ubuntuforums.org/showthread.php?t=238033&highlight=monitorlayout+x700)

---

### Post by winzhangout on 2007-01-06
> **firetux said:**
> I had that problem too. Fixed it with this: [http://www.ubuntuforums.org/showthread.php?t=238033&highlight=monitorlayout+x700](http://www.ubuntuforums.org/showthread.php?t=238033&highlight=monitorlayout+x700)

This thing worked now to a weird thing when i tryed do exact same thing with kubuntu it says when write sudo killall gdm, something about gdm abouts not a program or something how can that be is gdm only in gnome "ubuntu".

---

### Post by orb9220 on 2007-01-07
Dosesn't kubuntu use kdm? gdm is for gnome?

---

### Post by winzhangout on 2007-01-07
thanks all now it seems to work, just need to fix the wireless network.

---

