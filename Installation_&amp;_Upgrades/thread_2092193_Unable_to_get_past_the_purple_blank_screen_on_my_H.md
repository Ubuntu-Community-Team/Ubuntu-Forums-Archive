---
title: "Unable to get past the purple blank screen on my HP 450 Laptop"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by AmolR on 2012-12-07
[COLOR=Navy]Dear Experts,

Huh! Apologies for creating a new thread. I'm new to Ubuntu ( though I'm familiar with Linus/Solaris). This is the third day and I'm still unable to install ubuntu 12.04 nor 12.10. I searched in the ubuntu forums and found suggestions to use 'nomodeset'. However, after specifying nomodeset as per suggestions, I could only get a purple colored blank screen only (without nomodeset, its freezing at black screen). 

Could someone please suggest what else needs to be done or am I missing something?  

My laptop configuration is : Intel Core i3 processor and features 2 GB DDR3 RAM, 500GB SATA HDD, 14 inch LED HD display Intel HD Graphics 3000, Wi-Fi, Bluetooth.  

Any pointers/help would be highly appreciated. Thank you in advance! 
amol [/COLOR]

---

### Post by AmolR on 2012-12-07
[COLOR=Navy]And yes, I even tried with Live USB for 12.10. In this case, it takes me to the ubuntu cmd prompt which after few seconds goes off and black screen appears :(. Nothing works.

amol
[/COLOR]

---

### Post by mastablasta on 2012-12-07
> **AmolR said:**
> [COLOR=navy] However, after specifying nomodeset as per suggestions, I could only get a purple colored blank screen only (without nomodeset, its freezing at black screen). [/COLOR]

[COLOR=black]you can try pressing esc at the purple screen to see if there are any error messages. also i think if you really have intel GPU the thing should work out of the box without nomodeset parameter.[/COLOR]
my questions for you:
 
Did you check the md5sum of downloaded image. It has to match exaclty the one on server.
 
how did you create the Live USB ?
 
 
 
> 
[COLOR=navy]My laptop configuration is : Intel Core i3 processor and features 2 GB DDR3 RAM, 500GB SATA HDD, 14 inch LED HD display Intel HD Graphics 3000, Wi-Fi, Bluetooth. [/COLOR]

If intel HD 3000 is indeed your only card it is well supported in linux and should work fine.

---

