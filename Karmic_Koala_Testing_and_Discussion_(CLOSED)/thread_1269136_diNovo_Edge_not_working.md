---
title: "diNovo Edge not working"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lepy on 2009-09-17
So, after the Sept 15th show-stopper bug and a few others, I decided to do a fresh install of A6. Now I have another show-stopper: at the login screen, my Logitech diNovo Edge has stopped functioning.

In A5, the keyboard worked right out of the box. Replugging the dongle does not work either (as it did in Jaunty, before using the fix mentioned here: [http://ubuntuforums.org/showpost.php?p=6390002&postcount=6](http://ubuntuforums.org/showpost.php?p=6390002&postcount=6)).

Also, single user mode seems to not be working. If I add single or S options in grub, it takes me straight to the login screen.

Any ideas?

---

### Post by Lepy on 2009-09-17
Scratch that, upon further investigation my other logitech wireless keyboard does not work either. However, looking at the logs, the devices are recognized. I just can't type in my password to get to the desktop!

I installed from the alternate disc, did not install a boot loader, and manually updated grub from inside my jaunty install.

---

### Post by cleentrax on 2009-09-22
I have a diNovo Mini keyboard, and it has worked with jaunty and intrepid, but it is not working with karmic. I am using the dongle.

---

### Post by Lepy on 2009-09-24
Since I have a dedicated partition to testing, I just reinstalled karmic. 

I quickly ran through the keyboard detection instead of selecting "us" right of the bat, and my diNovo started working.

Updates must have fixed it. Otherwise, A6 has been running very well the past few days.

---

### Post by anders_c_ on 2009-10-05
i can get my diNovo to work if i connect using the button on the adapter, but karmic wont even recognize it as a bluetooth device, so i cant connect my phone...worked in Jaunty and works in Fedora 12 beta

---

### Post by huwshimi on 2009-10-05
I have a diNovo edge. I installed Karmic beta and it is working completely fine. Didn't have to do anything (in Jaunty I had to change a setting to make it connect at startup).

---

