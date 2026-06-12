---
title: "Karmic Alpha 5 Install - No Display Found"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by integral18 on 2009-09-03
I am trying to install Karmic Alpha 5 on a Dell Studio 14z.
I am installing this from a usb created with unetbootin.

It takes me to the command prompt fine but when I try to startx...

I get the following:
(EE) no devices detected fatal server error:no screens found


In the logs, the *NVIDIA* GeForce 9400M is not supported.  This also happens in 9.04 but it continues to boot and then I just install the Nvidia driver.


Thanks for any help or suggestions.

---

### Post by integral18 on 2009-09-04
I did not have the usb a persistent install and thus there was no way to install the nvidia driver to bring up the graphical install screen.

So the easy work around is just to use the alternate install cd and then login into (you will be using only the terminal because startx has failed and then just sudo apt-get install nvidia-glx-185 or the newest version.  Don't forget to do nivdia-xconfig restart and enjoy Alpha 5.

---

