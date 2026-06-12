---
title: "How to download packages after minimal installation using Huawei 3g USB modem"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by saransaleen on 2012-05-18
Hi everyone, my computer is a compaq presario 12XL307 with 64MB ram and a 10 GB HDD. I decided to do a minimal install because I have only 64MB of ram and I really don't want it to be slow. I installed looking at a tutorial on the net. HEre is the link: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
After installing the tutorial told to prepare for a graphical and to type the command sudo apt-get install xorg and it will start downloading from the net. Problem is that I do not have a ethernet cable that you just plug in and you are connected to the internet. I have a huawei 3g usb modem that you have to install a software first and only then will it connect to the net. Now I have no idea how to connect to the internet with minimal install as it shows me no way to actually install the usb modem's software. Can someone tell me how to install the software through the command line prompt in the ubuntu minimal install? Also I am a complete newbie and have no idea what so ever to do so please be considerate to give all the instructions required. 
Regards,
Sam

---

### Post by mikewhatever on 2012-05-18
Hi, and welcome to the forums. 

1. With only 64MB of RAM, you most certainly don't want to install the graphical environment. It won't work. You'll need about twice as much (128MB) for a lightweight window manager in Ubuntu to work decently, not to mention applications.
Perhaps you could try TinyCore, Feather Linux or Slitaz instead.

2. Is the modem recognised? Are there native Linux packages to install? Can you post links.

---

