---
title: "How can I test the binary nvidia driver LiveCD?"
date: 2009-06-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-06-18
Hey guys -- I've found a bug that is a regression somewhere in the Xorg/nvidia chain from Intrepid to Karmic.

I want to file a good bug report and make sure that the problem exists in all those versions (but not in Hardy). What is the easiest way to test in LiveCD/LiveUSB? 

jockey wants to reboot, and I assume that means that I will lose any drivers I install... so can I just install the driver and restart Xorg?

Any documentation or help would be helpful. :)

---

### Post by ranch hand on 2009-06-18
You should be able to do that on the LiveCD.  I have never done it but I have "installed" other things.  They just go on your ram.

---

### Post by ronacc on 2009-06-18
restarting x should do it , I never tried it from a livecd but have done that many times from an install .

---

### Post by JohnJackson on 2009-06-19
You could use a live USB with persistent storage

---

### Post by ranch hand on 2009-06-19
My box uses an ATI card but I was fooling around with grub2 on 9.10A2 with the live CD.

It offers me the option of using the restricted driver.  Just go right ahead and test with the LiveCD.  It will work fine.

---

