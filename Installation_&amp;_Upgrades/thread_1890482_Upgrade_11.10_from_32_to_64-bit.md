---
title: "Upgrade 11.10 from 32 to 64-bit"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by TekMaster on 2011-12-03
I apologize if this topic has been brought up in the past, I used the search function and didn't come up with any promising results. I have recently upgraded to the 11.10 32-bit version. Now I'm thinking I should have went with the 64-bit. I do have a dual core 64-bit processor, I'm just wondering if the 64-bit width is supported by a lot of Ubuntu software? I know windows has issues when it comes to that area. Is the 64-bit version any faster OS wise? What would be the best rout to take? Thanks for the recommendations. 

TekMaster

---

### Post by oldtimer7777 on 2011-12-03
64 bit works fine.  If you have to use Ndiswrapper to wrap your wifi drivers then probably not if you have non-native 32 bit win drivers only for your wifi.  If your wifi works out of the box with Ubuntu installed, then forgetaboutit.    If you are using Citrix ICA client to connect to Citrix servers, the installation deb for Citrix ISA installs perfectly in 32bit only but also works in 64bit which requires some tweaking.. not fun..

Other than that, just 64 bit is more responsive performance wise.  I don't really notice any issues anymore that would warrant someone going with 32-bit over 64-bit today.

Here is a nice walkthrough when you want to get started:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **TekMaster said:**
> I apologize if this topic has been brought up in the past, I used the search function and didn't come up with any promising results. I have recently upgraded to the 11.10 32-bit version. Now I'm thinking I should have went with the 64-bit. I do have a dual core 64-bit processor, I'm just wondering if the 64-bit width is supported by a lot of Ubuntu software? I know windows has issues when it comes to that area. Is the 64-bit version any faster OS wise? What would be the best rout to take? Thanks for the recommendations. 

TekMaster

---

### Post by bluexrider on 2011-12-03
Ive really not seen a reason to run the 64 without having the +4Gb of ram. But its whatever you choose I suppose.

---

### Post by TekMaster on 2011-12-03
Thanks for the great feedback oldtimer, much appreciated. 

@bluexrider - When you say +4GBs of RAM: are you referring to 4 and up, or strictly just over 4GBs? This system I have Ubuntu on only has 4, it's older. Thanks

---

### Post by oldtimer7777 on 2011-12-03
> **bluexrider said:**
> Ive really not seen a reason to run the 64 without having the +4Gb of ram. But its whatever you choose I suppose.

Oh it is much snappier on my dual core Intel system using 64-bit.  Nothing I could seriously measure with my watch, but on the other hand apps loader faster sometimes, boot up seems alittle more speedy.   I don't like the fact that I can't install some deb packages without forcing them to work in 64-bit though.  It really depends what you need your computer to do for you on a regular basis.   And you are correct, you can install the 32-bit and upgrade your OS to the PAE kernel to use the additional extra memory on your system over the 2Gb limit on 32-bit.

---

### Post by TekMaster on 2011-12-03
Went ahead with the upgrade and I have to say, I can tell a BIG difference already. Much more responsive and like oldtimer said much quicker boot times. Thank you both for your response and I hope this thread can help others with their decision.

cheers

---

### Post by bluexrider on 2011-12-03
> **TekMaster said:**
> Thanks for the great feedback oldtimer, much appreciated. 

@bluexrider - When you say +4GBs of RAM: are you referring to 4 and up, or strictly just over 4GBs? This system I have Ubuntu on only has 4, it's older. Thanks
the rule of thumb:

if your processor is 64bit but less than 4Gb ram it really does no good to install the 64bit OS/software, because the architecture does not utilize the RAM to its maximum abilities. 

**In your case IF you have 4Gb of RAM or are able to install more RAM then run the 64bit OS.  **

---

### Post by oldtimer7777 on 2011-12-03
> **TekMaster said:**
> Went ahead with the upgrade and I have to say, I can tell a BIG difference already. Much more responsive and like oldtimer said much quicker boot times. Thank you both for your response and I hope this thread can help others with their decision.

cheers

You are welcome..  Don't forget to mark this thread as solved above when you are done here..  Cheers.

---

### Post by oldos2er on 2011-12-04
> **bluexrider said:**
> the rule of thumb:

if your processor is 64bit but less than 4Gb ram it really does no good to install the 64bit OS/software, because the architecture does not utilize the RAM to its maximum abilities. 

**In your case IF you have 4Gb of RAM or are able to install more RAM then run the 64bit OS.  **

64-bit Ubuntu runs perfectly on 2GB RAM; CPU-intensive tasks are noticeably faster, and yes, RAM is used to its "maximum abilities" (not sure what that means). Please don't spread FUD.

---

