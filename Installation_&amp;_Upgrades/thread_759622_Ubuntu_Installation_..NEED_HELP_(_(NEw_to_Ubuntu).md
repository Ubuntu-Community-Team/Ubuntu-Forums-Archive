---
title: "Ubuntu Installation ..NEED HELP :( (NEw to Ubuntu)"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Dominicanboy260 on 2008-04-19
ok well im new to this kind of operating systems and i was recently trying to install ubuntu on my pc .. 
i got the cd .. it works fine wen i load it onto my PC.. wen the process end it goes to a black screen and i suppose that im suppost to enter some sort of command ? 

i need help ..

is there any website that could give me complete instructions step by step to the installation?

---

### Post by boomdiddly on 2008-04-19
I'm guessing your trying to boot into the live cd version, once the progress bar has finished on the black screen with the Ubuntu logo it should load straight into the desktop.

Whats your machines spec specially graphics card make and model?

Cheers

Paul

---

### Post by Pumalite on 2008-04-19
You specs would help. Lacking that, here are some links:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by conorsulli on 2008-04-19
Could you please clarify, Are you running just as a live CD or are you trying to install ubuntu? If you mean when you switch it off? then open the CD drive and press enter..then it should shut down. But I really dunno what you mean!:confused:

---

### Post by cward002 on 2008-04-19
Did you download the server image or the desktop image? The server image does not have a graphical desktop installed by default. You have to type the following commands at the prompt to install the graphical desktop
 
```
sudo aptitude install ubuntu-desktop
```

 or for Kubuntu you have to type 

```
sudo aptitude install kubuntu-desktop
```

hope this helps

Colin

---

### Post by Pumalite on 2008-04-19
Try:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver, then: startx

---

### Post by Dominicanboy260 on 2008-04-19
well now i see that the cd had about 56 errors and i cant figure out wat i did wrong during  burning it .. how can i make a cd of ubuntu with out ruining i t?

---

### Post by boomdiddly on 2008-04-19
> **cward002 said:**
> Did you download the server image or the desktop image? The server image does not have a graphical desktop installed by default. You have to type the following commands at the prompt to install the graphical desktop
 
```
sudo aptitude install ubuntu-desktop
```

 or for Kubuntu you have to type 

```
sudo aptitude install kubuntu-desktop
```

hope this helps

Colin

Thats a very good point Colin could well be the server image!

---

### Post by boomdiddly on 2008-04-19
> **Dominicanboy260 said:**
> well now i see that the cd had about 56 errors and i cant figure out wat i did wrong during  burning it .. how can i make a cd of ubuntu with out ruining i t?

Burn it as a normal CD :lolflag: it's a standard ISO and burns fine

---

### Post by Dominicanboy260 on 2008-04-19
o no i have the desktop image but  as i said earlier thanx everyone for all the help .. now my problem seems to be the downloading process because i checked the cd for errors and it it returned 56 errors .. HOW CAN I BURN THE ISO TO A CD WITHOUT ERRORS ?

---

### Post by Pumalite on 2008-04-19
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less on CD-R, check CD integrity after burn and before install

---

### Post by Dominicanboy260 on 2008-04-19
allright will do hopefully it works this time .. :) thanks

---

### Post by Pumalite on 2008-04-19
Good luck.

---

