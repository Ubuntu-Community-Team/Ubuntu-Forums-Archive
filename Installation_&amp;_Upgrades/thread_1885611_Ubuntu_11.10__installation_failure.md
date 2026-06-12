---
title: "Ubuntu 11.10  installation failure"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by younesgeorge on 2011-11-23
Hi,
 

I am not able to install UBUNTU 11.10 on my new Toshiba Qosmio F7553D.
It is a Intel® Core™ i7-2670QM processor, with a NVIDIA® GeForce® GT 540M (3D Vision) and a 1GB GDDR3 discrete graphics memory.



The technical discription of this laptop can be found here [http://us.toshiba.com/computers/laptops/qosmio/F750/F755-3D350](http://us.toshiba.com/computers/laptops/qosmio/F750/F755-3D350)
 I tried the CD installation, but right after the restart I am taken to a black page with writings such as:
 [           4.977467] sd 0:0:0:0:  [sda] Mode Sense: 00 3a 00 00
...
...
...
[           5.322385] usb  1-1.4: new high speed USB device number 3 using ehci_hcd
[           5.777889] usb  1-1.4: new high speed USB device number 4 using ehci_hcd
 

and everything stops after this last line, it is like the page freezes. I tried the wubi.exe windows installer, same thing. Tried version 11.04, same thing.

 

Just for the fun of it, I tried installing the same version, 11.10, on my  Samsung notebook 1GHz processor (which I use strictly for presentations)  and was done in 10 minutes.
 

I really can use some help, I use UBUNTU for work and I am freaking out.
 

Sincerely yours,
George Younes

---

### Post by Rubi1200 on 2011-11-23
Hi and welcome to the forums :)

You can try using nomodeset.

See post #1 here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by younesgeorge on 2011-11-26
Thanks a lot. I almost gave up on the laptop actually. Choosing the nomodeset option worked perfectly.
Thanks again.

---

### Post by Rubi1200 on 2011-11-26
No problem, you are more than welcome and I'm glad things worked out for you :)

Please mark this Solved using the Thread Tools near the top of the page.

---

