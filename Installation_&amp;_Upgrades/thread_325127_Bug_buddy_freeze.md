---
title: "Bug buddy freeze"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by qwondre on 2006-12-25
Hi, noob here, I downloaded super grub so I could do multiple os's and somewhere as I was trying to burn supergrub .iso I suffered a crash with bugbuddy telling me that it had collected the specs on my machine and was preparing to send it in.................and then I wait.](*,)  With bug buddy window open, nothing else is operable, I had to get out the cd that I downloaded and burned to be able to get online. Ive been using edgy for a couple of months now. Another thing that I noticed lately is that my screensaver freezes up after some time and I have to reboot. I dont know if the two are related or not. I did find out that I cant remove bug buddy!  All I do is sit and wait for something that never happens.  :-k         Thanks for any help!
Correction: I started using edgy the first of Dec, Ubuntu for two months.

---

### Post by bulldog on 2006-12-25
Why can't you remove bug-buddy?
Go to your synaptic packet manager and search for bug-buddy and mark it for removal.
Should work and if not try ```
sudo aptitude remove bug-buddy
``` and see if you get some error messages.

---

### Post by qwondre on 2006-12-25
Thanks for answering bulldog! I tried to get rid of bug-buddy using synaptic but I was told that to remove it, I would have to also remove Ubuntu-desktop.

And this is what I got when I used the terminal:

buntu@ubuntu:~$ sudo aptitude remove bug-buddy
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Im not even sure what that is saying.

Thanks!

---

### Post by bulldog on 2006-12-25
It means in simple translation,you'll have your synaptic not closed.
You can use one instance of a packetmanager the same time,so you'll have to close the other one.

But if bug-buddy is only remove able with your whole desktop,you can do so and reinstall it afterwards using ```
sudo aptitude install ubuntu-desktop
``` but I'm not sure if bug-buddy is installed as well again.

---

### Post by qwondre on 2006-12-25
Hey bulldog, thanks a lot! Re-installed the desktop without a problem, bug-buddy is reinstalled too- and thats probably a good thing! 
Once again, thank you so much.  :-D

---

### Post by bulldog on 2006-12-25
No problem,glad I could be of some assistance :D

---

