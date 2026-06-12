---
title: "Monitor Out Of range"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Hellberg on 2006-11-06
Hi 
I’m having trouble running Ubuntu live cd. I got the start up screen were I chose res. and language. and then live start’ up. after a while my monitor says “out of range” this happens when live cd is booting up. I've tryed all the resolutions on the startup scrren and nothing help. I don’t know watt to do. I hope that someone out there can help me. and tell me how i can solve this problem. Please.

My hardware 

Motherboard ESC K7SOM+ and onboard Grafik SIS962

I,m from DK and my English is probably not the best.
Bo

---

### Post by taurus on 2006-11-06
Do you plan to install Ubuntu on your computer or do you just want to check it out, running it off the CD--LiveCD?

If you want to install it on your computer, then try using the alternate CD.

But if you just want to check it out before you commit yourself to it, then see if you can get to a terminal by pressing <Ctrl><Alt>F1 (or F2).  Then at the prompt, type

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Hellberg on 2006-11-08
Hi
Thank's for the reply, I want to install ubuntu. but first i will try your hint and reconfigure Xserv-xorg. and then i robely will bee back with some more questions.

Thanks for now

---

### Post by Hellberg on 2006-11-15
Hi

I haved solved the problem with Reconfigure Xserver and it helped thanks for the help

---

