---
title: "Harddisc drivers"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Girgoo on 2007-04-21
Hi 

I have downloaded and run ubuntu 7.04. It starts realy slow and say something like this:

[     157.9827647 ] sda ... xferrmode ... massx=40 
[     193.9645645  ] sda ... xferrmode ... massx=40 

and so on, i dont rember all. But when it is finish with the error messages it all run without problem.

But i cant see my sata harddrives =( i got Abit AB9 PRO and you could find it here:

[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AB9+Pro&fMTYPE=LGA775](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AB9+Pro&fMTYPE=LGA775)

it has these controllercards:

6 SATA 3Gbps Ports - Intel ICH8R
(RAID 0,1,1+0,5,JBOD)
2 SATA 3Gbps Ports - JMicron JM363
(RAID 0,1,JBOD)
2 SATA 3Gbps Ports - Silicon Image 3132

I belive i need to install some drivers for use them.

---

### Post by hardyn on 2007-04-21
there is some trouble with the .20.15 kernel and some SATA drive/controller combinations... i suggest you submit a bug report at the launchpad.

---

### Post by Girgoo on 2007-04-21
Are you sure that really is a bugg? i mean when i try Mandriva 2007.1 it is the same problem.

Now i am running sabayon (gentoo) and everything works perfect there, i can see the sata disk without problem.

If it is a bugg, what could i do about it?

---

### Post by hardyn on 2007-04-21
apparently the bug is linux kernel trunk bug, if i understand correctly...
and the problem is not limited to ubuntu.  some distros have chosen to handle it differently...

---

### Post by Girgoo on 2007-04-21
So if it is in the kernel, why works it fine in sabayon then?

how is it with Ubuntu ultimate? does it exist with 7.04?

---

### Post by hardyn on 2007-04-21
i could only speculate... but...

either sabyon has actully got things working, or they chosed to use the older SATA drivers, which as i have been reading is how many are doing it.

ubuntu ultimate is not an official release, its hard to say what is going on there;  and you started the post showing with issue with 7.04...

perhaps i am mis-understanding what you are saying... i am certainly not an athority, i have just been ineteresting is the progression of this bug.

---

### Post by Girgoo on 2007-04-22
I have tried ubuntu 6.10 but i only get to the start menu on the live cd and everything gets black.

---

