---
title: "Strange problem installing LINUX along with windows XP"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by pavan_85 on 2010-03-21
Hi all,
I have installed windows xp (service pack 2) on my pc.
later i formatted a partition (drive E:) and installed ubuntu linux 8.04.
I have provided 2gb space for SWAP partition and remaining for root (/).
I have done this manually. 
Installation was completed, and ubuntu asked me to reboot the system. I did so.

Now comes my problem.......
I am getting some DHCP connection or some thing weird.......
after that i am getting a message ......and with a message asking me to press any key.....
the same thing is coming even after restarting the system....i am unable to see both windows and linux now!!!!!!!!!

I am totally confused......i dont know what to do???????
please help me out with this............

--pavan

---

### Post by abohsin on 2010-03-21
very difficult to judge. Please give us more details:
1. Did u perform a full install or wubi inside windows?
2. At which stage are you getting this message?
3. What is the message?

Appreciate giving us further details to further assist you.

---

### Post by pavan_85 on 2010-03-21
hi,
Yes...i performed full installation, the error message was coming after installation is completed and system is asked to reboot. When i rebooted i was not getting a screen (as i am expecting) asking me to load windowx xp or ubuntu.
All i was getting was:

DHCP ...../
check failed
please use any boot cd and press any key.....

this keeps on repeating.....even after rebooting several times......

Pavan

---

### Post by Sef on 2010-03-21
How are you connected to the internet?

---

### Post by pavan_85 on 2010-03-22
yeah.......i got internet connection through my windows xp os.
Does it create some problem????

---

### Post by abohsin on 2010-03-22
Pavan,

It seems that your computer is making an attempt, for some reason, after initial setup to connect to the internet, perhaps updating apt repos or something, i don't know. One suggestion, if this error occurs when you are connected to internet, disconnect it during the installation.

One more question, why are you installing 8.04? You may as well go for 9.10, may be there is a problem with 8.04 dual booting with XP, never tried that combination before.

But not to deviate away from your case, if the error happened while disconnected from internet, connect your machine; if it happened while your machine was connected, then disconnect it. It is just that I don't seem to remember how the 8.04 version went during install.

Update us once completed.

---

### Post by mkvnmtr on 2010-03-22
Did you by chance press the any key? Or maybe put in a boot cd and then press the any key?

---

