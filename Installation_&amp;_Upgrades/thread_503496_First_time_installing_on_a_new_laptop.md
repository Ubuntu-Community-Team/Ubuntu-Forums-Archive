---
title: "First time installing on a new laptop"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by Exul on 2007-07-18
Hey, im brand new to Ubuntu and i thought i would give it a try.  So i downloaded it off ubuntu.com and burned it to a CD.  (The alternate CD Version).  My laptop is brand new and is using the latest.  (Nvidia Gefroce 8400M G, and Intel Wifi 4965AGN).  I installed ubuntu and when i loaded it up for the first time, i get the message 'X server failed'.  I read around and tried the command 'sudo apt-get install nvidia-glx'.  I get a message to insert the Ubuntu Feisty Fawn CD.  I insert the CD but nothing happens.  Any suggestions so i can get my graphics card working, and also get drivers for my network card.

---

### Post by Turboaaa2001 on 2007-07-18
You seem to have several problems. All new notebook computers are Vista only. That doesn't mean you can't install something else just that the thought into the hardware is only for Vista.

I would first suggest not using the alternate cd but use the live CD to see what you can get running. Plus when it asks you for the disk I think it's asking for the CD I just mentioned.

As for your WiFi card, that will not work until you get the OS working properly. I would suggest plugging directly to the net with physical cable to get updates (thankfully the updates are small and really quick to download and install) and then work on getting the WiFi to work.


NOTE: I'm still getting my Ubuntu legs so take what I say with a grain of salt.

---

### Post by Exul on 2007-07-18
Hey, thanks for the reply.  I tried installing using the Live CD but i got some tty error.  'cant access job control' or something like that.  So then i used the alternate CD.  Anything i can do to fix my graphics card problem?

---

### Post by misfitpierce on 2007-07-18
Everytime I ever had a xorg error i did this from root line

sudo rm -r /etc/X11/xorg.conf and then type reboot

then at start if no auto start of gui type startx ... Try that?

---

### Post by Exul on 2007-07-19
i think its because i have a new graphics card, and its not natively supported.  I might be wrong im a completely new to Ubuntu, and am not yet familiar with it.  Is there any way to download drivers for this put them on a USB drive or CD and load them using the command line.

---

### Post by Exul on 2007-07-20
Anyone know of any fixes?

---

### Post by Pumalite on 2007-07-20
How did you partition?. If you have Vista in your laptop, then you HAVE TO partition from WITHIN Vista. Otherwise Vista will not allow you to install anything in that hard drive.

---

### Post by Exul on 2007-07-21
I originally had 2 partitions set up.  One wit h vista installed on it, and the other blank.  When i installed ubuntu, i deleted the 2nd parition (using the ubuntu installation cd) and used that free space to install ubuntu.

---

### Post by Pumalite on 2007-07-21
Did you use the Vista partitioner?

---

### Post by Exul on 2007-07-21
I dont think so.  How do i access the vista partitioner.  Like i said before i set up my partitions and everything using the ubuntu CD.

---

### Post by Pumalite on 2007-07-21
I don't know Vista ( I don't want to know it), but I know you have to use the Vista partitioner. It must be in Administration or something like that.

---

