---
title: "Restricted Drivers Manager."
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Vj_Freak on 2008-09-28
Hi , ive installed Intrepid and have upgraded the system to the latest using update manager. I am not able to install the driver for my Nvidia GeForce MX 4000 graphic card. When i click on Download and Install , It downloads the file and then nothing seems to happen.
Ive tried downloading the binary from Nvidia's site but it fails to compile the nvidia kernel it needs for proper functioning. Im clueless.

What should i do ? Is this a bug or am i destined for this ? 

Thanks.

---

### Post by ansorg on 2008-09-30
the action takes quite a while as I just experienced on an old Dell notebook; it is downloading and compiling source code in the background while the progress meter remains at 0% ...

Try to run 
top
in a terminal to see what is happening in the background. You should see some ld, cc and such processes

---

### Post by kayvee on 2008-10-28
Hello,
I also have MX 4000 graphics card installed on my desktop. I recently upgraded to Intrepid and lost 3D acceleration. Now, when I try to check if restricted drivers are available for my graphics card by going to System > Administration > Hardware Drivers, my computer does not find any hardware that needs restricted drivers. Were you able to fix your problem? If yes, how? Is there any other solution for this issue?

---

### Post by solitaire on 2008-10-28
Their is an issue with the latest version of "Xorg" and some of the Nvidia drivers.

I'm afraid we'll have to wait for Nvidia to release compatible drivers.

---

