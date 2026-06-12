---
title: "Help With Hardware Driver Fail During Livecd Start"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by bobbymilla on 2007-09-15
Hello all... i'm new to linux and of course ubuntu, i have seen it in action and it is fantastic and i wanted to install it on my machine. So i have downloaded the Ubuntu iso and booted into it and during the livecd "quiet splash" enabled startup it will freeze and reboot without warning. During the safe graphics startup it will show the splash but during the screen will fragment (kinda break up and be pixelated and show the top and bottom to be a broken magnification of the bar in the center) then this reboots also...
So i have tried the 64 bit version, the alternate version  and turned the "quiet splash" option off, when i do this i see loads of commands come up and then it stops at "Loading Hardware Drivers" then it goes crazy and starts displaying loads of commands... i have written down what i saw and it kinda goes like this if it is any help:
"RIP [<ffffffffff 00267b09>] _SPIN_LOCK_BH+0x9/0x20"
(then some more codes beginning with f s)
"Kernel panic - not syncing: aieee killing interrupt handler!!!"
then there is just a blinking cursor and a huge staring contest that you know your going to lose...
even after install with the alternate CD it will not boot
I have searched far and wide for a solution but to no avail... i have attached by DXdiag txt file if it helps and i made a video of the screen after the failure and if you want i'll give you the url...
if you have any info on how i could solve this please help...
thankyou in advance, Robert Miller
P.S. sorry for the zipped dxdiag file... it was too big to be uploaded as a txt file so i zipped it and uploaded... sorry for any inconvenience...

---

### Post by Pumalite on 2007-09-15
What are you specs?

---

### Post by bobbymilla on 2007-09-15
thanks for the help so quickly...
i have **2** pentium 4 @ 3 ghz each
1 gig of ram
a Nvidia Geforce 7600 GS
and a C-Media sound card
if you need any more info don't hesitate to ask
thanks in advance Robert Miller

---

### Post by Pumalite on 2007-09-15
It looks like you should be able to install anything in that system. I'm sure that when you say 'I have 2 Pentium 4' you don't mean Core 2 Duo, so this is your own personal arrangement. Do you care to elaborate?

---

### Post by bobbymilla on 2007-09-15
well i bought the system from an ebay shop and i was told it had 2 pentium 4s so it was not made by a large company such as dell etc. I realy do not know about the configuration of the processors so i really couldn't tell you much about them. Do you think this may be a problem?

---

### Post by Pumalite on 2007-09-15
Your hardware otherwise is A-OK. Try the Alternate CD
Here is a collection of boot options used to avoid hardware problems:[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

---

### Post by bobbymilla on 2007-09-15
i have tried the alternate cd but with no luck... would you like me to use the boot options you recommended with the alternate or main cd?!

---

### Post by bobbymilla on 2007-09-15
p.s. i have read the links you gave me but i am not good with linux ... this is my first time using it and i have no clue which boot options to implement... could you possibly recommend some, if not this is fine 
thankyou for your help, Robert

---

### Post by Pumalite on 2007-09-15
You can try them with the Live CD. Good luck.

---

