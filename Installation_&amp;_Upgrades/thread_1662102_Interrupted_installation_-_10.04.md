---
title: "Interrupted installation - 10.04"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by 9182736 on 2011-01-07
Newbie here. I was installing 10.04 as a dual boot with Win7, the install was interrupted and now I can't do anything with it. Booting, I get as far as '[    0.541227] kernal_thread_helper' and it stops there with or without a disc. 

How do I complete the install or strip out something so that I can start again?

Can anyone help?

Thanks.

---

### Post by zvacet on 2011-01-07
Read [this]("https://help.ubuntu.com/community/BurningIsoHowto"),just to be sure you did everything as it should be done.After that try burn iso on lower possible speed.Try to install again.If you still get errors,please post them here.

---

### Post by kansasnoob on 2011-01-07
> **9182736 said:**
> Newbie here. I was installing 10.04 as a dual boot with Win7, the install was interrupted and now I can't do anything with it. Booting, I get as far as '[    0.541227] kernal_thread_helper' and it stops there with or without a disc. 

How do I complete the install or strip out something so that I can start again?

Can anyone help?

Thanks.

What can you boot?

Nothing?

Windows only?

Please be more descriptive, we're not mind readers.

Also please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by 9182736 on 2011-01-08
> **zvacet said:**
> Read [this]("https://help.ubuntu.com/community/BurningIsoHowto"),just to be sure you did everything as it should be done.After that try burn iso on lower possible speed.Try to install again.If you still get errors,please post them here.

Thank you for your reply. This isn't the first install I've done, I've been dual booting 10.04 on an iMac and running it on a Win7 laptop through Virtual Box as part of an OU course I've just completed - all without any problems. I want to dual boot the laptop. The install was physically interrupted - I have a four year old. Booting up the laptop I get the option for Windows or Ubuntu. Choosing Ubuntu I get 'Completing the Ubuntu Installation' then a series of scripts, from:

[    0.548589]  [<c01fe087>] ? __kmalloc +0x77/0x190  

to 

[0549368]  [<c0104087>] kernal_thread_helper+0x7/0x10

then it stops. Always the same scripts and it never moves. It doesn't make any difference if I boot from a disc or not. I can't get this to complete so I'm wondering if the way forward is to remove what is already there and begin again.

Win7 is unaffected.

I'm unable to post scripts because nothing has started up.

Thank you.

---

### Post by kansasnoob on 2011-01-09
> **9182736 said:**
> Thank you for your reply. This isn't the first install I've done, I've been dual booting 10.04 on an iMac and running it on a Win7 laptop through Virtual Box as part of an OU course I've just completed - all without any problems. I want to dual boot the laptop. The install was physically interrupted - I have a four year old. Booting up the laptop I get the option for Windows or Ubuntu. Choosing Ubuntu I get 'Completing the Ubuntu Installation' then a series of scripts, from:

[    0.548589]  [<c01fe087>] ? __kmalloc +0x77/0x190  

to 

[0549368]  [<c0104087>] kernal_thread_helper+0x7/0x10

then it stops. Always the same scripts and it never moves. It doesn't make any difference if I boot from a disc or not. I can't get this to complete so I'm wondering if the way forward is to remove what is already there and begin again.

Win7 is unaffected.

I'm unable to post scripts because nothing has started up.

Thank you.

I don't know but thought I'd give this a bump :confused:

---

### Post by 9182736 on 2011-01-11
> **kansasnoob said:**
> I don't know but thought I'd give this a bump :confused:
 
What does 'give this a bump mean'?
 
Regards

---

### Post by 9182736 on 2011-01-27
The answer is update the BIOS for the Toshiba Satellite I'm using. Download the BIOS for Independent OS and Bingo!. The problem was something to do with a wrong GRUB being selected. It all works fine now, I'm dual booting with Win7 and Ubuntu 10.04 and haven't come across any problems.

---

