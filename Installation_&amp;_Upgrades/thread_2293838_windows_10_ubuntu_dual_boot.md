---
title: "windows 10 ubuntu dual boot"
date: 2015-09-08
forum: Installation &amp; Upgrades
---

### Post by krishnan t s on 2015-09-08
I have a relatively old HP compaq desktop which originally came with 160 gb  hard disk and 512 mb ddr2 ram. I fitted an additional 2gb of ram to my pc. In due course, the primary ram of 512 mb crashed and i had to remove it. Recently, my windows 7 install(by local computer guy) stopped working. The mouse refused to move and i couldnt even open the control panel as it started throwing some error about not having some stupid windows service. My ubuntu 14.04 which i upgraded to 14.10 and eventually 15.04 was working perfectly(mouse included :P)
 
One fine day, i decided enough was enough and installed windows 10 home(yeah screw privacy :P :P) from a bootable usb i had created using a friend's pc. I erased everything(ubuntu included) using gparted and made fresh partition tables. I then installed ubuntu 15.04 first and then installed windows 10 on a 35 gb ntfs partition i had created during the ubuntu install. Windows 10 also installed successfully and i started using it. 

The first time i rebooted to ubuntu, everything worked fine till the desktop loaded. Then all of a sudden the monitor went blank and came back with the screen distorted(nothing was visible, it was as if the desktop was showing itself many times over at the same time.Will attach pics later today) I could not understand what happened. So i thought it was a unity specific issue and so installed gnome-shell 15.04. I'm still stuck in the same issue. I dont think its a hardware issue because now ironically, windows 10 has not had a single crash since its install(i still dont like it. Its resemblance to kde 5.4 is uncanny to say the least). What could've gone wrong and how can i get back my original ubuntu? removing windows is out of question as there are no drivers for my stupid canon lbp 2900 laserjet printer on ubuntu.

---

### Post by Bucky Ball on 2015-09-08
Your Canon is supported in Linux. See [here]("http://askubuntu.com/questions/457774/driver-canon-lbp-2900"). Not sure how rigorously you researched this as that was the first link I found. :)

Sounds like you have an issue with your graphics card. Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit.

Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'. The end of the line should look like this:

> quiet splash nomodeset

Follow the instructions at the bottom of that screen to save changes and continue. Any luck?

---

### Post by krishnan t s on 2015-09-08
Thanks for the reply :)
Nomodeset seems to have resolved the graphics issue for now :)
I have tried to install the canon printer numerous times in ubuntu. Am trying the link now. Will probably take half a day to download the packages on my current internet connection(broadband, not kidding ;) ). Will post results once i am done.

---

### Post by Bucky Ball on 2015-09-08
Excellent news about the graphics issue. If you check 'Additional Drivers' and there may be third-party drivers in there, but if all is working, I wouldn't bother with them.

Yes, try with the printer and tell us how you went, but post a new thread to describe where you're at with it if it doesn't work as that issue has nothing to do with this thread and it will increase your chances of support posting a new one with a descriptive title.

If it does work, don't bother with the new thread. 

Either way, mark this thread as 'solved' by following the first link in my signature as your initial support request here is solved (this will not close the thread but will help others). 

Good luck.

---

### Post by krishnan t s on 2015-09-09
Thanks for the reply. The printer works. I have a few questions about that though. I'll open a new thread on that :)

---

