---
title: "After Kubuntu 12.04.3 install and login, only have black scree and mouse"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by Will_McDade on 2013-11-02
Hi guys

I installed Kubuntu 12.04.3 LTS and, of course, logged in. I was greeted with the small Kubuntu loading icons, then I was greeted by a black screen with a mouse (movable). After about 5 seconds the boot sound plays.

I did CTRL+ALT+F2 and got to a terminal where I did:

```
sudo apt-get update
sudo apt-get upgrade
```

and rebooted. the problem still occurred afterwards.

What can I do? It worked fine as a live USB!

Many thanks.

---

### Post by Will_McDade on 2013-11-02
I'm going to reinstall it, just to make sure nothing went wrong on that font. I'll just play kPatience to pass the time :)

---

### Post by fantab on 2013-11-02
What Graphics does your machine use?
Try [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") at boot.

---

### Post by Will_McDade on 2013-11-02
I have a Leadtek WinFast A360le 128mb agp 8x (nvidia geforce fx 5700le td). I will give 'nomodeset' a go.

---

### Post by Will_McDade on 2013-11-02
After reading the nomodeset link you provided, this is not what I mean. After a bit of googling, the problem is to do with KDE/Kubuntu/Plasma. I am not sure what to do as I can move the mouse around the screen and I can get to a console with CTRL+ALT+F(number)

---

### Post by Will_McDade on 2013-11-03
Just had a thought that it *might* be because my /home partition and swap (although i am not talking about the swap) is on another hard drive in my machine.

EDIT: IT WORKS!!!!!!!!!!! I installed Kubuntu with all directories on the same hard drive. There was an Xorg error but doing ```
sudo apt-get upgrade
``` kicked it back into shape as it installed xorg core server. Many thanks anyway! I just love KDE now :P

---

