---
title: "[SOLVED] What Is The Best nVidia Driver For GeForce2 Integrated GPU - Gutsy Gibbon"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Bruegger on 2007-10-28
Hi Folks,
Have just upgraded to Gutsy Gibbon 7.10 and would like to know what driver would be best for nVidia Geforce2 integrated gpu card.
The 9639 drivers never worked for me earlier in Feisty Fawn and i had to use 8776 drivers. 
PLease advice/suggest.

---

### Post by fallout75 on 2007-10-28
I second the question for a GeForce 2 MX400
Desktop Effects do not work with restricted driver even installed

---

### Post by gganitis on 2007-10-29
Fallout, I have the same card and the same problem. Many have the same problems with many nvidia cards.

It's not solved, but have a look at this:
[http://ubuntuforums.org/showthread.php?p=3666120#post3666120](http://ubuntuforums.org/showthread.php?p=3666120#post3666120)

---

### Post by Bruegger on 2007-11-02
So isnt there any way the 9639 or some driver could be modified for our cards in gutsy?
I was using the modified drivers 8776 in feisty and was able to use beryl pretty easily.
Cant that same be donw some way in Gutsy?

---

### Post by gganitis on 2007-11-05
My problem with nVidia GeForce 2 MX 400 solved. Have a look here:

[http://ubuntuforums.org/showthread.php?t=592837&page=4](http://ubuntuforums.org/showthread.php?t=592837&page=4)

---

### Post by Bruegger on 2007-11-06
Giganitis,
Let me run envy and see if it works the same for my geforce2 gpu too.
Happy you could get your problem solved.

Cheers!

---

### Post by waterloo_sunset on 2007-11-06
I have the same A7N266 mobo with the integrated geforce2 gpu. Tried Envy as a last resort, but no joy. Got the nvidia splash screen and then it hangs, or i get a blank screen. Any other stuff we can try? 

Have you tried using the legacy driver Bruegger?

---

### Post by Bruegger on 2007-11-08
Waterloo,
Installed the nVidia driver version 96.43.01 for Geforce2 Integrated GPU.
Used Envy 0.9.8 to install the nVidia driver. It installed 96.43.01. Installed the linux-restricted-modules-2.6.22-14-386 as the installation used to freeze. Installation completed. Let Envy edit your xorg.conf file. Restart.
Enable the restricted driver manager to use nVidia for 3D acceleration , restart and you are on.
Have some small issues, like using mouse clicks to paint the screen, but they are minor at the moment. Still testing it out. 
WIll see how it goes. Can you in the meantime try this out and see if it works for you?
Cheers!

---

