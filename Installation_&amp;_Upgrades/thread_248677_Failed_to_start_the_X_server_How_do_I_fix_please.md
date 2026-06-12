---
title: "Failed to start the X server? How do I fix please?"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by alanmzifa on 2006-09-01
Hi, I've just installed Ubuntu 6.06 on an old Dell Laptop I bought which came with no OS. 

As the laptop has no floppy or cd drive I had to install Ubuntu by putting the drive in my desktop p.c. temporarily. I imagine that has something to do with the error message.

I've got a blue screen with an error dialogue saying **"Would you like to view the X server output to diagnose the problem?"**.

Can someone give me some directions on ehat I do next?

Thanks

---

### Post by Omnios on 2006-09-01
Try using 
```
sudo dpkg-reconfigure xserver-xorg
```
either from the command line or from recovery mode.
 It is a turtle like graphics config program for configuring xserver. This should auto detect your settings for the lap top.

---

### Post by ahaslam on 2006-09-01
As it was installed on a different machine, have you tried reinstalling the xserver (sudo apt-get install xserver-xorg --reinstall)?

Tony.

PS. The advice from Omnios should work, with out reinstalling x. I couldn't remember that command ;) - I spent some time googling, but gave up :rolleyes:

---

### Post by alanmzifa on 2006-09-01
thanks, all.

I entered that in command line but although I selected auto detect I ended up having to answer a whole laod of questions.

Yhe laptop has now boted through splash screen however to full OS and I'm downloading updates as we speak.

If some things need to be changed, like the keyboard keys or layout wrong for example, how would I go about doing this. Is it a matter of entering what you told me in command line in a terminal again?

Ta

---

### Post by Malta Soron on 2006-09-06
Yep.

---

