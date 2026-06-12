---
title: "How to reinstall Ubuntu with a Home dir on a seperate partition???"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by akechi on 2006-07-05
Hi all,

Im going to reinstall Ubuntu and I just wanted to know how to go about it with my Home DIR already on a seperate partition.  I had heard that it was good to do so I would not lose my data if i had to reinstall.

When i start the installation and get to partitions, do I point it to my already created Home DIR?  Or will that overwrite whats on that partition.

Im pretty sure i read somewhere that I would have to move the DIR to another drive, do the install, then move it back and create the user?

I've basically been playing around with my install and have added way too much stuff and broke my wireless with too many instances of ndiswrapper.

One more question:  is it possible to save a kernel i compiled and just directly apply it the the fresh install, or do i need to compile it again?

Thanks for any help

Ron-

---

### Post by aysiu on 2006-07-05
This should help you out, especially the part toward the bottom about mount points:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Bottom line, though--you want to mount your /home partition at /home and choose **not** to reformat it. Then mount your / partition at / and choose **to** reformat it.

---

### Post by akechi on 2006-07-05
OK, gotcha.  It's been awhile since i've had to reinstall so i was not sure if i could just point it to /home and not reformat.

When i create the user, I just put in what i normally use and just point it to my home dir?

---

### Post by aysiu on 2006-07-05
Yes, use the same username.

---

### Post by akechi on 2006-07-05
Alright, got it now.   Would you or anyone else know if I can keep my compiled kernel or would I need to re-compile it again.   Thats kinda where my wireless broke.


EDIT:  I was using a vanilla kernel 2.6.17.3 - it was very nice, it actually enabled all of my usb ports on my notebook 
(Compaq Presario V255us) and the hibernate, suspend, and shutdown worked flawlessly.  Also, my fn keys all worked properly.  I was able to dim my screen to save battery life. (which for me is pretty horrible in Ubuntu compared to Windows XP)

---

### Post by aysiu on 2006-07-05
Having never compiled a kernel myself, I don't know. Someone else here probably can tell you, though.

---

### Post by akechi on 2006-07-06
I got everything working now. I reinstalled the OS while keeping my /home.  I also compiled the latest ndiswrapper with broadcom 4318 drivers and everything is ok. Now i just have to get my video up and running and im ok.


THIS THREAD CAN BE CLOSED IF NEED BE!

Thanks for all the help.

---

