---
title: "HP Pavillion dv9774ca Webcam Problems"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by matthew_leonard on 2008-03-20
I just bought a new laptop. It is a HP pavillion dv9774ca, I was able to get most things working on it so far but have been unable to get the onboard webcam to work. it is on the usb2 bus and it is a chicony electronics webcam. every time i reboot and try to get information on the device it seems to be on a different bus and with a different device id.

i have tried almost every driver/solution that i have found online but still nothing seems to get the camera to work. i was wondering if anyone had any ideas.

i am still fairly new to linux, i used to use it back in day but i am not totally lost....

any help would be appriciated

---

### Post by linuxwizard on 2008-03-20
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by matthew_leonard on 2008-03-24
so i do have the drivers installed and it works in ekiga but i  cannot seem to find another program that actaully makes the webcam work.... do you have any suggestions for an easy to use webcam program, preferably one with a gui...

---

### Post by linuxwizard on 2008-03-24
Which apps have you tried ? You might look at Camorama, Cheese they are in the repo.

---

### Post by matthew_leonard on 2008-03-24
i have tried camorama, cheese works fine now

do you have any suggestions for a msn compatible chat program that supports webcam? i am using pidgin now...

thanks for all the help

---

### Post by linuxwizard on 2008-03-24
Look at Amsn also in repo.

[http://www.amsn-project.net/](http://www.amsn-project.net/)

---

