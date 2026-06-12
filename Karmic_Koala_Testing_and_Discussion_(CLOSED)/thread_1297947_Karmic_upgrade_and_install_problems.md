---
title: "Karmic upgrade and install problems"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by namluc on 2009-10-22
"hp mini 1120" netbook

jaunty alt+f2 upgrade to karmic

caused many problems. window drawing was very very slow, the system as a whole was unresponsive, and the computer couldnt see my trackpad. 

I also lost my network connection until i did this. 

sudo depmod -a
modprobe -l|grep wl
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan

after this i had internet. 

evolution however keeps crashing, i'm not great with ubuntu, so my only solution has been to log out and log back in, as the force quit applet does not resolve the problem. 

big file downloads are difficult, the internet cuts out, or more commonly the screen goes completely black, with nothing visible at all which needed a cold boot.

the cpu was running at 50% with no apps open, and the computer would completely stall when trying to turn on compiz.

I have done a clean install on another partition, the live cd can see my wireless drivers, but after installation. the above code just results in an error message. (wl not found) or something. 

i have one system that crashes with internet access, and one system that doesn't crash that has no internet access...

for bug reporting, i'll need someones help to find the relevant info on my computer!

---

