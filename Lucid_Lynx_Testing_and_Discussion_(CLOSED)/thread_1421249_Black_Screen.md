---
title: "Black Screen"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brimondyl on 2010-03-04
Hello, I Have a VIA Cloudbook. Everything worked good with Alpha 2 but Alpha 3 gives me a black screen after grub. If I hit 'enter' then put in my password I can hear it login. Wondering if somebody has a workaround or would know whats causing this? Thanks

---

### Post by Ibidem on 2010-03-04
nomodeset?  
You might try adding nomodeset to the boot parameters...

---

### Post by brimondyl on 2010-03-04
No, I tried that and it has no effect

---

### Post by brimondyl on 2010-03-04
Another thing the Live Cd works perfect. How would I go about finding the settings of the Live Cd and copy it to the installed version?

---

### Post by brimondyl on 2010-03-04
No one?

---

### Post by Lollerke on 2010-03-04
Press CTRL+ALT+F1 then CTRL+ALT+F7.

---

### Post by brimondyl on 2010-03-05
> **Lollerke said:**
> Press CTRL+ALT+F1 then CTRL+ALT+F7.

That does nothing unless I have it plugged into a external monitor. Even then I cant start X because it says its already running. I sure wish I could figure this out, It makes the Cloudbook one fast little netbook

---

### Post by VMC on 2010-03-05
> **brimondyl said:**
> Hello, I Have a VIA Cloudbook. Everything worked good with Alpha 2 but Alpha 3 gives me a black screen after grub. If I hit 'enter' then put in my password I can hear it login. Wondering if somebody has a workaround or would know whats causing this? Thanks

It might be **plymouth**. Try removing it , then see if it improves. If not you can always re-install it.

---

### Post by brimondyl on 2010-03-05
I removed Plymouth, still the same. I did find out that if I am by a bright light I can sort of see things on the screen but I cant brighten it

---

### Post by VMC on 2010-03-05
What does the VIA Cloudbook have for video card?

Also when **grub** menu comes up, if you edit and at the end of the linux line add the word ***single*** to see if you get to a recovery mode.

---

### Post by brimondyl on 2010-03-06
> **VMC said:**
> What does the VIA Cloudbook have for video card?

Also when brun menu comes up, if you edit and at the end of the linux line add the word ***single*** to see if you get to a recovery mode.

It has the VIA UniChrome Pro IGP (VIA VX700)

---

### Post by brimondyl on 2010-03-06
I Checked and their isnt any errors in the boot log. I can't be the only person with a VIA chipset. How would I go about checking what the configuragion is when using the live cd?

---

### Post by kurros on 2010-03-06
Dont know if its the same issue but I get this sometimes with my intel video laptop. I have to Ctrl+Alt+F2, login, and run *sudo /etc/init.d/gdm restart*

---

### Post by brimondyl on 2010-03-08
I would try that but I cant see the screen to do anything.

---

### Post by ViperScull on 2010-03-08
Your are not alone and i don't think it has anything to do with VIA.

Same here:

[http://ubuntuforums.org/showthread.php?t=1424261](http://ubuntuforums.org/showthread.php?t=1424261)

---

### Post by brimondyl on 2010-03-09
I dont get it? X is running, the screen is just so dark that you can't make anything out. I tried to take the xorg.conf from my Karmic install and put it in Lucids but that did nothing. I tried blacklisting the VIA driver that did nothing.

---

