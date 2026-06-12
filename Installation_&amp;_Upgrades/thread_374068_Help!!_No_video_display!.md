---
title: "Help!! No video display!"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by tekpunk on 2007-03-02
I really need your help guys.  I'm installing Ubuntu on a Dell xps 400, and I can't see anything!  The install screen shows up, I click install, the kernel loads, then the Unbuntu loading screen comes up for a while, then my monitor just says "Unable to display analog input".  I've tried in the safe mode, and it still didn't work.  I'm running a Intel Duo 3.0 ghz, 1 gb ram, with an Nvidia 6800.  Unfortunately Dell designed this computer "so well" that I do not have a default video input from the motherboard, only from the video card.  Any thoughts or suggestions???

---

### Post by Kateikyoushi on 2007-03-02
I would try what this post suggests, just change ati driver to nvidia, you could also use the alternate install cd which runs in text mode, that might work.

[LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by tekpunk on 2007-03-02
Ok, I got it to work by changing the resolution to 1024x768x32.  It's working fine...except I can't see my mouse pointer...any other suggestions?

---

### Post by Kateikyoushi on 2007-03-02
I looked around but could not find anything helpful, this is the first time I hear this. Can you click buttons etc just the pointer missing ?

You could try to install via keyboard using Tab and enter or wait if someone has ideas.

---

### Post by tekpunk on 2007-03-02
Only the pointer is missing.  It's pretty annoying.  Thanks for your help so far.

---

### Post by tekpunk on 2007-03-02
ok...now i really need help.  I installed Ubuntu (i was using the livecd before) and now I can't see anything again.  I have to run the livecd to see any display at all.  What now?

EDIT:  So..i basically gave up, reinstalled XP, but I really want to try ubuntu.  Can anyone figure out wtf is wrong or what I should do differently?

---

### Post by tekpunk on 2007-03-02
so yeah..any help would be FANTASTIC.

---

### Post by Prometheus.172214 on 2007-03-02
Couple things that I need to know. 
1) Can you post the Service Tag for your XPS 400. I can check the system specs from support.dell.com 
2) When the system starts and you see the Dell logo, tap the function key F2 to enter the system setup. Use the keyboard to locate the performance tab and then hit enter. Check if there is a Hyperthreading / Multi Core Option. Disable this or these if they are enabled. We can enable them once the O.S. is up and running and maybe if needed run a different kernel later.
3) What monitor are you using on this system. A lot depends on the optimal resolution of the video card and the monitor. The installation may use a different resolution.

---

### Post by tekpunk on 2007-03-02
i installed it already, but i keep getting the "no analog input" display.  the livecd works when i press f4 and change the display to 1024x768x32.  but i can't run ubuntu after i install it.  i'm trying to find a way that i can correct the problem from the recovery mode in the terminal, if that's possible.

---

### Post by Kateikyoushi on 2007-03-03
Try to reconfigure Xserver from the recovery terminal so you use the 1024X768X32 resolution.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tommcd on 2007-03-03
Perhaps you could try the alternate CD. At the end of the install process it asks you to choose the screen resolutions you want. It has been a while since I used the live CD, but if I remember correctly the live CD does not ask you for screen resolutions. If the screen resolution is the problem this may help.

---

### Post by tekpunk on 2007-03-03
THANK YOU!! I really appreciate your help.  It finally worked, now I think I just have to update the nvidia driver.  Thanks a lot!

---

