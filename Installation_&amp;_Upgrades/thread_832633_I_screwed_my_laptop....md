---
title: "I screwed my laptop..."
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by cespinal on 2008-06-17
hello guys... 

I just did something stupid... I downloaded the last update, and restarted my laptop before the installations were complete... 

now: my screen resolution went straight to hell... 
Im an not able to fix things because, according to the system, i need to run a couple of commands to restore de drivers as a superuser and I dont know what does that mean!.. I dont know how to run commands as root either.. 

also, synaptic manager wont work...

help on this POR FAVOR!!!!!!!!

---

### Post by Pumalite on 2008-06-17
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
(One at the time)

---

### Post by wolfen69 on 2008-06-17
running as superuser means typing "sudo" (without quotes)  before any command, such as- sudo apt-get install vlc.

for the video problem, run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i'll follow your progress and help if i can.

---

### Post by cespinal on 2008-06-17
thank you very much por the fast answers!!! got it right away!! :D 

now, it downloaded a .19 version of the kernel which is conflicting with the .18, which one of the bunch of files in the synaptic manager is the .18 so I can delete it?

---

### Post by Pumalite on 2008-06-18
Paste here the entire output (error message)

---

### Post by cespinal on 2008-06-18
There is no error message, 

When a new kernel version conflicts with the older one, you can get some symptoms like: 

-text on splash screen and when closing ubuntu
-taskbar disappears when you click over the log out button
-flash movies wont play 
-back button wont work on firefox
-it takes ages for the system to connect to the internetzzzz 

I got exactly the same issues when I updated from the .17 kernel to the .18 one some weeks ago. The point is that I need to find out the old kernel in synaptics but there's so much files in there!! :lolflag:

Once I get rid of the old one, ubuntu comes back to normal (I hope)

---

### Post by Pumalite on 2008-06-18
Remove from Synaptic>linux-image>linux-image-2.6.24-19-generic-2.6.24-19.33
Do it while booting with the previous kernel.

---

### Post by cespinal on 2008-06-18
Cant I just do it the other way around? 

Loading .19 and then going to synaptics to erase .18?

---

### Post by Pumalite on 2008-06-18
I thought you said 19 was giving you problems.

---

### Post by cespinal on 2008-06-18
I apalogize if I didnt explain myself correctly. 

I meant that, to my experience, a new and an older kernel conflict with each other. Deleting one of them (I usually delete the older) brings back everything to normal.. .

---

